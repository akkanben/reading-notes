# Reading Notes 31 -- Espresso

From the [Android Espresso Documentation](https://developer.android.com/training/testing/espresso)

Espresso is used to write Android UI tests. Espresso is designed to be reliable because it waits until actions/assertions are synchronized before continuing, reducing the likelihood of concurrent tests.

**Packages:**

- *espresso core* includes basic View matchers, actions, and assertions.
- *espresso web* for WebView support.
- *espresso idling-resource* for working with background jobs.
- *espresso contrib* includes DatePicker, RecyclerView, Drawer actions, accessibility checks and CountingIdlingResource.
- *espresso intents* for validating stub intents.
- *espresso remote* for Espresso's multi-process methods.

## Basics

- *Espresso* The parent class for interacting with views.
  - `onView()` used for locating a view to make assertions on.
  - `onData()` used to load larger objects into the view hierarchy for assertions.
  - Includes other general methods.
- *ViewMatchers* The objects sent to an `onView()` call to locate a view.
- *ViewActions* The objects that can be passed to `ViewInteraction.perform()`.
- *ViewAssertions* The objects that can be passed to `ViewInteraction.check()` to perform assertions.

[Espresso Cheat Sheet](https://developer.android.com/images/training/testing/espresso-cheatsheet.png)

## Recipes

Android documentation has a series of examples, here are a few:

### Match a view to another view

Pairing two views is a way to isolate certain views that are not unique alone.

```java
onView(allOf(withText("7"), hasSibling(withText("item: 0"))))
    .perform(click());
```

### Assert that a view is not displayed

Using not() with isDisplayed() can assert a negative case for the state of th UI.

```java
import static androidx.test.espresso.Espresso.onView;
import static androidx.test.espresso.assertion.ViewAssertions.matches;
import static androidx.test.espresso.matcher.ViewMatchers.isDisplayed;
import static androidx.test.espresso.matcher.ViewMatchers.withId;
import static org.hamcrest.Matchers.not;

onView(withId(R.id.bottom_left))
    .check(matches(not(isDisplayed())));
```

### Assert that a view is not present

Use doesNotExist() to confirm a view is gone, often after an action has moved the current view to another activity.

```java
import static androidx.test.espresso.Espresso.onView;
import static androidx.test.espresso.assertion.ViewAssertions.doesNotExist;
import static androidx.test.espresso.matcher.ViewMatchers.withId;

onView(withId(R.id.bottom_left))
    .check(doesNotExist());
```

## Espresso Test Recorder

Espresso Test Recorder allows creating assertions while running the app live. It allows for easily stepping through the app and asserting that some UI text matches the expected text.

Verifying UI elements uses three main assertions: *text is*, *exists*, and *does not exist*. The tester can create a snapshot and click on a part of the UI directly to create the interactive assertion.

The tests can run locally or in the cloud using Firebase Text Lab.
