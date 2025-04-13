# Developing-a-mini-IMDB-Database
Designed and implemented a relational database using Oracle SQL to analyze IMDb movie data. Built from scratch with an optimized schema, structured tables, and efficient queries to extract insights on ratings, genres, and crew members while ensuring data integrity and performance optimization.

# IMDb Database Design

## Overview

This repository contains the design for an IMDb-inspired database. The database focuses on storing information about movies, TV shows, and the people involved in their creation. This repository also contains project report PDF file which documents the Relational Schema diagram and Entity Relationship (ER) diagram along with some query results.

### Entities

The main entities in the database design are Movie and TV Show. [cite: 2, 3] Other entities include Actor, Director, and Writer. [cite: 3, 4, 5, 6] Movie Review and TV Show Review are included as well. [cite: 38, 39, 40, 41, 42]

* **Movie:** Stores information about movies, including name (title) and release date. [cite: 10, 11, 12, 13, 14, 15]
    * Key attribute: name (title) [cite: 12, 13, 14, 15]
* **Show:** Stores information about TV shows, including name (title), release date, and seasons. [cite: 16, 17, 18, 19, 20, 21, 22]
    * Key attribute: name (title) [cite: 21, 22]
    * Shows have seasons, which have episodes as a multivalued attribute. [cite: 22]
* **Actor:** Stores information about actors, including name, date of birth (DOB), age, and awards. [cite: 23, 24, 25, 26, 27, 28, 29, 30, 31]
    * Key attribute: name (composite attribute of first and last name) [cite: 23, 24, 25, 26, 27, 28]
    * Age is a derived attribute, calculated from DOB. [cite: 29, 30]
* **Director:** Stores information about directors, including name, DOB, age, and awards. [cite: 31, 32, 33, 34]
    * Key attribute: name (composite attribute of first and last name) [cite: 34]
    * Age is a derived attribute, calculated from DOB. [cite: 34]
* **Writer:** Stores information about writers, including name, DOB, age, and awards. [cite: 35, 36, 37]
    * Key attribute: name (composite attribute of first and last name) [cite: 37]
    * Age is a derived attribute, calculated from DOB. [cite: 37]
* **Movie Review:** Stores reviews for movies, including user\_name, rating, rating title, review date, and review. [cite: 38, 39]
    * This is a weak entity, dependent on the existence of a Movie. [cite: 38, 39]
    * Primary Key: user\_name [cite: 39]
* **Show Review:** Stores reviews for TV shows, including user\_name, rating, rating title, review date, and review. [cite: 40, 41, 42]
    * This is a weak entity, dependent on the existence of a Show. [cite: 40, 41, 42]
    * Primary Key: user\_name [cite: 42]

### Relationships

* **Actor / Acts In:** An actor must act in a movie or show to be considered an actor. [cite: 43, 44, 45, 46]
* **Director / Directed:** A director must have directed a movie or a show to be considered a director. [cite: 47, 48]
* **Writer / Wrote\_Script:** A writer must write a script to be considered a writer. [cite: 48, 49]
* **Movie / Rating:** A movie can have a rating. [cite: 49, 50]
* **Show / Rating:** A show can have a rating. [cite: 49, 50]

### Relationship Constraints

* **Director vs. Movies/Shows:** Total relationship (double line) between Director and Movies/Shows. [cite: 50, 51, 52]
    * A movie or show can have only one director, but a director can direct multiple movies and shows (1:M cardinality). [cite: 52]
* **Actor vs. Movies/Shows:** Total relationship (double line) between Actor and Movies/Shows. [cite: 53, 54, 55, 56]
    * A movie or show can have multiple actors, and actors can act in multiple movies and shows (N:M cardinality). [cite: 56]
* **Writer vs. Movies/Shows:** Total relationship (double line) between Writer and Movies/Shows. [cite: 57, 58, 59]
    * A movie or show can have only one writer, but a writer can write for multiple movies and shows (1:M cardinality). [cite: 59]
* **Movies/Shows vs. Movie Review/Show\_Reviews:** Partial relationship (single line) between Movies/Shows and Movie Review/Show\_Reviews. [cite: 60, 61, 62]
    * A movie or show may or may not have a review, but a review must be tied to a movie or show. [cite: 61, 62]
    * A movie or show can have multiple reviews, but reviews must be tied to a particular movie or show (1:M cardinality). [cite: 62]

### Examples

* Christopher Nolan, a director and writer, is associated with multiple movies, such as Oppenheimer (one-to-many relationship). [cite: 63, 64, 65, 66]
* Cillian Murphy, an actor in Oppenheimer, has appeared in various movies and shows (many-to-many relationship). [cite: 65, 66]
* Each entity includes attributes like Name, Awards, and Date of Birth, along with other relevant details. [cite: 66]
