---
layout: page
title: User Guide
---

**PlanIT** is a todo list, calendar application for NUS computer science students with a busy schedule to quickly 
and efficiently add classes for modules and easily view their tasks.
It is optimised for users who prefer typing.


### Table of Contents
* [Quick start](#start)
* [Features](#features)
* [FAQ](#faq)
* [Command summary](#summary)

--------------------------------------------------------------------------------------------------------------------

## <a name="start"></a> Quick start

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `planit.jar` from [here](https://github.com/AY2021S2-CS2103T-T10-2/tp/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your planner.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. 
   Note how the app contains some sample data.<br>
   ![Ui](images/Ui.png)

1. Type the command in the command box and press Enter to execute it. e.g. typing **`help`** and 
   pressing Enter will open the help window.<br>
   Some example commands you can try:

   * **`list`** : Lists all contacts.

   * **`add`**`eat dinner` : Adds a task titled `eat dinner` to the todo list.

   * **`delete`**`3` : Deletes the 3rd task shown in the current list.

   * **`exit`** : Exits the app.

1. Refer to the [Features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Features

<div markdown="block" class="alert alert-info">

**:information_source: Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add NAME`, `NAME` is a parameter which can be used as `add eat dinner`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last 
  occurrence of the parameter will be taken.<br>
  e.g. if you specify `p/12341234 p/56785678`, only `p/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit` and `clear`) 
  will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

### View Commands : `help`

Displays a list of possible commands along with each of their formats respectively.

Format: `help`


### Adding a task: `add`

Adds a task to the todo list.

Format: `add TITLE`

Examples:
* `add eat dinner`

### Listing all tasks : `list`

Shows a list of all tasks in the planner.

Format: `list`

### Adding deadline to a task : `deadline`

Adds a deadline to an existing task in the list.

Format: `Add INDEX [d/DATE]…​`

* Edits the task at the specified `INDEX`. The index refers to the index number shown in the displayed list. The index **must be a positive integer** 1, 2, 3, …​
* Date field must be provided.
* Existing values will be updated to the input values.
* When editing dateline, the existing dates of the person will be removed i.e adding of dateline is not cumulative.
* You can remove all the person’s dateline by typing `d/` without
  specifying any deadline after it.

Examples:
*  `Add 1 d/2021-05-13` Adds a deadline to the 1st task on the list which is to be `13 May 2021.
*  `Add 2 d/` Clears the existing deadline of 2nd task on the list.

### Editing a person : `edit`

Edits an existing person in the address book.

Format: `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [t/TAG]…​`

* Edits the person at the specified `INDEX`. The index refers to the index number shown in the displayed person list. 
  The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
* You can remove all the person’s tags by typing `t/` without
    specifying any tags after it.

Examples:
*  `edit 1 p/91234567 e/johndoe@example.com` Edits the phone number and email address of the 1st person to be 
   `91234567` and `johndoe@example.com` respectively.
*  `edit 2 n/Betsy Crower t/` Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

### Searching a task: `find`

Find matching tasks based on the keyword(s) provided by the user.

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `project` will match `Project`
* The order of the keywords does not matter. e.g. `CS2103 Project` will match `Project CS2103`
* Only full words will be matched e.g. `proj` will not match `projects`

Examples:
* `find CS2103` returns `cs2103` and `CS2103 team project`

### Deleting a task : `delete`

Deletes an existing task from the task list.

Format: `delete INDEX`

* Deletes the task at the specified `INDEX`.
* The index refers to the index number shown in the displayed task list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd task in the task list.
* `find Work` followed by `delete 1` deletes the 1st task in the result of the `find` command.

### Clearing all entries : `clear`

Clears all entries from the address book.

Format: `clear`

### Exiting the program : `exit`

Exits the program.

Format: `exit`

### Saving the data

AddressBook data are saved in the hard disk automatically after any command that changes the data. 
There is no need to save manually.

### Editing the data file

AddressBook data are saved as a JSON file `[JAR file location]/data/addressbook.json`. 
Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, AddressBook will discard all data and 
start with an empty data file at the next run.
</div>

--------------------------------------------------------------------------------------------------------------------

## <a name="faq"></a> FAQ

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file 
that contains the data of your previous AddressBook home folder.

--------------------------------------------------------------------------------------------------------------------

## <a name="summary"></a> Command summary

Action | Format, Examples
--------|------------------
**Add** | `add TITLE` <br> e.g., `add eat dinner`
**Clear** | `clear`
**Delete** | `delete INDEX`<br> e.g., `delete 3`
**Edit** | `edit INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [a/ADDRESS] [t/TAG]…​`<br>e.g.,`edit 2 n/James Lee e/jameslee@example.com`
**Find** | `find KEYWORD [MORE_KEYWORDS]`<br> e.g., `find CS2103 team project`
**List** | `list`
**Help** | `help`
