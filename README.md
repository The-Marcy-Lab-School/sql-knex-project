# SQL Project
- [SQL Project](#sql-project)
- [Welcome](#welcome)
- [Overview](#overview)
- ["This is boring! We can't see anything!"](#this-is-boring-we-cant-see-anything)
- [Tech Checklist](#tech-checklist)
  - [Entity Relationship Diagram (ERD)](#entity-relationship-diagram-erd)
  - [Migrations](#migrations)
  - [Models](#models)
  - [Seed](#seed)

# Welcome
Welcome to the SQL project! This is a culmination of all your SQL skills so far! There will feel like a lot of components to look at, but remember that each part feeds into the next. It's all connected! So the more clearly you set up one stage, the easier the next stages will be.

# Overview
You're going to be building a database that has a `many to many` relationship. This means that you'll have a primary parent table, a secondary parent table, and a join table. The primary parent table will have a `one to many` relationship with the join table, and the join table will have a `many to one` relationship with the secondary parent table. This is a common relationship in databases, and it's important to understand how to set it up.

To build this, you must use `knex`. Please, do not use any of `knex`'s query methods. We know they're great! But we want to see your raw SQL skills. You will also need to create 4 migrations (3 for your table, plus one to do some kind of edit), 2 JS models (you may or may not need a model for your join table), and a seed file.

# "This is boring! We can't see anything!"
Honestly, I feel ya. But the fact of the matter is, a lot of the work you'll do will be purely backend and there won't be anything to "see." No friendly GUI to interact with, no pretty colors, no fun animations. Just a bunch of code and a database. Now, your next project is going to be *all about* hooking up a DB to a server and client for display, but for now, we're going to focus on *just* the data.

If you can set up migrations, models, and seeds for a database, you're in a good place to start building out the rest of your app. **That** is the skill we're looking for with this project.

# Tech Checklist

## Entity Relationship Diagram (ERD)
Remember, this project is about creating a `many to many` relationship, and your ERD should reflect that.

- [ ] You created an ERD for your database
- [ ] Your primary parent table is exists
- [ ] Your join table exists
- [ ] Your secondary parent table exists
- [ ] Your primary parent class displays the right crows feet to the join
- [ ] Your secondary parent class displays the right crows feet to the join
- [ ] All properties on the primary parent are present in your diagram
- [ ] All properties on the secondary parent are present in your diagram
- [ ] All properties on the join table are present in your diagram
- [ ] All required foreign keys are present in your diagram


## Migrations
- [ ] You have an NPM script to create a new migration file
- [ ] You have an NPM script to run your migrations
- [ ] You have an NPM script to rollback your migrations
- [ ] You have a migration to create you primary parent table
- [ ] You have a migration to create you join table
- [ ] You have a migration to create you secondary parent table
- [ ] Your migrations are created in such a way that you **only need 3 migrations in total to establish the relationships properly**
- [ ] You have one extra migration to perform some edit/add a column on one of your existing tables
  - This migration should not be where you establish the relationships between your tables!
- [ ] Each migration sets up a table with a primary parent key that goes up by 1 for each new record
- [ ] Foreign keys are present in your migrations in the correct place
- [ ] There are the correct number of foreign keys in your migrations
- [ ] Your migrations feature a text column
- [ ] Your migrations feature a date column
- [ ] Your migrations feature a boolean column
- [ ] Your migrations feature a number column
- [ ] Your migrations must have a unique constraint on a field
- [ ] Your migrations must feature a default value for a field
- [ ] Your primary parent has at least 5 columns
- [ ] Your secondary parent has at least 3 columns

The parent table migration should have:
- [ ] an `up` function that returns a promise
- [ ] a `down` function that returns a promise
- [ ] The `down` function should undo the action of the `up` function

The secondary parent table migration should have:
- [ ] an `up` function that returns a promise
- [ ] a `down` function that returns a promise
- [ ] The `down` function should undo the action of the `up` function

The join table migration should have:
- [ ] an `up` function that returns a promise
- [ ] a `down` function that returns a promise
- [ ] The `down` function should undo the action of the `up` function

The edit migration should have:
- [ ] an `up` function that returns a promise
- [ ] a `down` function that returns a promise
- [ ] The `down` function should undo the action of the `up` function

## Models
Models are how we interact with our database in JS. Now, depending on your project that `join` table may have a real world counterpart (like `appointments`) but they may also be purely for the database (like `book_genres`). Because of this, you may not *need* a model for your middle entity, so we aren't requiring it here.

- [ ] You have a model for your primary parent table
- [ ] You have a model for your secondary parent table
- [ ] Each model always returns instances
  - Instead of returning raw data, your model should return instances of the model class (or secondary model class)

The primary parent model should have:
- [ ] `create` method that takes an object of data and returns a the data (including id) of the new record
- [ ] `list` method that returns all records
- [ ] `find` method that returns a single record specified by id
- [ ] `findBy` method that returns a single record specified by a field
- [ ] `update` method that updates a record and returns the data of the updated record
- [ ] `destroy` method that deletes a record and returns true if successful (null otherwise)
- [ ] `SOME AGGREGATOR` at least one method on your class must use a SQL aggregator function
- [ ] `listAll[SECONDARY]` method that returns all records of the secondary parent that are related to the primary parent
  - So think `duneBook.listAllGenres()` or `tom.listAllFriends()`
- [ ] `createNew[SECONDARY]` method that takes in data to create the secondary resource, but it will already be associated by default to the primary resource.
  - For example, `duneBook.createNewGenre({ name: 'Science Fiction' })`
- [ ] `add[SECONDARY]` method that takes in a secondary resource and associates it with the primary resource
  - For example, `duneBook.addGenre(scienceFictionGenre)`
- [ ] `remove[SECONDARY]` method that takes in a secondary resource and disassociates it with the primary resource
  - For example, `duneBook.removeGenre(scienceFictionGenre)`, note this does not destroy the resource itself, just the association!
- [ ]


The secondary parent is much simpler, and all it needs are the basics:
- [ ] `create` method that takes an object of data and returns a the data (including id) of the new record
- [ ] `list` method that returns all records
- [ ] `find` method that returns a single record specified by id
- [ ] `findBy` method that returns a single record specified by a field
- [ ] `update` method that updates a record and returns the data of the updated record
- [ ] `destroy` method that deletes a record and returns true if successful (null otherwise)
- [ ] `SOME AGGREGATOR` at least one method on your class must use a SQL aggregator function
- [ ] `listAll[SECONDARY]` method that returns all records of the secondary parent that are related to the primary parent


## Seed
You only need 1 seed file!

- [ ] a seed file exists
- [ ] All existing tables are cleared at the start of the seed file
- [ ] 10 instances of the primary parent are created
- [ ] 5 instances of the secondary parent are created
- [ ] At least 10 joins are created between the primary and secondary parents
- [ ] An NPM script exists to run your seed file