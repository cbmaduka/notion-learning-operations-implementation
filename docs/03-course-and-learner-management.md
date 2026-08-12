# NexaCore Learning — Course & Learner Management

## Overview

Course and learner management form the core of the NexaCore Learning workspace.

The implementation uses two connected Notion databases to manage course information and learner participation while avoiding unnecessary duplication of data.

The **Course Management** database provides course-level visibility, while the **Learner Management** database maintains individual learner records.

A database relation connects both areas of the workspace.

---

## Course Management Database

The Course Management database was designed to provide a central record for each training course.

### Properties

The database includes:

* **Course Name** — Primary course identifier
* **Category** — Course classification
* **Status** — Current course status
* **Start Date** — Scheduled course start
* **End Date** — Scheduled course completion
* **Assigned Instructor** — Relation to the Instructor Directory
* **Enrolled Learners** — Relation to Learner Management
* **Total Learners** — Rollup of connected learner records
* **Average Learner Progress** — Rollup calculating progress across connected learners

---

## Sample Course Structure

The workspace was configured with sample course records representing different professional training areas:

* Project Management Essentials
* Excel for Business Analytics
* Customer Experience Fundamentals
* Leadership & Team Management

These records provide sample data for demonstrating the functionality of the implementation.

Each course contains its own operational information while remaining connected to the appropriate instructor and learner records.

---

## Course Status Tracking

The Status property provides visibility into the current stage of each course.

Courses can be identified as:

* Not started
* In progress
* Done

This makes it possible to distinguish upcoming programs from active and completed courses without maintaining separate databases.

---

## Learner Management Database

The Learner Management database provides an individual record for each learner participating in the training program.

### Properties

The database includes:

* **Learner Name** — Primary learner record
* **Email** — Learner contact information
* **Course** — Relation to Course Management
* **Enrollment Date** — Date the learner joined the program
* **Progress** — Percentage of course progress completed
* **Status** — Current participation status
* **Cohort** — Learner intake group

This structure makes it possible to monitor both enrollment information and ongoing learner participation.

---

## Course Enrollment Relationship

The Course property was configured as a Notion **Relation** rather than a simple text or select field.

Each learner is connected directly to a corresponding record in the Course Management database.

For example:

**Learner → Course**

Amara Nwosu → Project Management Essentials

Samuel Adeyemi → Excel for Business Analytics

Fatima Bello → Customer Experience Fundamentals

David Okoro → Leadership & Team Management

Grace Mensah → Customer Experience Fundamentals

The reciprocal **Enrolled Learners** property in Course Management displays the learner records connected to each course.

This means the course and learner databases remain synchronized through their relationship.

---

## Automated Enrollment Count

The **Total Learners** property uses a Notion Rollup.

Instead of manually entering the number of learners participating in each course, the rollup counts the records connected through the Enrolled Learners relation.

For example, Customer Experience Fundamentals has two connected learner records and therefore automatically displays a Total Learners value of 2.

This reduces the need to maintain the same information manually in multiple locations.

---

## Learner Progress Tracking

Each learner record includes a Progress property.

Progress values provide a simple indication of how far a learner has advanced through the assigned course.

Sample values within the implementation include:

* 0%
* 65%
* 80%
* 100%

These individual values are also used by Course Management to calculate course-level learner progress.

---

## Average Learner Progress

The **Average Learner Progress** property in Course Management is configured as a Rollup.

The rollup:

1. Uses the Enrolled Learners relation.
2. Retrieves the Progress property from related learner records.
3. Calculates the average.

For example, two learners enrolled in Customer Experience Fundamentals have progress values of 80% and 100%.

The resulting course-level average is automatically calculated as **90%**.

This demonstrates how learner-level data can be summarized at the course level without manual calculations.

---

## Learner Status Board

In addition to the standard database table, a Board view was created for Learner Management.

The board groups learner records according to Status:

**Not started | In progress | Done**

This provides a visual representation of learner participation and allows the same learner records to be viewed as a workflow.

No separate learner records are required for the Board view.

The Table and Board views display the same underlying database information in different formats.

---

## Cohort Tracking

The Cohort property provides an additional method for organizing learners according to intake period.

Example cohorts used in the implementation include:

* August 2026
* September 2026

This structure could support future filtering, reporting, and cohort-specific views as the learning operation grows.

---

## Operational Benefits

The Course and Learner Management configuration provides:

* Centralized course records
* Structured learner enrollment data
* Learner progress tracking
* Course status visibility
* Cohort organization
* Direct learner-to-course relationships
* Automatic enrollment counts
* Automatic course-level progress calculations
* Multiple database views without record duplication

---

## Implementation Result

The completed configuration creates a connected course and learner management system rather than two independent lists.

Learner information is maintained at the individual record level, while relations and rollups make relevant information available within Course Management.

This allows the workspace to provide both detailed learner-level tracking and higher-level course visibility from the same underlying data.
