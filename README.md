# 🚀 JSON Server — Fake REST API + Postman Testing Guide

This project demonstrates how to create a **fake REST API** using `json-server` and test it using **Postman** — perfect for practicing front-end integration or backend simulation.

---

## 📁 Project Overview

**Tools Used:**  
- 🟢 Node.js & npm  
- 🧰 JSON Server  
- 📬 Postman  

**Features:**  
✅ Create, Read, Update, Delete (CRUD) operations  
✅ Test all endpoints in Postman  
✅ Easy setup — ready in 2 minutes  

---

## ⚙️ Step 1: Create Project Folder

```bash
mkdir json-server-demo
cd json-server-demo
npm init -y
📦 Step 2: Install JSON Server
bash
Copy code
npm install json-server --save-dev
✅ Check installation:

bash
Copy code
npx json-server --version
🗂️ Step 3: Create db.json
Create a new file called db.json in your project root and add the following data 👇

json
Copy code
{
  "users": [
    { "id": 1, "name": "Nikhil", "skill": "full stack developer" },
    { "id": 2, "name": "Atul", "skill": "front end developer" },
    { "id": 3, "name": "Sanket", "skill": "back end developer" },
    { "id": 4, "name": "Ankush", "skill": "data scientist" },
    { "id": 5, "name": "Rohit", "skill": "devops engineer" }
  ]
}
🧩 Step 4: Add Server Script in package.json
Open package.json and add this line under "scripts" 👇

json
Copy code
"scripts": {
  "server": "json-server --watch db.json --port 5000"
}
▶️ Step 5: Start the JSON Server
bash
Copy code
npm run server
🎉 You’ll see:

arduino
Copy code
JSON Server is running
Resources
http://localhost:5000/users
🌐 Step 6: Test Endpoints in Browser or Postman
Method	Endpoint	Description
GET	http://localhost:5000/users	Fetch all users
GET	http://localhost:5000/users/1	Fetch user with ID 1
POST	http://localhost:5000/users	Add a new user
PUT	http://localhost:5000/users/1	Replace user with ID 1
PATCH	http://localhost:5000/users/1	Update user partially
DELETE	http://localhost:5000/users/1	Delete user with ID 1

💥 Step 7: Test with Postman (Example Requests)
🧾 GET — All Users
Method: GET

URL: http://localhost:5000/users

➕ POST — Add New User
Method: POST

URL: http://localhost:5000/users

Body (raw JSON):

json
Copy code
{
  "name": "Rahul",
  "skill": "mobile developer"
}
🔁 PUT — Replace User
Method: PUT

URL: http://localhost:5000/users/2

Body (raw JSON):

json
Copy code
{
  "id": 2,
  "name": "Atul Updated",
  "skill": "frontend engineer"
}
✏️ PATCH — Update Specific Field
Method: PATCH

URL: http://localhost:5000/users/3

Body (raw JSON):

json
Copy code
{
  "skill": "backend expert"
}
❌ DELETE — Remove User
Method: DELETE

URL: http://localhost:5000/users/5

⚠️ Common Errors & Fixes
❌ npm error Missing script: "server"
✅ Fix: Add the "server" script in package.json or run directly with:

bash
Copy code
npx json-server --watch db.json --port 5000
❌ Port Already in Use
✅ Fix: Change port number:

bash
Copy code
npx json-server --watch db.json --port 4000
❌ npm ERR! A complete log of this run can be found...
✅ Fix: Check log file for exact error:
C:\Users\<YourUser>\AppData\Local\npm-cache\_logs\<timestamp>-debug-0.log

💡 Extra Tips
Use --delay 1000 to simulate network latency

bash
Copy code
npx json-server --watch db.json --port 5000 --delay 1000
Add relationships like posts → users using foreign keys.

Use Postman Collections to organize your API tests.

📚 Example package.json
json
Copy code
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
✨ Final Result
Once started, open in your browser:
👉 http://localhost:5000/users

You’ll see your JSON data as an API response 🎯

💖 Author
👨‍💻 Nikhil Mali
Full Stack Developer
📫 Reach me on GitHub or LinkedIn

🏁 License
This project is licensed under the MIT License — free to use and modify.

⭐ If you found this helpful, don’t forget to star the repo! ⭐




