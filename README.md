✅ What this repo contains

db.json — sample data (users)

package.json — scripts to run the fake API

this README.md — instructions

🔧 Prerequisites

Node.js (v12+) and npm installed.

Postman (or any REST client).

Basic terminal / PowerShell familiarity.

1. Create project folder
mkdir json-server-demo
cd json-server-demo
npm init -y

2. Install json-server

You can install as a devDependency or use npx (no install needed).

Option A — local devDependency

npm install json-server --save-dev


Option B — run without installing

npx json-server --watch db.json --port 5000

3. Add sample db.json

Create a file named db.json in the project root and paste:

{
  "users": [
    { "id": 1, "name": "Nikhil", "skill": "full stack developer" },
    { "id": 2, "name": "Atul",   "skill": "front end developer" },
    { "id": 3, "name": "Sanket", "skill": "back end developer" },
    { "id": 4, "name": "Ankush", "skill": "data scientist" },
    { "id": 5, "name": "Rohit",  "skill": "devops engineer" }
  ]
}

4. Add an npm script (recommended)

Open package.json and add a server script under "scripts":

"scripts": {
  "server": "json-server --watch db.json --port 5000",
  "start": "node index.js"
}


Now you can run:

npm run server


Expected console output:

JSON Server is running
Resources
http://localhost:5000/users

5. Endpoints json-server gives you

GET /users → list all users

GET /users/1 → get user with id=1

POST /users → create new user (auto id)

PUT /users/1 → replace user with id=1

PATCH /users/1 → partial update user id=1

DELETE /users/1 → delete user id=1
json-server also supports query params like ?name=Atul or _sort, _page, _limit.

6. Test with Postman — step-by-step
A) GET all users

Method: GET

URL: http://localhost:5000/users

Send → should return array of 5 user objects (200 OK)

B) GET single user

Method: GET

URL: http://localhost:5000/users/1

Send → returns object for Nikhil

C) POST (create)

Method: POST

URL: http://localhost:5000/users

Body → raw JSON:

{
  "name": "Rahul",
  "skill": "mobile developer"
}


Send → response includes created object with id (201 Created).

D) PUT (replace)

Method: PUT

URL: http://localhost:5000/users/2

Body:

{
  "id": 2,
  "name": "Atul Updated",
  "skill": "frontend dev"
}


Send → replaces the entire record.

E) PATCH (partial update)

Method: PATCH

URL: http://localhost:5000/users/3

Body:

{ "skill": "backend engineer" }


Send → only skill changes.

F) DELETE

Method: DELETE

URL: http://localhost:5000/users/5

Send → 200 OK and user removed.

7. Helpful Postman tips

Use JSON (application/json) as content-type for body.

Save requests to a collection for reuse.

Use Tests tab in Postman to write basic asserts (e.g., pm.test("status is 200", ()=> pm.response.to.have.status(200));).

8. Common problems & fixes
npm error Missing script: "server"

You ran npm run server but "server" is not in package.json. Add the script (see step 4) or run with npx:

npx json-server --watch db.json --port 5000

A complete log of this run can be found in: ... npm-cache\_logs\...

Open the referenced log file (path shown in the error) for details. On Windows it’s typically:

C:\Users\<YourUser>\AppData\Local\npm-cache\_logs\<timestamp>-debug-0.log

Port already in use

If 5000 is taken, use another port:

npx json-server --watch db.json --port 4000

CORS issues from browser-based apps

json-server has CORS enabled by default. If you see CORS problems in development, ensure your browser app is using the correct http://localhost:5000 URL.

9. Extra tips

Use _delay or advanced middleware if you want to simulate latency.

You can add relationships (e.g., posts referencing userId) and json-server will auto-handle nested routes (see json-server docs).

To persist changes across runs, edit db.json or commit it to your repo.

10. Example package.json (minimal)
{
  "name": "json-server-demo",
  "version": "1.0.0",
  "scripts": {
    "server": "json-server --watch db.json --port 5000"
  },
  "devDependencies": {
    "json-server": "^0.17.0"
  }
}

🎉 You're done!

Start the server (npm run server or npx json-server ...) and test the endpoints in Postman.
