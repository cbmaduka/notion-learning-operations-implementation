# NexaCore Learning — Relations & Rollups

## Overview

The NexaCore Learning workspace uses Notion Relations and Rollups to connect operational databases and automatically summarize information across related records.

Rather than maintaining Course Management, Learner Management, and the Instructor Directory as independent lists, relationships were created between the databases.

This allows information to be stored once and referenced where it is needed.

---

## Relational Database Structure

The core relational structure is:

**Learner Management ↔ Course Management ↔ Instructor Directory**

Course Management functions as the central connection point.

Learners are connected to the courses in which they are enrolled, while instructors are connected to the courses they are assigned to deliver.

This creates a structured relationship between the three main areas of the learning operation.

---

# Learner-to-Course Relation

## Purpose

The learner-to-course relation connects individual learner records with their corresponding Course Management records.

Instead of storing a course name as independent text within Learner Management, the **Course** property was configured as a Relation.

## Configuration

**Source Database:** Learner Management

**Relation Property:** Course

**Connected Database:** Course Management

**Reciprocal Property:** Enrolled Learners

This creates a two-way connection.

A learner record identifies the course in which the learner is enrolled, while the corresponding course record displays the learners connected to it.

---

## Example Relationship

The implementation includes relationships such as:

* Amara Nwosu → Project Management Essentials
* Samuel Adeyemi → Excel for Business Analytics
* Fatima Bello → Customer Experience Fundamentals
* David Okoro → Leadership & Team Management
* Grace Mensah → Customer Experience Fundamentals

Because multiple learner records can relate to the same course, Customer Experience Fundamentals contains two connected learner records.

---

# Instructor-to-Course Relation

## Purpose

A second relation connects instructors with their assigned courses.

This allows instructor assignments to be managed as relationships between actual database records rather than duplicated text values.

## Configuration

**Source Database:** Instructor Directory

**Relation Property:** Assigned Course

**Connected Database:** Course Management

**Reciprocal Property:** Assigned Instructor

---

## Example Relationship

The implementation includes:

* Ada Okafor → Project Management Essentials
* Daniel Mensah → Excel for Business Analytics
* Grace Bello → Customer Experience Fundamentals
* Michael Eze → Leadership & Team Management

Course Management therefore provides direct visibility into the instructor associated with each course.

---

# Course Management as the Central Record

After configuring both relations, Course Management can display information from multiple operational areas.

A course record can contain:

* Course information
* Course schedule
* Course status
* Assigned instructor
* Enrolled learners
* Total number of learners
* Average learner progress

This makes Course Management a central operational record without requiring learner and instructor information to be recreated manually.

---

# Rollup: Total Learners

## Purpose

The **Total Learners** Rollup automatically calculates the number of learner records associated with each course.

## Configuration

**Property Type:** Rollup

**Relation:** Enrolled Learners

**Related Property:** Learner Name

**Calculation:** Count All

---

## Result

The resulting values in the implementation are:

| Course                           | Total Learners |
| -------------------------------- | -------------: |
| Project Management Essentials    |              1 |
| Excel for Business Analytics     |              1 |
| Customer Experience Fundamentals |              2 |
| Leadership & Team Management     |              1 |

These values are generated from the relationships between the databases rather than manually entered enrollment totals.

---

# Rollup: Average Learner Progress

## Purpose

The **Average Learner Progress** Rollup provides course-level visibility into learner progress.

Individual progress values are maintained within Learner Management.

The Course Management database retrieves those values through the Enrolled Learners relation and calculates their average.

## Configuration

**Property Type:** Rollup

**Relation:** Enrolled Learners

**Related Property:** Progress

**Calculation:** Average

---

## Example Calculation

Customer Experience Fundamentals has two connected learner records:

* Fatima Bello — 80%
* Grace Mensah — 100%

The Rollup automatically calculates:

**(80% + 100%) ÷ 2 = 90%**

Course Management therefore displays an Average Learner Progress value of **90%**.

No separate calculation needs to be maintained manually.

---

# Removing Duplicate Data

Before the relations were implemented, course assignments could be represented using simple Select or Text properties.

Once the relational structure was confirmed, duplicate properties were removed or hidden in favor of the connected database properties.

This ensures the workspace uses the relational records as the primary source of information.

For example:

**Before**

Instructor name stored as independent text inside Course Management.

**After**

Course Management displays the instructor through the **Assigned Instructor** relation.

The same principle applies to learner enrollment.

---

# Why Relations Matter

Without relations, the workspace would contain several separate databases that happen to use similar information.

With relations, the databases operate as parts of one connected system.

This provides several benefits:

* Reduced duplicate data
* Better consistency across databases
* Easier navigation between related records
* Centralized course-level visibility
* Automatic aggregation of related information
* More scalable workspace architecture

---

# Why Rollups Matter

Relations establish the connection between records.

Rollups make those connections operationally useful.

Instead of simply showing which learners belong to a course, the workspace can use related learner information to answer questions such as:

* How many learners are enrolled?
* What is their average progress?

As additional learner records are connected to a course or their progress values change, the Rollup calculations can update based on the underlying database records.

---

## Implementation Result

The Relations and Rollups configuration transforms NexaCore Learning from a collection of independent Notion databases into a connected learning operations workspace.

The implementation demonstrates how Notion can be used to establish relationships between operational records and automatically summarize information across those relationships.

The resulting structure supports a single-source-of-truth approach where information is maintained in its appropriate database and surfaced elsewhere through database connections rather than unnecessary duplication.
