# NexaCore Learning — Dashboard & Database Views

## Overview

The NexaCore Learning workspace includes a centralized **Learning Operations Hub** designed to provide quick access to the major operational areas of the workspace.

The dashboard brings together navigation, high-level operational metrics, quick actions, and access to the underlying databases.

Multiple database views were also configured to present the same operational data in formats appropriate for different use cases.

---

## Learning Operations Hub

The main NexaCore Learning page functions as the entry point to the workspace.

The dashboard includes:

* Workspace introduction
* Operations Overview
* Navigation to core databases
* At a Glance metrics
* Quick Actions
* Access to operational databases

The dashboard was intentionally kept simple so that users can quickly understand the structure of the workspace without unnecessary visual clutter.

---

## Operations Overview

The Operations Overview provides navigation to the four primary areas of the workspace:

* 📚 Course Management
* 👩🏽‍🎓 Learner Management
* 👨🏽‍🏫 Instructor Management
* ✅ Tasks & Operations

Navigation links provide direct access to the corresponding operational databases.

This reduces the need to manually search through the workspace to locate frequently used information.

---

## At a Glance

An **At a Glance** section was added to provide a quick summary of the sample operational environment.

The completed implementation displays:

* 4 Courses
* 5 Learners
* 4 Instructors
* 7 Operational Tasks
* 2 Courses In Progress

These values provide a simple executive-level snapshot of the workspace used in the portfolio implementation.

For a larger production implementation, similar dashboard indicators could be expanded or supported by additional database views and calculated properties.

---

## Quick Actions

A **Quick Actions** section provides clearly identified starting points for common activities:

* Add New Course
* Add New Learner
* Add New Instructor
* Add New Task

The section helps organize frequently performed actions and makes the intended workflow of the dashboard immediately understandable.

---

# Database View Strategy

One of the key design principles used in the workspace is that different operational perspectives do not require separate datasets.

Notion database views allow the same records to be presented differently according to the user's objective.

The implementation demonstrates four primary view types:

1. Table
2. Board
3. Gallery
4. Calendar

---

## Table View

Table views are used for structured data management across the workspace.

They provide visibility into database properties and are particularly useful for:

* Creating records
* Updating properties
* Reviewing detailed information
* Managing relations
* Reviewing Rollup results

Course Management uses a Table view to display course details together with relational and calculated information.

This includes:

* Assigned Instructor
* Enrolled Learners
* Total Learners
* Average Learner Progress

The Table view therefore provides one of the clearest representations of the relational architecture implemented within the workspace.

---

## Learner Status Board

Learner Management includes a Board view that groups learner records according to Status.

The workflow stages are:

* Not started
* In progress
* Done

This provides a visual representation of learner participation.

Instead of reading individual status values from a table, users can quickly see how learners are distributed across the different stages.

The Board uses the same records maintained in Learner Management.

---

## Instructor Profiles Gallery

The Instructor Directory includes a Gallery view named **Instructor Profiles**.

Each Gallery card provides selected operational information about an instructor, including:

* Specialization
* Assigned Course
* Availability
* Teaching Status

The Gallery provides a more visual method of reviewing instructor resources while remaining connected to the underlying Instructor Directory database.

Properties that are less useful for the visual overview, such as email addresses, can remain stored in the database without being displayed on the Gallery cards.

---

## Operations Calendar

The Operations Task Tracker includes a Calendar view based on the **Due Date** property.

Tasks automatically appear according to their scheduled deadlines.

This provides a visual timeline for activities such as:

* Course preparation
* Learner communications
* Progress reviews
* Instructor coordination
* Content updates
* Administrative reporting

The Calendar does not require a separate set of task records.

Changes made to the underlying task database are reflected in its Calendar representation.

---

## Operations Status Board

The Operations Task Tracker also includes a Board view grouped according to task Status.

Tasks are displayed across:

* Not started
* In progress
* Done

Priority information remains visible on task cards, allowing users to review both workflow stage and importance.

This provides a simple operational workflow for monitoring work from creation through completion.

---

# One Database, Multiple Perspectives

The use of multiple views demonstrates an important workspace design principle:

**Data should not be duplicated simply because users need to see it differently.**

For example, an operational task can exist once in the Operations Task Tracker and simultaneously appear:

* As a row in the Table
* On its deadline in the Calendar
* Under its current stage on the Board

The underlying task remains a single record.

This approach improves consistency and reduces unnecessary data maintenance.

---

## Dashboard Design Approach

The final dashboard was designed around three priorities:

### Simplicity

Users should be able to understand the workspace without extensive instructions.

### Navigation

Frequently used operational areas should be accessible from the main page.

### Visibility

Important information should be available without requiring users to open every database individually.

The resulting Learning Operations Hub provides a clean entry point while the underlying databases handle the more detailed operational information.

---

## Implementation Result

The completed dashboard and database views provide multiple ways to interact with the NexaCore Learning workspace while maintaining a consistent underlying data structure.

The dashboard provides high-level visibility and navigation.

Table views support detailed record management.

Board views provide workflow visibility.

The Gallery view supports instructor resource management.

The Calendar provides deadline-based operational planning.

Together with the Relations and Rollups implemented across the workspace, these components create a structured Notion learning operations system that demonstrates practical workspace design, database configuration, and information management.
