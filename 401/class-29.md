# Reading Notes 29 -- The Room

The Room in Android is an abstraction layer over SQLite and is the recommended way to store local persistent data. The Room checks SQL queries at compile time, has convenient annotations, and has streamlined database migration paths. There are three primary components to the Room:

1. The database class that holds the database and is the main access point to the database.
2. The data entities that act as the tables in the database.
3. The data access objects which are used to store methods for accessing and modifying the database.

To setup an implementation first use annotations to identify entities in your models. Next create a DAO and build out some query methods for getting, inserting and deleting data. Finally create a database class that extends RoomDatabase, and use the builder method to make an instance of the database.

## Defining Entities

The `@Entity` annotation is added to a class that should have a corresponding table in the database. The `@PrimaryKey` annotation is used to uniquely identify each row in the database (typically an id). The primary key can be a composite of two properties if necessary.

- Any properties that should be ignored can be marked with the `@Ignore` annotation.
- `@Fts4` can be added to an entity to allow for fast full-text search support.

## Relationships

The Room supports two ways of defining a query to the database. One way is to setup an intermediate class that maps to the values in the query. The other way is the just grab everything from the query and set it to return a map.

- The `@Embedded` annotation can be used to decompose an object into subfields within a table. This in a way is defining a join between tables.
- The `@Relation()` annotation is used to define the primary key connections between entities.

### One to One

A one-to-one relationship is used when an instance of a parent entity corresponds to exactly one child entity (and vice-versa). 

- Create a data class where each instance holds an instance of the parent entity and the child entity.
- One of the entities must have a property that can reference the primary key of the other entity. 
- Use the `@Relation()` annotation to define the "parentColumn" to the parent's id and the "entityColumn" to the property that references the parent's id. 
- Finally add a method in the DAO with the `@Transaction` and `@Query` annotations that returns a query that returns all the instances that pair the parent and child entities.

### One to Many

The one-to-many relationship defines a relationship where the parent entity corresponds to zero or more child entities but the child has only the single parent. 

- Create a data class where each instance holds a single instance of the parent and a list of the child.
- The child entity must have a property that holds a reference to the primary key of the parent.
- Use the `@Relation()` annotation to define the "parentColumn" to the parent's id and the "entityColumn" to the property that references the parent's id. 
- Finally add a method in the DAO with the `@Transaction` and `@Query` annotations that returns a query that returns all the instances that pair the parent and child entities.

### Many to Many

The many-to-many relationship defines a relationship where the both the parent and child entities can correspond to zero or more entities of the other.

- For many-to-many relationships a reference the primary key of the parent or child is not needed. Instead create a third cross reference class that has a property to represent the primary key from each entity in the many-to-many relationship.
- Create a data class that has a single parent instance and a list of the child. Multiple data classes can be made to represent different queries.
- Use the `@Relation()` annotation to define the "parentColumn" to the parent's id and the "entityColumn" to the child's id, additionally add "associateBy" and use the `@Junction` annotation with the name of the cross reference class.
- Finally add a method in the DAO with the `@Transaction` and `@Query` annotations that returns a query that returns all the instances that pair the parent and child entities.

## Using the Room DAO

The Room Dao holds methods that let you run queries on the database. Dao's are defined as an interface or an abstract class (typically an interface) with the `@DAO` annotation.

### Convenience Methods

Built in query methods using annotations for `@Insert`, `@Update`, and `@Delete`. These annotations accept `@Entity` instances as parameters.

Examples

```java
@Dao
public interface UserDao {
    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);

    @Query("SELECT * FROM user")
    List<User> getAll();
}
```

### Query Methods

The `@Query` annotation allows for SQL queries to be used as DAO methods. Classes can be constructed to allow DAO methods to return objects. Use the `@ColumnInfo()` annotation to define the column name that should map to the given property. Parameters can be passed into DAO methods as well by prefixing a colon in the SQL statement. Whole collections can be passed in by enclosing the colon prefixed variable name with parenthesis. 

When pre-made classes are not used a multimap can be used to dump everything into a map.

Examples

```java
public class NameTuple {
    @ColumnInfo(name = "first_name")
    public String firstName;

    @ColumnInfo(name = "last_name")
    @NonNull
    public String lastName;
}

@Query("SELECT first_name, last_name FROM user")
public List<NameTuple> loadFullName();

@Query("SELECT * FROM user WHERE age BETWEEN :minAge AND :maxAge")
public User[] loadAllUsersBetweenAges(int minAge, int maxAge);

@Query("SELECT * FROM user WHERE region IN (:regions)")
public List<User> loadUsersFromRegions(List<String> regions);

@Query(
    "SELECT * FROM user" +
    "JOIN book ON user.id = book.user_id" +
    "GROUP BY user.name WHERE COUNT(book.id) >= 3"
)
public Map<User, List<Book>> loadUserAndBookNames();
```
