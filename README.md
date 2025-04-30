
# 🤖 GenAI PDF Reader Bot

An AI-powered mobile app that answers natural language questions from uploaded PDFs using **LangChain**, **OpenAI GPT-4**, and **ChromaDB**.

## 🧱 Tech Stack

| Layer        | Technology                         |
|--------------|------------------------------------|
| Frontend     | React Native CLI                   |
| Backend API  | Express.js                         |
| Storage      | Amazon S3                          |
| GenAI Engine | LangChain + OpenAI (GPT-4) + ChromaDB |
| Parsing      | PyMuPDF                            |
| Language     | JavaScript (Node.js) + Python      |

---

## 🚀 Features

- Upload any PDF from a mobile device
- Ask questions in plain English
- Get accurate, context-aware answers using GPT-4
- Efficient performance using chunking, embeddings, and RAG pipeline

---

## 📱 React Native Frontend

```bash
npx react-native init GenAIPDFReader
npm install axios react-native-document-picker
```

### Core Functions

- `DocumentPicker` for PDF uploads
- `axios` to send form-data with PDF and question to backend
- Display bot response from the server

> See `App.js` for implementation

---

## 🌐 Express.js Backend

```bash
npm init -y
npm install express multer aws-sdk dotenv cors axios
```

### Endpoints

- `POST /ask`: Upload PDF to **Amazon S3**, then forward request to Python microservice.

### Config (.env)

```dotenv
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
AWS_REGION=your_region
S3_BUCKET=your_bucket
PYTHON_SERVICE_URL=http://localhost:5000/ask
```

---

## 🧠 Python GenAI Service (FastAPI + LangChain)

```bash
pip install fastapi uvicorn python-multipart openai langchain chromadb PyMuPDF requests
```

### Key Functions

- Download PDF from S3
- Parse and chunk text with `PyMuPDF`
- Embed chunks with `OpenAIEmbeddings`
- Store vectors in **ChromaDB**
- Use `RetrievalQA` + GPT-4 to answer user’s question

### Run Server

```bash
uvicorn main:app --host 0.0.0.0 --port 5000
```

---

## 🖼 Architecture Overview

```mermaid
graph TD
  RN[📱 React Native App]
  RN -->|PDF + Question| BE[🌐 Express.js Backend]
  BE -->|Upload PDF| S3[(☁️ Amazon S3)]
  BE -->|Forward Request| PY[🧠 Python FastAPI (LangChain)]
  PY -->|Download PDF| S3
  PY -->|Answer| BE
  BE --> RN
```

---

## ✅ TODO / Enhancements

- [ ] Add authentication (Firebase/Auth0)
- [ ] Multi-document support
- [ ] Caching via ChromaDB persistence
- [ ] Show source passages for answers

---

## 🧠 Powered By

- [LangChain](https://www.langchain.com/)
- [OpenAI GPT-4](https://platform.openai.com/)
- [ChromaDB](https://www.trychroma.com/)
- [React Native](https://reactnative.dev/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Amazon S3](https://aws.amazon.com/s3/)

---

## 📬 Contact

Created by [Kaushal](mailto:mail4kaushal.kr@gmail.com) • Contributions welcome!

---

Would you like me to bundle this into a zip structure or set up GitHub Actions for CI/deployment?
