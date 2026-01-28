Project Name

MongoDB Structure – Optics (Cul d'Ampolla)
Description: This repository contains the NoSQL (MongoDB) data modeling solution for the “Cul d'Ampolla” optics store. It includes two alternative models (Exercise 01 and Exercise 02) expressed as diagrams (Draw.io) and JSON collection examples.

📌 Exercise Statement (if applicable)

An optics store called “Cul d'Ampolla” wants to computerize the management of customers and eyeglasses sales.

The system must store:

Supplier

Name

Address: street, number, floor, door, city, zip code, country

Phone, fax, NIF

Glasses

Brand

Graduation for each lens (left/right)

Frame type (floating / plastic / metallic)

Frame color

Lens color (left/right)

Price

Customer

Name

Postal address

Phone

Email

Registration date

Recommended by another customer (optional)

Sales

Which employee sold each pair of glasses

Date/time of the sale

✨ Features (if applicable)

Exercise 01: Classic MongoDB modeling using separate collections (customers, employees, suppliers, glasses, sales) with references between documents.

Exercise 02: UI-oriented modeling where glasses are the main “view” (catalog), embedding provider info and purchase history in a single document structure.

🛠 Technologies

Database: MongoDB

Tools: MongoDB Compass, Draw.io

Version Control: Git / GitHub

🚀 Installation and Run

Clone the repository:
git clone <YOUR_GITHUB_REPO_URL>

Start MongoDB (local or Docker) and open MongoDB Compass.
Default connection example:
mongodb://localhost:27017

Import the JSON files into MongoDB Compass:

Create/open the database for each exercise (recommended naming):

optica_store (Exercise 01)

optica_store_ex2 (Exercise 02)

Create the collections and use Import Data to load the .json files.

Validate your data structure using Compass (Documents / Schema tabs).

No automated tests are included because this task focuses on data modeling and documentation.

📸 Demo (if applicable)

Not applicable. (This project is a data model + documentation repository.)

🧩 Diagrams and Technical Decisions (if applicable)
Exercise 01 (Separate Collections + References)

Goal: model the domain with normalized collections and references (similar to relational thinking but in MongoDB).
Included artifacts:

Diagram: model/optica_exercise01.drawio and model/optica_exercise01.drawio.png

Sample collections (JSON): mongo_data/Exercise01/

Collections:

customer

employee

supplier

glasses

sale

Key decision: Use ObjectId references between collections (e.g., sale.customer_id, sale.employee_id, sale.glasses_id, glasses.supplier_id) to avoid duplication and keep entities reusable.

Exercise 02 (Glasses as the “View” / UI-Oriented Model)

Goal: If the UI perspective is “glasses”, keep a single document structure focused on catalog + purchase history.
Included artifacts:

Diagram: model/optica_exercise02.drawio and model/optica_exercise02.drawio.png

Sample collection (JSON): mongo_data/Exercise02/glasses_catalog.json

Main collection:

glasses_catalog

Key decision:

Embed provider details inside the glasses document.

Use an array purchased_by[] to keep purchase history, including customer snapshot and employee/sale info.

This design prioritizes reading the full UI view in one query, at the cost of some controlled duplication (denormalization).

📁 Repository Structure

model/ → Draw.io diagrams (.drawio and exported .png)

mongo_data/Exercise01/ → JSON files for Exercise 01 collections

mongo_data/Exercise02/ → JSON file for Exercise 02 collection

README.md → Project documentation
