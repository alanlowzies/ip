# User Guide for Sora Chatbot

## Features 

### Create a New Task

Create a new task that is a deadline, an event, or a to-do, and add it to Sora's 
list for her to keep track of your tasks.

### Display Your Tasks

Get Sora to display all the tasks that you have created and given to her to keep track on.

### Mark Your Tasks as Completed

Tell Sora that you have completed a task and she will update it accordingly in her list of tasks.

### Delete an Existing Task

Remove a task that you no longer wish Sora to keep track of.

### Search for an Existing Task

Enter a search query and Sora will show you the tasks that matches your search keywords.

### Automatic Saving of Task Data to Local Storage

Every time you create, update, or delete a task, Sora automatically saves these changes into a file
that is stored locally on your system's storage. This way, your tasks will remain after you bid
Sora farewell for the day and will be available the next time you start her up.

---

## Quick Start Guide

1. Download the JAR file for Sora from the repository's [releases page](https://github.com/alanlowzies/ip/releases/latest).
2. (Optional but recommended) Create a new folder and transfer `Sora.jar` into it.
3. From your terminal, set the new folder as your working directory.
4. Start up Sora with `java -jar Sora.jar`.

---

## Usage

### `deadline` - Create a new deadline task

Creates a new task that is a deadline.

**Syntax**
```
deadline <description> /by <due date>
```

| Parameters | Description |
| --- | --- |
| `<description>` | Information about this deadline task. |
| `<due date>` | When this task is due. Format: `DD/MM/YYYY HHmm`, where `HHmm` is the time in 24-hour format. |

**Example**
```
> deadline Project submission /by 12/04/2022 2359
```
**Expected Outcome**
```
------------------------------------------------------------
Alright, I've added your new task to my list:

	[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)

------------------------------------------------------------
```
A new deadline task called 'Project submission' with a deadline of 12 April 2022 at 11:59pm is created
and added to Sora's list.

### `event` - Create a new event task

Creates a new task that is an event.

**Syntax**
```
event <description> /at <event date>
```

| Parameters | Description |
| --- | --- |
| `<description>` | Information about this event task. |
| `<event date>` | When this event is set to occur. Format: `DD/MM/YYYY HHmm`, where `HHmm` is the time in 24-hour format. |

**Example**
```
> event Table tennis match /at 22/02/2022 1400
```
**Expected Outcome**
```
------------------------------------------------------------
Okay, I've added your new task to my list:

	[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)

------------------------------------------------------------
```
A new event task called 'Table tennis match' that is expected to take place on 22 February 2022 at 2pm
is created and added to Sora's list.

### `todo` - Create a new todo task
Creates a new task that is a todo.

**Syntax**
```
todo <description>
```

| Parameter | Description |
| --- | --- |
| `<description>` | Information about this todo task. |

> **Note**: Unlike deadline and event tasks, todo tasks do not have dates.

**Example**
```
> todo Buy groceries
```

**Expected Outcome**
```
------------------------------------------------------------
Gotcha, I've added your new task to my list:

	[T][ ] Buy groceries

------------------------------------------------------------
```
A new todo task called 'Buy groceries' is created and added to Sora's list.

### `list` - Show your tasks

Lists down all the tasks that you have given to Sora.

**Syntax**
```
list
```
**Example Outcome**
```
------------------------------------------------------------
Gotcha, here's a list of 3 tasks that you have given to me:

	1.[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)
	3.[T][ ] Buy groceries

------------------------------------------------------------
```
Each task entry
has the following information:

| Example | Attribute Name | Description |
| --- | --- | --- |
| `1.` | Task number | The task number of the task entry. |
| `[D]` | Task type | The type of task this entry is. `D` for deadline tasks, `E` for event tasks, and `T` for todo tasks. |
| `[ ]` | Task status | Indicates whether a task is complete or not. If it is marked as done, it will be shown as `[X]`.
| `Project submission` | Task description | The description of the task entry. |
| `(due on: Tue, 12 Apr 2022, 11:59 PM)` | Task date & time | (_Applicable to deadline and event tasks only_) The date and time associated with the task entry.

### `mark` - Mark a task as done

Marks a task as completed.

**Syntax**
```
mark <task number>
```

| Parameter | Description |
| --- | --- |
| `<task number>` | The number of the task that you want to mark as done. |

**Example**

Assume that Sora has the following list (generated by the `list` command):
```
------------------------------------------------------------
Gotcha, here's a list of 3 tasks that you have given to me:

	1.[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)
	3.[T][ ] Buy groceries

------------------------------------------------------------
```
Suppose that you want to mark the project submission, which is labelled as task number 1
on the list as complete, you can type
```
> mark 1
```

**Expected Outcome**
```
------------------------------------------------------------
Gotcha, I've marked this task as done:

	[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)

------------------------------------------------------------
```
Now, if you run the `list` command again, you will see that your 'Project submission' deadline 
task has been marked as complete, as denoted by the `[X]` checkbox.

```
------------------------------------------------------------
Okay, here's a list of 3 tasks that you have given to me:

	1.[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)
	3.[T][ ] Buy groceries

------------------------------------------------------------
```

### `Unmark` - Mark a task as not done

Marks a task as incomplete.

**Syntax**
```
unmark <task number>
```

| Parameter | Description |
| --- | --- |
| `<task number>` | The number of the task that you want to mark as not done. |

**Example**

Assume that you have the following list of tasks (generated by the `list` command):
```
------------------------------------------------------------
Okay, here's a list of 3 tasks that you have given to me:

	1.[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)
	3.[T][ ] Buy groceries

------------------------------------------------------------
```
Suppose you want to mark your 'Project submission' task as not done, you can type
```
> unmark 1
```
**Expected Outcome**
```
------------------------------------------------------------
Got it, I've marked this task as not done:

	[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)

------------------------------------------------------------
```
Now, if you run the `list` command again, you will see that the 'Project submission' task is no longer marked as done,
as indicated by the empty `[ ]` checkbox.

### `delete` - Delete a task

Deletes a task that is on the list.

**Syntax**
```
delete <task number>
```

| Parameter | Description |
| --- | --- |
| `<task number>` | The number of the task that you want to delete. |

**Example**

Assuming that the following is your current list of tasks (generated by the `list` command):
```
------------------------------------------------------------
Gotcha, here's a list of 3 tasks that you have given to me:

	1.[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)
	3.[T][ ] Buy groceries

------------------------------------------------------------
```
Suppose that your table tennis match has been cancelled due to unforseen circumstances
and you wish to remove it from the list, you can type:
```
> delete 2
```

**Expected Outcome**
```
------------------------------------------------------------
Alright, I've deleted this task:

	[E][ ] Table tennis match (scheduled for: Tue, 22 Feb 2022, 2:00 PM)

------------------------------------------------------------
```
Now, if you run the `list` command again, you will notice that the above task is no longer in your
list and you only have 2 tasks left.
```
------------------------------------------------------------
Alright, here's a list of 2 tasks that you have given to me:

	1.[D][ ] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[T][ ] Buy groceries

------------------------------------------------------------
```

### `find` - Search for task(s)

Searches the list for tasks that matches your specified search query. Your query can be a word or a phrase.
The search mechanism is a simple word/phrase match on the texts as shown in the `list` command.

**Syntax**
```
find <search query>
```

| Parameter | Description |
| --- | --- |
| `<search query>` | The word/phrase that you wish to search for in your list of tasks. |
---

**Examples**

Suppose you have the following list of tasks (generated by the `list` command):
```
------------------------------------------------------------
Alright, here's a list of 8 tasks that you have given to me:

	1.[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	2.[T][ ] Buy groceries
	3.[T][ ] Homework
	4.[E][ ] Fireworks (scheduled for: Sun, 1 Jan 2023, 12:00 AM)
	5.[D][X] SEP application (due on: Mon, 28 Feb 2022, 11:59 PM)
	6.[T][ ] Walk the dog
	7.[D][ ] Art submission (due on: Fri, 11 Nov 2022, 10:00 PM)
	8.[E][ ] Raining cats and dogs (scheduled for: Fri, 1 Apr 2022, 8:00 AM)

------------------------------------------------------------
```
If you want to find tasks with the word 'submission', you can type
```
> find submission
```
and Sora will respond to you with
```
------------------------------------------------------------
Alright, I have found 2 tasks that matches your search
phrase:

	1.[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	7.[D][ ] Art submission (due on: Fri, 11 Nov 2022, 10:00 PM)

------------------------------------------------------------
```

If you want to find all event tasks, you can type
```
> find [E]
```
and Sora will reply to you with
```
------------------------------------------------------------
Okay, I have found 2 tasks that matches your search
phrase:

	4.[E][ ] Fireworks (scheduled for: Sun, 1 Jan 2023, 12:00 AM)
	8.[E][ ] Raining cats and dogs (scheduled for: Fri, 1 Apr 2022, 8:00 AM)

------------------------------------------------------------
```
If you want to find all completed tasks, you can type
```
> find [X]
```
and Sora will reply with
```
------------------------------------------------------------
Gotcha, I have found 2 tasks that matches your search
phrase:

	1.[D][X] Project submission (due on: Tue, 12 Apr 2022, 11:59 PM)
	5.[D][X] SEP application (due on: Mon, 28 Feb 2022, 11:59 PM)

------------------------------------------------------------
```

>**Note**: The search mechanism is case-sensitive. Thus, `find SEP` will give you
>```
>------------------------------------------------------------
>Gotcha, I have found 1 task that matches your search
>phrase:
>
>	5.[D][X] SEP application (due on: Mon, 28 Feb 2022, 11:59 PM)
>
>------------------------------------------------------------
>```
>but `find SeP` will not return any results:
>```
>------------------------------------------------------------
>Oops, there are no tasks that match your search phrase.
>Perhaps you could refine your search parameters?
>------------------------------------------------------------
>```

### `bye` - Bid Sora farewell

Exits the application.

**Syntax**
```
bye
```
**Expected Outcome**
```
------------------------------------------------------------
Good night, have a good rest...
See you again soon~
------------------------------------------------------------
<end of program>
```
Note that depending on the time or day, Sora will bid you farewell differently.
(She also greets you differently based on the time of the day!)

---
## File Storage Information

When you start Sora for the first time on a computer, the following are created:
- A directory named `CS2113T_iP_Sora_Resources`
- A text file named `data.txt` residing within the aforementioned directory.

On subsequent boot ups, Sora will automatically read the file to load the tasks created in previous
sessions onto the current one.

### Caution

The directory and text file will be created in your terminal's **current working directory**.
Thus, it is highly recommended that you **set your working directory to the directory where
`Sora.jar` is located in** before starting up Sora.

### Recommendation
1. Create an empty directory and place `Sora.jar` inside it.
2. Set your terminal's current working directory to the aforementioned directory.
3. Run `Sora.jar` from the directory.

This way, `Sora.jar` and your file data will be stored within the same directory.