# 🎯 DrishyaMitra — AI-Powered Photo Management

**DrishyaMitra** is a full-stack AI-powered photo management application that leverages generative AI for intelligent photo analysis, face recognition, smart tagging, and a conversational chat assistant to help you organize and search through your photo library effortlessly.

> Built for the **GenAI Hackathon 2026**

---

## ✨ Features

### 📸 Photo Management
- **Upload & Store** — Upload photos (PNG, JPG, JPEG, WebP, GIF, BMP) up to 10 MB each
- **Gallery View** — Browse all your photos in a responsive grid with modal viewer
- **AI-Powered Analysis** — Automatic scene detection, object recognition, and description generation using **Groq Vision API (LLaMA 3.1)**
- **Smart Tagging** — Auto-generated tags + custom user tags for easy categorization
- **Categories** — Pre-seeded categories for organizing photos

### 👤 Face Recognition
- **Automatic Face Detection** — Powered by **MediaPipe BlazeFace** model
- **Person Labeling** — Label detected faces and group photos by people
- **People View** — Browse all recognized people and their associated photos

### 📁 Folder Management
- **Create Folders** — Organize photos into custom folders
- **Smart Folders** — Create folders via chat assistant based on search queries

### 🤖 AI Chat Assistant
- **Natural Language Search** — Find photos by describing what you're looking for
- **Chat-Based Actions** — Create folders, search photos, and manage your library through conversation
- **Intent Detection** — Automatic recognition of user commands (create folder, search, list, etc.)
- **Powered by Groq** — Uses LLaMA 3.1 8B Instant for fast, intelligent responses

### 📊 Dashboard
- **Analytics Overview** — Total photos, storage usage, face counts, and category breakdowns
- **Recent Uploads** — Quick access to your latest photos

### 🔐 Authentication
- **JWT-Based Auth** — Secure user registration and login
- **Protected Routes** — All API endpoints and frontend pages require authentication

---

## 🏗️ Tech Stack

### Backend
| Technology | Purpose |
|---|---|
| **Flask 3.x** | Web framework |
| **Flask-SQLAlchemy** | ORM & database (SQLite) |
| **Flask-JWT-Extended** | JWT authentication |
| **Flask-CORS** | Cross-origin resource sharing |
| **Groq SDK** | AI/LLM integration (LLaMA 3.1) |
| **MediaPipe** | Face detection |
| **OpenCV** | Image processing |
| **Pillow** | Image handling |
| **Python 3.10+** | Runtime |

### Frontend
| Technology | Purpose |
|---|---|
| **React 18** | UI library |
| **TypeScript** | Type-safe JavaScript |
| **Vite 5** | Build tool & dev server |
| **Tailwind CSS 3** | Utility-first styling |
| **Shadcn/UI (Radix)** | Accessible component library |
| **React Router 6** | Client-side routing |
| **TanStack React Query** | Server state management |
| **Recharts** | Dashboard charts |
| **Lucide React** | Icons |
| **Sonner** | Toast notifications |

---

## 📁 Project Structure

```
genAI hackathon/
├── drishyamitra-backend/           # Flask Backend
│   ├── app.py                      # Application factory & entry point
│   ├── config.py                   # Configuration (DB, JWT, Groq, uploads)
│   ├── requirements.txt            # Python dependencies
│   ├── .env                        # Environment variables
│   ├── models/                     # SQLAlchemy models
│   │   ├── user.py                 # User model
│   │   ├── photo.py                # Photo model
│   │   ├── face.py                 # Face detection model
│   │   ├── person.py               # Person (labeled face) model
│   │   ├── folder.py               # Folder model
│   │   └── associations.py         # Categories & many-to-many tables
│   ├── routes/                     # API route blueprints
│   │   ├── auth.py                 # POST /api/auth/register, /login
│   │   ├── photos.py               # CRUD /api/photos
│   │   ├── faces.py                # GET /api/faces
│   │   ├── persons.py              # CRUD /api/persons
│   │   ├── folders.py              # CRUD /api/folders
│   │   ├── tags.py                 # GET /api/tags
│   │   ├── categories.py           # GET /api/categories
│   │   ├── chat.py                 # POST /api/chat
│   │   └── dashboard.py            # GET /api/dashboard
│   ├── services/                   # Business logic layer
│   │   ├── auth_service.py         # Authentication logic
│   │   ├── photo_service.py        # Photo upload & AI analysis
│   │   ├── face_service.py         # Face detection & recognition
│   │   ├── person_service.py       # Person management
│   │   ├── chat_service.py         # AI chat processing
│   │   └── chat_actions.py         # Chat action handlers
│   ├── uploads/                    # Uploaded photo storage
│   └── instance/                   # SQLite database file
│
├── drishyamitra-frontend/          # React Frontend
│   ├── package.json                # Node.js dependencies
│   ├── vite.config.ts              # Vite configuration
│   ├── tailwind.config.ts          # Tailwind CSS config
│   ├── src/
│   │   ├── App.tsx                 # Root app with routing
│   │   ├── lib/api.ts              # API client (Axios/Fetch)
│   │   ├── pages/
│   │   │   ├── Landing.tsx         # Landing / home page
│   │   │   ├── Login.tsx           # Login page
│   │   │   ├── Signup.tsx          # Registration page
│   │   │   ├── Dashboard.tsx       # Analytics dashboard
│   │   │   ├── Gallery.tsx         # Photo gallery grid
│   │   │   ├── UploadPage.tsx      # Photo upload with AI scan
│   │   │   ├── People.tsx          # People / face groups
│   │   │   ├── Folders.tsx         # Folder management
│   │   │   └── ChatAssistant.tsx   # AI chat interface
│   │   └── components/             # Reusable UI components
│   └── public/                     # Static assets
│
├── .gitignore
└── README.md                       # ← You are here
```

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.10+** — [Download Python](https://www.python.org/downloads/)
- **Node.js 18+** — [Download Node.js](https://nodejs.org/)
- **Git** — [Download Git](https://git-scm.com/)
- **Groq API Key** — [Get a free key](https://console.groq.com/keys)

### 1. Clone the Repository

```bash
git clone https://github.com/bhanu-teja1977/404-Error-Not-Found-.git
cd 404-Error-Not-Found-
```

### 2. Backend Setup

```bash
cd drishyamitra-backend

# Create a virtual environment (recommended)
python -m venv venv

# Activate the virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

#### Configure Environment Variables

Create a `.env` file in the `drishyamitra-backend/` directory:

```env
# Groq API Key (REQUIRED — get yours at https://console.groq.com/keys)
GROQ_API_KEY=your_groq_api_key_here

# Flask Secret Key
SECRET_KEY=your-secret-key-here

# CORS Allowed Origins
ALLOWED_ORIGINS=http://localhost:5173,http://localhost:5174

# JWT Token Expiration (seconds) — default: 24 hours
JWT_ACCESS_TOKEN_EXPIRES=86400

# Backend Base URL
BACKEND_URL=http://localhost:5000
```

#### Run the Backend

```bash
python app.py
```

The backend will start at **http://localhost:5000**

### 3. Frontend Setup

```bash
cd drishyamitra-frontend

# Install dependencies
npm install

# Start the development server
npm run dev
```

The frontend will start at **http://localhost:5173**

---

## 🔌 API Endpoints

### Authentication
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Login & get JWT token |

### Photos
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/photos` | Get all photos (with filters) |
| `POST` | `/api/photos/upload` | Upload a photo (with AI analysis) |
| `GET` | `/api/photos/<id>` | Get photo details |
| `DELETE` | `/api/photos/<id>` | Delete a photo |

### Faces & People
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/faces` | Get all detected faces |
| `GET` | `/api/persons` | Get all labeled people |
| `POST` | `/api/persons` | Create/label a person |
| `PUT` | `/api/persons/<id>` | Update a person |

### Folders
| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/folders` | Get all folders |
| `POST` | `/api/folders` | Create a folder |
| `GET` | `/api/folders/<id>` | Get folder with photos |
| `DELETE` | `/api/folders/<id>` | Delete a folder |

### Others
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/chat` | Send message to AI assistant |
| `GET` | `/api/dashboard` | Get dashboard analytics |
| `GET` | `/api/tags` | Get all tags |
| `GET` | `/api/categories` | Get all categories |
| `GET` | `/api/health` | Health check |

---

## 🧠 AI Features Explained

### Photo Analysis Pipeline
1. User uploads a photo
2. **MediaPipe BlazeFace** detects faces in the image
3. **Groq Vision API (LLaMA 3.1)** analyzes the image for:
   - Scene description
   - Object detection
   - Auto-generated tags
   - Confidence scores
4. Results are stored with the photo metadata

### Chat Assistant
The AI chat assistant uses a **pre-processing intent detector** that recognizes commands like:
- `"Create a folder called Vacation"` → Creates a folder
- `"Show me photos of sunsets"` → Searches by tags/description
- `"How many photos do I have?"` → Returns stats
- `"Find photos with people"` → Filters by face detection

---

## 🛠️ Development

### Backend Commands
```bash
# Run in debug mode
python app.py

# Install a new dependency
pip install <package-name>
pip freeze > requirements.txt
```

### Frontend Commands
```bash
# Development server
npm run dev

# Production build
npm run build

# Run tests
npm run test

# Lint
npm run lint
```

---

## 👥 Team — 404 Error Not Found

Built with ❤️ for the **GenAI Hackathon 2026**

---

