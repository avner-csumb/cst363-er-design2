---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 35min
---

# ER Modeling — Constraints

CST 363



---


## Lecture Objectives


After this lecture, you should be able to:
Add mapping cardinalities, participation cardinalities, and keys to an ER model


Remove redundant attributes from an ER model

---

## Motivation


- So far, our ER models let us talk about:
  - some entities
  - their relationships
  - attributes of entities and relationships
- Can an ER model answer these questions?
  - can one session be taught by multiple instructors?
  - must every student have an advisor?


---


## Mapping cardinalities


- Can a student have more than one advisor?
- Can an instructor advise more than one student?


<img src="/images/si1.png" class="w-50" />


<img src="/images/si2.png" class="w-50" />


---

## Mapping cardinalities: one-to-one

Example: office-of relationship set

<img src="/images/si3.png" class="w-50" />



- An office can be assigned to at most one instructor
- An instructor can have at most one office

---

## Mapping cardinalities: one-to-many


Example: adviser relationship set


<img src="/images/si4.png" class="w-50" />


- A student has at most one adviser
- An instructor can have zero or more students


---

## Mapping cardinalities: many-to-many

Example: takes  relationship set


<img src="/images/si5.png" class="w-50" />


- Each section is taken by zero or more students
- Each student takes zero or more sections


---

## What are mapping cardinalities for the music library model?


---

## Participation constraints

- Only two cases:
  - total
  - partial
- Remember, this is a constraint 
  - prescriptive, not descriptive

<img src="/images/si6.png" class="w-50" />


---

## Participation constraints of music lib.


What are participation constraints in our music library example?


---

## Keys of entities

- We need to be able to distinguish entities
- So — no two entities in an entity set can have the same attribute values
- Definitions of key, superkey, candidate key all apply
  - A superkey is any set of attributes that uniquely identifies a tuple (row) in a relation (table).
  - A candidate key is a minimal superkey—a superkey without any unnecessary attributes.
  - A primary key is one chosen candidate key that serves as the main unique identifier for the table.

---

## Complication: keys of relationship sets


We also need to be able to uniquely identify 
relationships
primary keys of the entity sets:
instructor: inst_ID
student: student_ID
So a superkey for the ‘advises’ is:
inst_ID, student_ID


<img src="/images/table1.png" class="w-50" />


In other words: we can uniquely identify a relationship if we can uniquely identify the entities in the relationship
