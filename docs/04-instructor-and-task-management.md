# NexaCore Learning — Instructor & Task Management

## Overview

The NexaCore Learning workspace includes dedicated systems for managing instructor information and operational tasks.

The **Instructor Directory** provides visibility into instructor specialization, course assignments, availability, and teaching status.

The **Operations Task Tracker** provides a structured system for managing responsibilities, priorities, deadlines, and task completion across learning operations.

Together, these databases support both instructional coordination and day-to-day operational management.

---

## Instructor Directory

The Instructor Directory was created as the central location for managing instructor records.

### Properties

The database includes:

* **Instructor Name** — Primary instructor record
* **Email** — Instructor contact information
* **Specialization** — Primary subject or professional area
* **Assigned Course** — Relation to Course Management
* **Availability** — Current instructor availability
* **Teaching Status** — Current teaching activity status

---

## Instructor Specializations

Specialization information allows instructors to be categorized according to their primary area of expertise.

Sample specializations used within the implementation include:

* Project Management
* Data Analytics
* Customer Experience
* Leadership

This provides an additional layer of information when reviewing instructor resources and course assignments.

---

## Availability Tracking

The Availability property was configured to provide quick visibility into instructor capacity.

Availability options include:

* Available
* Limited
* Unavailable

This allows the workspace to distinguish instructors who are available for assignments from those with limited or unavailable capacity.

---

## Instructor-to-Course Relationship

The Assigned Course property is configured as a Notion **Relation** connected to the Course Management database.

The implementation includes the following sample assignments:

* Ada Okafor → Project Management Essentials
* Daniel Mensah → Excel for Business Analytics
* Grace Bello → Customer Experience Fundamentals
* Michael Eze → Leadership & Team Management

The reciprocal relationship allows Course Management to display the instructor connected to each course.

This prevents course assignment information from being maintained independently in multiple databases.

---

## Instructor Profiles Gallery

A Gallery view named **Instructor Profiles** was created from the Instructor Directory.

The Gallery provides a visual alternative to the standard table while continuing to use the same underlying instructor records.

Instructor cards display operational information including:

* Specialization
* Assigned Course
* Availability
* Teaching Status

Email information remains stored within the database but does not need to be displayed on the Gallery cards.

This keeps the visual profile focused on information relevant to instructor coordination.

---

# Operations Task Tracker

The Operations Task Tracker was created to centralize activities required to support the learning program.

Instead of maintaining separate task lists for course administration, learner support, instructors, and content, operational activities are maintained within one structured database.

## Task Properties

The database includes:

* **Task Name** — Primary task record
* **Area** — Operational category
* **Owner** — Person or team responsible
* **Priority** — Importance level
* **Due Date** — Required completion date
* **Status** — Current stage of work

---

## Operational Areas

Tasks can be categorized across:

* Course Management
* Learner Support
* Instructor Management
* Content
* Administration

This allows operational activities to remain within one database while still being classified according to business function.

---

## Task Ownership

The Owner property identifies responsibility for each operational activity.

Sample ownership within the implementation includes individual instructors and the Operations Team.

This provides visibility into who is responsible for completing each activity.

---

## Priority Management

Tasks are assigned one of three priority levels:

* High
* Medium
* Low

Priority information provides a simple method for distinguishing urgent activities from routine operational work.

It can also support future filtering and priority-specific views.

---

## Status Tracking

Operational tasks move through three primary statuses:

* Not started
* In progress
* Done

A Board view was created to group tasks by these statuses.

This provides a visual workflow where users can quickly identify:

* Work waiting to begin
* Work currently underway
* Completed activities

The Board uses the same records contained in the Operations Task Tracker and does not require duplicate task entries.

---

## Operations Calendar

A Calendar view was also created using the **Due Date** property.

Tasks automatically appear on the calendar according to their assigned deadlines.

The calendar provides a time-based view of activities such as:

* Course material reviews
* Cohort communications
* Course resource preparation
* Learner progress reviews
* Instructor availability checks
* Course outline updates
* Monthly operations reporting

Because the Calendar and Table views use the same underlying database, changes to a task are reflected across both views.

---

## Multiple Views, One Dataset

The Operations Task Tracker demonstrates an important Notion database principle:

**A different view does not require a different database.**

The same operational records can be displayed as:

* A structured Table
* A workflow Board
* A deadline-based Calendar

Each view serves a different operational purpose while maintaining a single source of task information.

---

## Operational Benefits

The Instructor and Task Management configuration provides:

* Centralized instructor records
* Instructor specialization tracking
* Availability visibility
* Relational course assignments
* Visual instructor profiles
* Centralized operational task management
* Task ownership
* Priority tracking
* Deadline management
* Status-based workflow visibility
* Calendar-based scheduling
* Multiple views without duplicating records

---

## Implementation Result

The completed configuration connects instructional resources with the broader learning operation.

Instructor records provide visibility into who is delivering each course and their current availability, while the Operations Task Tracker provides a centralized system for coordinating the activities required to keep the program running.

Together with Course and Learner Management, these components form a structured Notion workspace for managing learning operations from a single environment.
