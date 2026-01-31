---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: CST 363
info: |
  ## ER Modeling — Constraints
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 35min
---

# ER Modeling — Constraints

CST 363



---


## Lecture Objectives

<div class="p-5">

After this lecture, you should be able to:
Add mapping cardinalities, participation cardinalities, and keys to an ER model


Remove redundant attributes from an ER model


</div>

---

## Motivation

<div class="p-5">


- So far, our ER models let us talk about:
  - some entities
  - their relationships
  - attributes of entities and relationships
- Can an ER model answer these questions?
  - can one session be taught by multiple instructors?
  - must every student have an advisor?


</div>


---


## Mapping cardinalities

<div class="p-5">


- Can a student have more than one advisor?
- Can an instructor advise more than one student?


<img src="/images/si1.png" class="w-40" />


<img src="/images/si2.png" class="w-40" />

</div>


---

## Mapping cardinalities: one-to-one

<div class="p-5">


Example: office-of relationship set

<img src="/images/si3.png" class="w-40" />



- An office can be assigned to at most one instructor
- An instructor can have at most one office



</div>


---

## Mapping cardinalities: one-to-many

<div class="p-5">



Example: adviser relationship set


<img src="/images/si4.png" class="w-40" />


- A student has at most one adviser
- An instructor can have zero or more students

</div>


---

## Mapping cardinalities: many-to-many

<div class="p-5">


Example: takes  relationship set


<img src="/images/si5.png" class="w-40" />


- Each section is taken by zero or more students
- Each student takes zero or more sections


</div>


---

## What are mapping cardinalities for the music library model?


---

## Participation constraints

<div class="p-5">


- Only two cases:
  - total
  - partial
- Remember, this is a constraint 
  - prescriptive, not descriptive

<br>

<img src="/images/si6.png" class="w-60" />



</div>


---

## Participation constraints of music lib.

<div class="p-5">



What are participation constraints in our music library example?

</div>


---

## Keys of entities

<div class="p-5">


- We need to be able to distinguish entities
- So — no two entities in an entity set can have the same attribute values
- Definitions of key, superkey, candidate key all apply
  - A superkey is any set of attributes that uniquely identifies a tuple (row) in a relation (table).
  - A candidate key is a minimal superkey—a superkey without any unnecessary attributes.
  - A primary key is one chosen candidate key that serves as the main unique identifier for the table.



</div>


---

## Complication: keys of relationship sets

<div class="p-5">



- We also need to be able to uniquely identify relationships
- primary keys of the entity sets:
  - instructor: `inst_ID`
  - student: `student_ID`
- So a superkey for the ‘advises’ is:
  - `inst_ID, student_ID`


<img src="/images/table1.png" class="w-50" />


In other words: we can uniquely identify a relationship if we can uniquely identify the entities in the relationship


</div>



<!-- 

On this slide we’re saying that the primary keys of the entities gives a superkey of the relationship; on the next slide we say how you get a primary key for the relationship.


In Entity-Relationship (ER) modeling, relationships can be uniquely identified using keys derived from the participating entities.



-->


---

## Primary keys for relationship sets

<div class="p-5">



Suppose a student have at most one advisor, but an advisor can advise many students


<img src="/images/table2.png" class="w-50" />



We know {advisor ID, student ID} is a superkey.


Question: Is there a smaller superkey?


</div>

<!-- 



When you tighten the cardinality constraint, you can often reduce the size of the key because fewer attributes are needed to uniquely identify each relationship instance

1:N constraint
Each student has at most one advisor.

inst_ID → student_ID is one-to-many (one instructor → many students)


student_ID → inst_ID is one-to-one or many-to-one (each student appears at most once)


ach student can appear in the Advises relationship at most once, so their ID alone uniquely identifies a relationship instance.
Therefore, the key of the relationship can be reduced to:
Key = {student_ID}



This is showing that, in some cases, the relationship can be identified without identifying
both of the primary keys.

Remember, the point of a key is to uniquely identify things.  Or – no two relationships can
be indistinguishable.  Here, every advisor relationship can be identified through its unique
student ID.

If each student is assigned exactly one advisor, student_id alone uniquely identifies the relationship.



-->

---

## Primary keys for relationship sets

<div class="p-5">



| **Mapping cardinality**                                                                                       | **Primary key**                                  |
| ---------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| *many-to-many*<br>(a student can have more than one advisor;<br>an instructor can advise more than one student) | `advises(inst_ID, student_ID)`                  |
| *many-to-one*<br>(a student can have at most one advisor;<br>instructors can advise many students)              | `advises(student_ID)`                           |
| *one-to-one*<br>(a student can have at most one advisor,<br>similarly for instructors)                          | `advises(student_ID)`<br> or<br>`advises(inst_ID)` |



</div>


---


## Keys of music library

<div class="p-5">



What should we use as primary keys in our music library example?


</div>


---

## Removing redundant attributes

<div class="p-5">


Example:

```
instructor(ID, name, dept_name, salary)
department(dept_name, building, budget)
```

- We might decide to add relationship set  inst_dept between instructor and department.
- Then the dept_name attribute of instructor becomes redundant.
- It should be removed from instructor – it is the key of department.

</div>

<!-- 


Basically, it is better to treat the inst/dept relationship explicitly, rather than as an attribute of instructor.

-->


---

## Music Library exercise

<div class="p-5">


Do we need to remove redundant attributes in the music library example?

</div>

<!-- 


Song and Album:
Rather than storing album details (like Album Title or ReleaseDate) in each Song record, these should reside only in the Album entity. Songs should reference the Album via a foreign key.

Song and Artist:
Instead of duplicating artist details in each Song, use a join table (e.g., SongArtist) that links the unique identifiers of songs and artists.


-->

---


## A method for developing an ER model


<div class="p-5">


- Identify entity sets
- Identify relationship sets
- Identify mapping cardinalities
- Identify participation constraints
- Identify attributes of entity and relationship 
- sets (and their domains)
- Identify primary keys of entity sets
- Identify primary keys of relationship sets


This is not a rule  
(it’s more of a guideline…)
Try it and see if it’s helpful


</div>

---

## Summary

<div class="p-5">


- Mapping cardinalities
  - how many relationships (of one relationship type) can an entity participate in?
  - example: how many advisors can a student have?
- Participation constraints
  - must every entity participate in a relationship in some relationship set?
- Keys
  - similar to keys of relations
  - a concept of keys also used for relationships

</div>