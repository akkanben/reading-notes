# Reading Notes 27 -- Tasks, Back Stack and SharedPreferences

## The LifeCycle of a Task

When an app is launched and has no previous state the initial activity as added to a stack. This "back stack" grows as activities lead to other activities in the app. If the home button is pressed the entire task (stack of activities) is suspended.

While in the task the back button will pop an activity off the stack destroying it and revealing the new top activity of the back stack.

If a app was previously suspended and is started again from the menu or recents, the suspended the entire task's stack will be brought to the foreground and the activity at the top resumes.

## Managing Tasks

Typically the default behavior of the back stack is the ideal. Sometimes though it might be preferred if the back button popped multiple or the entire stack down to the root element or some other custom behavior. If an app requires a different behavior there are flags that can be used in the manifest to allow these adjustments.

### Launch Modes

Launch modes allow activities to have custom associations to the current task. These can be defined in the manifest or with intent flags. In the manifest there are 4 different launch modes that the `launchMode` attribute can be assigned.

- *standard* is the default launch mode for an activity.
- *singleTop* prevents an activity from stacking on top of an identical activity but allows the stack to grow if the launched activity is not the same.
- *singleTask* only instantiates a single instance. If one already exists the call goes through `onNewIntent()` method. The back button will still return the user to the previous activity.
- *singleInstance* launches the activity as it's own task.

These behaviors can be overridden with intent flags:

- FLAG_ACTIVITY_NEW_TASK starts the activity as a new task (similar to "singleTask").
- FLAG_ACTIVITY_SINGLE_TOP if the activity is the same as the current activity a call to `onNewIntent()` is made instead.
- FLAG_ACTIVITY_CLEAR_TOP often used with the new task flag, clear top destroys all other activities on the stack if the new activity is already running in the current task. 

### Clear the Back Stack

If a task is left for long enough the system clears all the activities except the root activity. This default behavior can be modified.

- `alwaysRetainTaskState` This keeps the activities in tack even after long periods of time have passed.
- `clearTaskOnLaunch` This clears all the activities down to the root activity if the task is left. Requires FLAG_ACTIVITY_RESET_TASK_IF_NEEDED flag.
- `finishOntaskLaunch` Behaves like clearTaskOnLaunch but applies to a single activity. Requires FLAG_ACTIVITY_RESET_TASK_IF_NEEDED flag.

## SharedPreferences

A SharedPreferences object controls a file that holds a small number of key-value pairs. 

- `getSharedPreferences()` is used to get multiple shared preference files.
- `getPreferences()` is used to retrieve a single preference file.
- `edit()` can be used on a SharedPreferences.Editor object in order to write to a shared preference file.
- `apply()` is used to commit changes that have been edited.
- `getInt()` and `getString()` can be used to read from shared preferences by providing the key.
