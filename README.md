# Practice Spring Boot + PostgreSQL Project

## What is inside
- Backend: Spring Boot (Java 17, Maven) with a simple `User` entity and two endpoints:
  - `GET /api/users` - list users
  - `POST /api/users` - add user
- Frontend: `frontend/index.html` (plain HTML/JS) that calls the backend API.
- `src/main/resources/data.sql` seeds two users on first run.

## How to run locally (slow & steady)
1. Install Java 17 (or compatible) and Maven.
2. Install PostgreSQL and create a database named `testdb`.
   Example:
     - create database: `createdb testdb`
     - or in psql: `CREATE DATABASE testdb;`
3. Edit `src/main/resources/application.properties` if your Postgres username/password/database differ.
4. From the project root run:
   ```
   mvn clean package
   mvn spring-boot:run
   ```
   The backend will start on `http://localhost:8080`.
5. Serve the frontend:
   - Option A (quick): run a static server from the `frontend` folder:
     ```
     cd frontend
     python -m http.server 5500
     ```
     then open `http://localhost:5500` in your browser.
   - Option B: Open `frontend/index.html` with a live-server extension (VSCode) or similar.

## Notes
- The frontend uses `http://localhost:8080/api/users` as the API. When deploying, change `API_BASE` in `frontend/index.html` to your deployed backend URL (for example Render's URL).
- CORS: The backend controller allows all origins (`@CrossOrigin("*")`) for easy local testing. Tighten this in production.

## Deployment
- Frontend can go to Netlify (static).
- Backend + Postgres can go to Render or Railway (managed Postgres).

Have fun practicing! If you want, I can also create a GitHub repo for this or produce a Dockerfile next.
