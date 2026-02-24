# Drishyamitra Backend

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Set your Groq API key in .env
# GROQ_API_KEY=your_key_here

# Run the server
python app.py
```

The server starts at `http://localhost:5000`.

## API Endpoints

### Auth
- `POST /api/auth/signup` — Register
- `POST /api/auth/login` — Login

### Photos
- `POST /api/photos/upload` — Upload with metadata
- `GET /api/photos` — List (filter by category, tag, person, search, favorites)
- `GET /api/photos/<id>` — Get details
- `PATCH /api/photos/<id>/favorite` — Toggle favorite
- `DELETE /api/photos/<id>` — Delete

### Faces
- `POST /api/faces/detect` — Detect faces in image
- `PUT /api/faces/<id>/assign` — Assign name

### Persons
- `GET /api/persons` — List all
- `GET /api/persons/<id>/photos` — Photos by person
- `POST /api/persons` — Create
- `DELETE /api/persons/<id>` — Delete

### Other
- `GET /api/categories` — List categories
- `GET /api/tags` — List tags
- `GET /api/dashboard/stats` — Dashboard stats
- `POST /api/chat` — AI chat (Groq)
- `GET /api/health` — Health check

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `SECRET_KEY` | Flask secret key | dev default |
| `GROQ_API_KEY` | Groq API key for AI chat | (fallback mode) |
| `GROQ_MODEL` | Groq model name | `llama-3.1-8b-instant` |
