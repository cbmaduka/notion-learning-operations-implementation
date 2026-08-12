# NexaCore Learning — Workspace Architecture

## Overview

The NexaCore Learning workspace was designed as a centralized learning operations system in Notion.

The architecture separates operational information into dedicated databases while connecting related records through Notion relations and rollups.

This approach allows each record to be maintained in its appropriate database while still making related information available across the workspace.

## Workspace Structure

The implementation consists of four core databases:

1. **Course Management**
2. **Learner Management**
3. **Instructor Directory**
4. **Operations Task Tracker**

These databases support the main Learning Operations Hub.

---

## 1. Course Management

The Course Management database acts as the central academic operations database.

### Key Properties

* Course Name
* Category
* Status
* Start Date
* End Date
* Assigned Instructor
* Enrolled Learners
* Total Learners
* Average Learner Progress

### Purpose

The database provides a consolidated view of each course and connects course records to instructor and learner information.

Rather than manually maintaining separate learner counts and progress summaries, relational properties and rollups allow course-level information to update based on connected records.

---

## 2. Learner Management

The Learner Management database stores individual learner records.

### Key Properties

* Learner Name
* Email
* Course
* Enrollment Date
* Progress
* Status
* Cohort

### Purpose

This database provides structured tracking of learner enrollment and course participation.

Each learner is connected to an actual record in the Course Management database through a Relation property.

This replaces the need to repeatedly type course information into learner records.

---

## 3. Instructor Directory

The Instructor Directory provides a centralized record of instructors involved in course delivery.

### Key Properties

* Instructor Name
* Email
* Specialization
* Assigned Course
* Availability
* Teaching Status

### Purpose

The directory provides visibility into instructor expertise, availability, current assignments, and teaching status.

Instructor assignments are connected to Course Management using a database relation.

This allows course records and instructor records to reference one another.

---

## 4. Operations Task Tracker

The Operations Task Tracker manages administrative and operational activities supporting the learning program.

### Key Properties

* Task Name
* Area
* Owner
* Priority
* Due Date
* Status

### Operational Areas

Tasks can be categorized across areas including:

* Course Management
* Learner Support
* Instructor Management
* Content
* Administration

This provides a single location for tracking responsibilities and deadlines across the learning operation.

---

## Database Relationship Architecture

The workspace uses relations to connect the main operational records.

The core relationship structure is:

**Learner Management ↔ Course Management ↔ Instructor Directory**

Learners are connected to the courses in which they are enrolled.

Instructors are connected to the courses they are assigned to deliver.

Course Management therefore becomes a central point from which both learner participation and instructor assignments can be viewed.

### Learner-to-Course Relationship

The Learner Management database contains a **Course** relation connected to Course Management.

The corresponding Course Management property identifies the **Enrolled Learners** associated with each course.

### Instructor-to-Course Relationship

The Instructor Directory contains an **Assigned Course** relation connected to Course Management.

The corresponding Course Management property identifies the **Assigned Instructor** for each course.

---

## Rollup Architecture

Relations are also used to support automated course-level calculations.

### Total Learners

The **Total Learners** rollup counts learner records connected through the Enrolled Learners relation.

This provides an automatically calculated enrollment count.

### Average Learner Progress

The **Average Learner Progress** rollup retrieves the Progress values of related learner records and calculates their average.

This provides course-level visibility into learner progress without manually calculating the value.

---

## Database Views

Different views were created from the same underlying databases to support different operational needs.

### Table View

Used for structured record management and detailed data entry.

### Board View

Used to visualize records according to workflow status.

Learner records can be viewed across:

* Not started
* In progress
* Done

Operational tasks can also be viewed according to their current status.

### Gallery View

Used within the Instructor Directory to provide an Instructor Profiles view displaying key information such as specialization, course assignment, availability, and teaching status.

### Calendar View

Used within the Operations Task Tracker to display operational deadlines according to Due Date.

This allows the team to visualize scheduled activities without maintaining a separate calendar dataset.

---

## Design Principle

The architecture follows a simple principle:

**Store information once, connect it where needed, and display it differently according to operational purpose.**

A learner record does not need to be recreated inside Course Management.

An instructor does not need to be manually entered into multiple databases.

A task does not need to be duplicated to appear on a calendar.

Notion relations and database views allow the same underlying records to support multiple workflows.

---

## Result

The completed architecture creates a connected Notion environment where:

* Courses serve as central learning records.
* Learners are connected to their enrolled courses.
* Instructors are connected to assigned courses.
* Enrollment counts are automatically calculated.
* Learner progress is summarized at course level.
* Tasks can be managed through both structured and visual views.
* The dashboard provides centralized access to the operational system.

This structure demonstrates how Notion can be configured beyond basic note-taking into a relational workspace for managing business operations.
