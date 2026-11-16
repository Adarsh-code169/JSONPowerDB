# Student Enrollment Form — JsonPowerDB Micro Project

## Table of Contents
- [Description](#description)
- [Benefits of using JsonPowerDB](#benefits-of-using-jsonpowerdb)
- [Scope of Functionalities](#scope-of-functionalities)
- [Examples of Use](#examples-of-use)
- [Project Status](#project-status)
- [Sources](#sources)
- [Release History](#release-history)

## Description
A web form that stores student records in the **STUDENT-TABLE** relation of the **SCHOOL-DB** database on JsonPowerDB (JPDB).
Fields: Roll No (primary key), Full Name, Class, Birth Date, Address, Enrollment Date.
Built with HTML, Bootstrap, jQuery and the JPDB REST API — no separate backend server.

## Benefits of using JsonPowerDB
- Simplest way to retrieve data in JSON format
- Schema-free, simple to use, nimble and in-memory database
- Built-in, real-time indexing, so lookups by key are fast
- Serverless support: the frontend talks to the database directly over REST
- Minimum development cost and time to market
- Supports multiple data modes: document DB, key-value DB, RDBMS-style relations

## Scope of Functionalities
1. On page load only **Roll No** is enabled; all buttons are disabled.
2. When the user leaves Roll No, the app checks JPDB (`GET_BY_KEY` on `/api/irl`):
   - **Not found** → fields enabled, **Save** and **Reset** enabled.
   - **Found** → record shown, Roll No locked, **Update** and **Reset** enabled.
3. **Save** validates all fields and inserts with `PUT` on `/api/iml`.
4. **Update** validates and changes the existing record with `UPDATE` using its `rec_no`.
5. **Reset** returns the form to its initial state.

## Examples of Use
1. Enter Roll No `101` → new student → fill details → **Save**.
2. Enter Roll No `101` again → details load → edit Class → **Update**.

## How to Run
1. Log in at login2explore.com/jpdb and copy your connection token.
2. Paste it into `connToken` in `index.html` (do **not** commit a real token to a public repo).
3. Open `index.html` directly in a browser. The JPDB API is plain `http`, so a page served over
   `https` (e.g. GitHub Pages) will have its requests blocked as mixed content.

## Project Status
Completed (v1.0). Possible next steps: delete record, list all students, search by name.

## Sources
- JsonPowerDB documentation — login2explore.com/jpdb
- Login2Xplore micro-internship lectures

## Release History
- **v1.1** — Show JPDB errors instead of false success messages; handle failed lookups.
- **v1.0** — Initial release: Save, Update, Reset with field validation.
