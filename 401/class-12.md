# Reading Notes 12 -- Spring and RESTful Routing & Static Files

## Accessing Data with JPA

From [Spring.io Guides](https://spring.io/guides/gs/accessing-data-jpa/)

- Include the "Spring Data JPA" and "H2 Database" dependencies from the Spring Initializr
- Create a class to be an entity by using the `@Entity` annotation before the class.
  - `@Id` annotation let's JPA know the object will have an ID.
  - `@GeneratedValue` indicates that the value for the ID should be generated.
- A repository interface can be setup to extend CrudRepository<type, type> (these types of the entity and Id -- customer/long in example).
- Expand on the application class build with Spring init:

```java
package com.example.accessingdatajpa;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;

@SpringBootApplication
public class AccessingDataJpaApplication {

  private static final Logger log = LoggerFactory.getLogger(AccessingDataJpaApplication.class);

  public static void main(String[] args) {
    SpringApplication.run(AccessingDataJpaApplication.class);
  }

  @Bean
  public CommandLineRunner demo(CustomerRepository repository) {
    return (args) -> {
      // save a few customers
      repository.save(new Customer("Jack", "Bauer"));
      repository.save(new Customer("Chloe", "O'Brian"));
      repository.save(new Customer("Kim", "Bauer"));
      repository.save(new Customer("David", "Palmer"));
      repository.save(new Customer("Michelle", "Dessler"));

      // fetch all customers
      log.info("Customers found with findAll():");
      log.info("-------------------------------");
      for (Customer customer : repository.findAll()) {
        log.info(customer.toString());
      }
      log.info("");

      // fetch an individual customer by ID
      Customer customer = repository.findById(1L);
      log.info("Customer found with findById(1L):");
      log.info("--------------------------------");
      log.info(customer.toString());
      log.info("");

      // fetch customers by last name
      log.info("Customer found with findByLastName('Bauer'):");
      log.info("--------------------------------------------");
      repository.findByLastName("Bauer").forEach(bauer -> {
        log.info(bauer.toString());
      });
      // for (Customer bauer : repository.findByLastName("Bauer")) {
      //  log.info(bauer.toString());
      // }
      log.info("");
    };
  }

}
```

## JpaRepository

From [Baeldung](https://www.baeldung.com/spring-data-repositories) & [Spring.io Docs](https://docs.spring.io/spring-data/data-jpa/docs/current/api/org/springframework/data/jpa/repository/JpaRepository.html#deleteAllInBatch-java.lang.Iterable-)


JpaRepository implements PagingAndSortingRepository which implements CrudRepository so it has the functionality of both and more.

Code example from Baeldung
```java
public interface JpaRepository<T, ID extends Serializable> extends
  PagingAndSortingRepository<T, ID> {

    List<T> findAll();

    List<T> findAll(Sort sort);

    List<T> save(Iterable<? extends T> entities);

    void flush();

    T saveAndFlush(T entity);

    void deleteInBatch(Iterable<T> entities);
}
```

Useful methods:

- `findAll()` Returns all instances of the type.
- `findAll(Sort sort)` Returns all entities sorted by the give options
- `save()` saves a given entity
- `flush()` flushes all pending changes to the database
- `saveAndFlush()` Saves an entity and flushes changes instantly
- `deleteInBatch()` Deletes the given entities in a batch which means it will create a single query. This kind of operation leaves JPAs first level cache and the database out of sync. Consider flushing the EntityManager before calling this method.

