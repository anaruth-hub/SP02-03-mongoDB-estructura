SP02-03-mongoDB-estructura — MongoDB Data Modeling (Optics Store)
📖 Description

This repository contains a MongoDB (NoSQL) data modeling solution for the optics store “Cul d'Ampolla”.
It includes two alternative modeling approaches, supported by Draw.io diagrams and JSON sample data:

Exercise 01: Separate collections + references (ObjectId-style)

Exercise 02: UI-oriented model where glasses are the main “view” (catalog + purchase history)

🧭 Table of Contents

Requirements

Exercise Statement

Deliverables

Exercise 01

Exercise 02

Technologies

Setup & Execution

How to Validate

Repository Structure

✅ Requirements / Completion Criteria

To complete this task, the repository includes:

A MongoDB data model for the domain

Two alternative solutions (Exercise 01 + Exercise 02)

Diagrams explaining each model

Example JSON documents/collections

Documentation describing structure and technical decisions

📌 Exercise Statement

An optics store called “Cul d'Ampolla” wants to computerize the management of customers and eyeglasses sales.

The system must store:

Supplier

Name

Address (street, number, floor, door, city, ZIP code, country)

Phone, fax, NIF

Glasses

Brand

Graduation per lens (left / right)

Frame type (floating / plastic / metallic)

Frame color

Lens color (left / right)

Price

Customer

Name

Postal address

Phone

Email

Registration date

Recommended by another customer (optional)

Sales

Employee who sold each pair of glasses

Date/time of sale

✨ Deliverables / What’s Included
Exercise 01 — Separate Collections + References

Goal: Model the domain using reusable entities with minimal duplication, using references between documents.

Artifacts:

Diagram:

model/optica_exercise01.drawio

model/optica_exercise01.drawio.png

Sample data:

mongo_data/Exercise01/

Collections:

customer

employee

supplier

glasses

sale

Key decision:
Use reference fields to represent relationships, for example:

sale.customer_id

sale.employee_id

sale.glasses_id

glasses.supplier_id

Exercise 02 — UI-Oriented Model (Glasses as Main View)

Goal: Optimize reads when the UI perspective is “glasses” (catalog + purchase history), using a single main collection.

Artifacts:

Diagram:

model/optica_exercise02.drawio

model/optica_exercise02.drawio.png

Sample data:

mongo_data/Exercise02/glasses_catalog.json

Main collection:

glasses_catalog

Key decisions:

Embed supplier details inside each glasses document

Store purchase history in purchased_by[], including:

customer snapshot

employee info

sale date/time

✅ This approach prioritizes a single-query UI read, trading some controlled denormalization for performance.

🛠 Technologies

Database: MongoDB

Tools: MongoDB Compass, Draw.io

Version Control: Git / GitHub

🚀 Setup & Execution
1) Clone the repository
git clone <YOUR_GITHUB_REPO_URL>
cd SP02-03-mongoDB-estructura

2) Run MongoDB

Use MongoDB locally or with Docker.

Default connection example:

mongodb://localhost:27017

3) Import JSON data (MongoDB Compass)

Open MongoDB Compass

Connect to MongoDB (mongodb://localhost:27017)

Create/open databases (recommended names):

optica_store (Exercise 01)

optica_store_ex2 (Exercise 02)

Create collections and import the .json files using Import Data

Validate using:

Documents tab

Schema tab

🔍 How to Validate (Checklist)

Before submitting, confirm:

 Exercise 01 database includes: customer, employee, supplier, glasses, sale

 Exercise 01 collections use reference fields for relationships

 Exercise 02 database includes: glasses_catalog

 glasses_catalog embeds supplier details and contains purchased_by[]

 Diagrams exist in /model for both exercises

 JSON sample data exists in /mongo_data

📁 Repository Structure
model/
  ├─ optica_exercise01.drawio
  ├─ optica_exercise01.drawio.png
  ├─ optica_exercise02.drawio
  └─ optica_exercise02.drawio.png

mongo_data/
  ├─ Exercise01/
  └─ Exercise02/

README.md
