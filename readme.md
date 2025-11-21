### 🛡️ Cyber Security Chatbot API (Vercel Ready)

A simple and powerful **FastAPI-based chatbot** trained with essential **cyber security knowledge** such as phishing, malware, ransomware, SQL injection, and encryption.

This version is optimized for **Serverless Deployment (Vercel)** by using a static knowledge base.

## 🚀 Features

  * 🔐 Preloaded cyber-security knowledge base
  * 🤖 Smart keyword-based chatbot system
  * ⚡ **Built with FastAPI** (High performance)
  * ☁️ **Vercel Ready** (Configured for serverless)
  * 🧪 Easy to test using Postman
  * 📖 Read-only architecture (Prevents serverless file-write errors)

## 📁 Project Structure

```text
cyber-chatbot/
│── chatbot.py           # Main application file
│── cyber_data.json      # Static knowledge base (Must be included in repo)
│── vercel.json          # Vercel configuration file
│── requirements.txt     # Python dependencies
│── README.md
```

## 📦 Installation & Local Run

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/cyber-chatbot.git
cd cyber-chatbot
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Run the Server locally

```bash
python -m uvicorn chatbot:app --reload
```

Server will start at: `http://127.0.0.1:8000`

## ☁️ Deployment on Vercel

To deploy this successfully, you **must** have the following files in your root directory:

### 1\. `vercel.json`

Create this file to tell Vercel how to run FastAPI:

```json
{
  "builds": [
    {
      "src": "chatbot.py",
      "use": "@vercel/python"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "chatbot.py"
    }
  ]
}
```

### 2\. `requirements.txt`

Ensure it contains:

```text
fastapi
uvicorn
```

### 3\. Deploy

Push to GitHub and import the project into Vercel. It will deploy automatically without 404 errors.

## 📚 Endpoints

### ✔️ `POST /chat`

Send a message to the chatbot.

**URL:**
`https://your-vercel-app.vercel.app/chat`

**Body (JSON):**

```json
{
  "message": "What is phishing?"
}
```

**Response:**

```json
{
  "user": "What is phishing?",
  "bot": "Phishing is a cyber attack where attackers trick users..."
}
```

### ✔️ `GET /`

Check if the API is running.

## 🗂️ Data Storage Note

**Important for Vercel Users:**
Since Vercel uses a **Read-Only File System**, this bot reads responses from `cyber_data.json` but **does not save new chat history** to the file.

  * `cyber_data.json` → Serves as a static database for answers.
  * If you need to save history, you must connect a cloud database (e.g., MongoDB Atlas, Supabase).

## 🤝 Contributing

You can expand the knowledge base by adding new topics to `cyber_data.json` and pushing the changes to GitHub.

## 🛡️ License

Free to use for personal and educational purposes.

-----

