# Reading Notes 13 -- Related Resources and Integration Testing

## One-to-Many Relationship

The one-to-many relationship between entities in Spring Data REST is defined with annotations.

- `@OneToMany` is used to define the entity that the current class will point to many. This annotation goes on the entity that is one and points to the many. This annotation can be added to a List of the "many" type.
- `@ManyToOne` is used in the opposite fashion to from the entity that will be many to the entity that will be one. This annotation is added to an instance of the "one" type.

Example from Baeldung:

```java
@Entity
public class Book {

    @Id
    @GeneratedValue
    private long id;
    
    @Column(nullable=false)
    private String title;
    
    @ManyToOne
    @JoinColumn(name="library_id")
    private Library library;
    // standard constructor, getter, setter
}

public class Library {
    //...
    @OneToMany(mappedBy = "library")
    private List<Book> books;
    //...
}

```

From [Baeldung](https://www.baeldung.com/spring-data-rest-relationships)

## Integration Testing

From [Baeldung](https://www.baeldung.com/integration-testing-in-spring)

Integration testing allows for verifying the view and response body, http response status, and headers. 


1. Add dependencies for junit-jupiter-engine, junit-jupiter-api and Spring test.
2. Setup a test class with annotations for jUnit 5 extension interface.
  - `@ExtendWith(SpringExtension.class)`
  - `@ContextConfiguration(classes = {ApplicationConfig.class})`
  - `@WebAppConfiguration` loads the web app context that defaults to "src/main/webapp" which can be overridden by passing a value.
3. Setup the WebAppContext Object using the `@Autowired` annotation.
4. Initialize a MockMvc object using `@BeforeEach` and it will initialize inside each test.
5. Verify the configuration with a test that checks the servlet context.
  - Use the `getServeltContext()` method on the WebApplicationContext object.
  - Also use `getBean("greetController")` to verify it exists.


### Tests

Simple MockMvc test example from Baeldung:

```java
@Test
public void givenHomePageURI_whenMockMVC_thenReturnsIndexJSPViewName() {
    this.mockMvc.perform(get("/homePage")).andDo(print())
      .andExpect(view().name("index"));
}
```
The *perform()* method returns "ResultActions", *andDo(print())* is chained to that in order to print it out and *andExpect()* targets the expected result for the test.

Response body test example from Baeldung:

```java
@Test
public void givenGreetURI_whenMockMVC_thenVerifyResponse() {
    MvcResult mvcResult = this.mockMvc.perform(get("/greet"))
      .andDo(print()).andExpect(status().isOk())
      .andExpect(jsonPath("$.message").value("Hello World!!!"))
      .andReturn();
    
    Assert.assertEquals("application/json;charset=UTF-8", 
      mvcResult.getResponse().getContentType());
}
```

- The *isOk()* refers to a 200 status. 
- The *jsonPath().value()* extracts the response content and compares to value.
- The *andReturn()* allows saving the MvcResult and running assertions.

GET request example from Baeldung:

```java
@Test
public void givenGreetURIWithPathVariable_whenMockMVC_thenResponseOK() {
    this.mockMvc
      .perform(get("/greetWithPathVariable/{name}", "John"))
      .andDo(print()).andExpect(status().isOk())
      
      .andExpect(content().contentType("application/json;charset=UTF-8"))
      .andExpect(jsonPath("$.message").value("Hello World John!!!"));
}
```

- GET request test can also use query parameters with *.param(<name>, <value>)*

POST test example from Baeldung:

```java
@Test
public void givenGreetURIWithPost_whenMockMVC_thenVerifyResponse() {
    this.mockMvc.perform(post("/greetWithPost")).andDo(print())
      .andExpect(status().isOk()).andExpect(content()
      .contentType("application/json;charset=UTF-8"))
      .andExpect(jsonPath("$.message").value("Hello World!!!"));
}

@Test
public void givenGreetURI_whenMockMVC_thenVerifyResponse() throws Exception {
    MvcResult mvcResult = this.mockMvc.perform(MockMvcRequestBuilders.get("/greet"))
      .andDo(print())
      .andExpect(MockMvcResultMatchers.status().isOk())
      .andExpect(MockMvcResultMatchers.jsonPath("$.message").value("Hello World!!!"))
      .andReturn();
 
   assertEquals("application/json;charset=UTF-8", mvcResult.getResponse().getContentType());
}
```

