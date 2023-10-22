# 002. ER Diagram

Tags: Database

### Introduction

An entity-relationship (ER) diagram, also called an entity-relationship model basically shows the connection between entities.

here are two kinds of ER diagrams: **conceptual** and **physical**.

### Conceptual ER Diagrams

A conceptual ER diagram uses six standard symbols.

1. **Entities** are objects or concepts that represent important data. Also known as strong entities or parent entities, these entities will often have weak entities that depend on them.
2. **Attributes** are characteristics of an entity (i.e., many-to-many or one-to-one).
3. **Relationships** are associations between entities.
4. **Weak entities** depend on another entity.
5. **Multivalued attributes** are attributes that can have more than one value.
6. **Weak relationships** are the connections between a weak entity and its parent.

![ER Diagram Notations](https://github.com/debjotyms/blog-posts/blob/main/Database%20Systems/resources/002%20ER%20Diagram/1_er_diagram_notations.png?raw=true)

### Physical ER Diagrams

Physical diagram models are more granular, showing the processes necessary for adding information to a database. Rather than using symbols, they consist of a series of tables.

Each entity is represented as a table, with each **field** acting as an attribute of the entity containing it.

![Physical ER Diagram](https://github.com/debjotyms/blog-posts/blob/main/Database%20Systems/resources/002%20ER%20Diagram/2_physical_er_diagram.png?raw=true)

Entities are connected via a system of **notation** called **crow’s foot notation**. The styling of the endpoint of each line distinguishes the relationship.

![Crow's Foot Notation](https://github.com/debjotyms/blog-posts/blob/main/Database%20Systems/resources/002%20ER%20Diagram/3_crow's_foot_notation.png?raw=true)

The types of relationships of an ER diagram depend on the entity’s interactions with the other elements. Relationships can be one-to-one (1:1) or one-to-many (1:N). In some instances, the relationship will include many to many (N:N).