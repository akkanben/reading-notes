# Reading Notes 11 -- Spring

## Spring App Basics

From [Spring's guide](https://spring.io/guides/gs/serving-web-content/)

Spring's tutorial is a simple guide to getting a HTTP GET request set up using Java.

### Spring Initializr (not misspelled)

Use the spring initializr to generate a customized .zip file with all the dependencies you need.

### Web Controller

Create a web controller class using the `@Controller` annotation. In the example the "GreetingController" handles the GET requests for "/greeting" via a "View".

```java
// src/main/java/com/example/servingwebcontent/GreetingController.java
package com.example.servingwebcontent;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class GreetingController {

	@GetMapping("/greeting")
	public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
		model.addAttribute("name", name);
		return "greeting";
	}
}
```

- `@GetMapping` ensures that HTTP GET requests to "/greeting" are mapped the the `greeting()` method.
- `@RequestParam` binds the parameters passed via the url.
- Adding the name value to the model object makes it accessible to the view template.
- Thymeleaf is used as the view technology for server-side rendering
  - "greeting.html" is parsed and the `th:text` expression signals Thymeleaf to render the name variable in place of `${name}`.

### Spring Boot Devtools

The `spring-boot-devtools` module can be added to a project via dependencies in Gradle (or Mavin). The dev tools include a helpful live-reload feature that can speed up development.

### Run the Application

Spring Initializr creates a "ServingWebContentApplication.java" class.

```java
// src/main/java/com/example/servingwebcontent/ServingWebContentApplication.java
package com.example.servingwebcontent;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ServingWebContentApplication {

    public static void main(String[] args) {
        SpringApplication.run(ServingWebContentApplication.class, args);
    }
}
```

- `@SpringBootApplication` is a annotation that provides multiple annotations.
  - `@Configuration` tags this class as a "bean" definition source.
  - `@EnableAutoConfiguration` allows Spring to automatically start adding beans and other propery settings.
  - `@ComponentScan` tells Spring to find other items in "com/example" package.
- The `main()` function runs via Spring's `SpringApplication.run()`.

### Build and Test

You can build the application with Gradle with `./gradlew bootRun` or separately run `./gradlew build` followed by `java -jar build/libs/gs-serving-web-content-0.1.0.jar`.

The new running application can be tested at `http://localhost:8080/greeting` or the same followed by `?name=Spring` to bypass the default "Hello World" and replace with "Hello Spring".

If a static homepage is desired an `index.html` can be added to "/static" or "/public" classpath.

## Spring MVC and Thymeleaf

From [Thymeleaf's docs](https://www.thymeleaf.org/doc/articles/springmvcaccessdata.html)

### Spring Model Attributes

Bits of data that can be accessed during the execution of views are called "model attributes" in Spring but are referred to as "context variables" in Thymeleaf. These context variables can be added to a view in a few different ways:

- Using the `addAttribute()` method:
```java
    @RequestMapping(value = "message", method = RequestMethod.GET)
        public String messages(Model model) {
            model.addAttribute("messages", messageRepository.findAll());
            return "message/list";
        }
```

- By returning the whole `ModelAndView` with the attributes inside:

``java
    @RequestMapping(value = "message", method = RequestMethod.GET)
        public ModelAndView messages() {
            ModelAndView mav = new ModelAndView("message/list");
            mav.addObject("messages", messageRepository.findAll());
            return mav;
        }
```

- Or by annotating methods with `@ModelAttribute`

```java
    @ModelAttribute("messages")
        public List<Message> messages() {
            return messageRepository.findAll();
        }
```

The context variables can be accessed via Spring El (Spring Expression Language):

```html
    <tr th:each="message : ${messages}">
            <td th:text="${message.id}">1</td>
            <td><a href="#" th:text="${message.title}">Title ...</a></td>
            <td th:text="${message.text}">Text ...</td>
        </tr>
```

### Request & Session Parameters

Parameters added to the url like `https://example.com/query?q=Thymeleaf+Is+Great!` can be accessed with the `param.` prefix.

Examples:

- `<p th:text="${param.q}">Test</p>` single parameter, if it is missing an empty string will replace it.
- `<p th:text="${param.q[0] + ' ' + param.q[1]}" th:unless="${param.q == null}">Test</p>` a multivalued parameter
  - `<p th:text="${#request.getParameter('q')}" th:unless="${#request.getParameter('q') == null}">Test</p>` accessing a multivalued parameter. 

In a similar fashion to request parameters, session parameters can be accessed with the `session.` prefix after using `session`'s `setAtribute()` method.

### Others

**ServletContext** attributes are shared between sessions and requests. A `#servletContext.` prefix can be used.

**Spring Beans** can be accessed with the `@beanName` syntax.
