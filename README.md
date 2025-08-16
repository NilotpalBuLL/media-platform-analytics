# 📊 Media Platform Analytics

Media Platform Analytics is a backend project built with **FastAPI** that provides REST APIs to manage and analyze media platform data.  
It enables collecting content usage data, tracking user activity, and generating analytics for decision-making.  

---

## 🚀 Features
- FastAPI-powered RESTful API
- User and media content management
- Analytics endpoints to generate insights
- Database integration (SQLite/PostgreSQL)
- Modular and scalable code structure
- Interactive API docs with Swagger UI (`/docs`)

---

## 🛠️ Tech Stack
- **Backend Framework:** FastAPI  
- **Server:** Uvicorn  
- **Database:** SQLite (default), PostgreSQL (optional)  
- **Language:** Python 3.10+  

---

## What's added
- POST /media/{id}/view  -> logs a view (IP + timestamp)
- GET /media/{id}/analytics -> returns total_views, unique_ips, and views_per_day

## Quickstart
1. Create and activate virtualenv
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # Windows: .venv\Scripts\activate
   ```
2. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```
3. Copy .env.example to .env and set SECRET_KEY

4. Run server
   ```bash
   uvicorn app.main:app --reload
   ```

## Test flow (curl)
1) Signup
```bash
curl -X POST "http://127.0.0.1:8000/auth/signup" -H "Content-Type: application/json" -d '{"email":"admin@example.com","password":"StrongPass123"}'
```

2) Login (get token)
```bash
curl -X POST "http://127.0.0.1:8000/auth/login" -H "Content-Type: application/x-www-form-urlencoded" -d "username=admin@example.com&password=StrongPass123"
```

3) Create media
```bash
curl -X POST "http://127.0.0.1:8000/media" -H "Authorization: Bearer <TOKEN>" -H "Content-Type: application/json" -d '{"title":"Test Video","type":"video","file_url":"https://example.com/video.mp4"}'
```

4) Log a view
```bash
curl -X POST "http://127.0.0.1:8000/media/1/view" -H "Authorization: Bearer <TOKEN>"
```

5) Get analytics
```bash
curl -X GET "http://127.0.0.1:8000/media/1/analytics" -H "Authorization: Bearer <TOKEN>"
```
