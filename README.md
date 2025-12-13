# Raja-Mantri-Chor-Sipahi Game Backend  
A lightweight Python Flask backend for the classic 4-player Indian game **Raja–Mantri–Chor–Sipahi**, built using **CSV files as the database** (no SQL / NoSQL required).  
Designed to be easy to test using **Postman** and simple to deploy on any server.

---

## 🎯 Features

- 🔹 Create and join rooms
- 🔹 Auto-assign roles when 4 players join
- 🔹 Private role viewing (each player sees only their role)
- 🔹 Mantri guessing system with score calculation
- 🔹 Multiple rounds per room with cumulative points
- 🔹 CSV-based database (thread-safe)
- 🔹 Clean REST API with proper error codes
- 🔹 Works fully without frontend (Postman-only workflow)

---

## 🎮 Game Rules

**Roles:**
- **Raja (King):** Observer — gets **1000 points**
- **Mantri (Minister):** Must guess the Chor — gets **800 points if correct**
- **Chor (Thief):** Avoids detection
- **Sipahi (Soldier):** Supports Mantri — gets **500 points if Mantri is correct**

**Scoring Logic:**

| Case | Raja | Mantri | Sipahi | Chor |
|------|------|--------|--------|------|
| ✔️ Mantri correct | 1000 | 800 | 500 | 0 |
| ❌ Mantri wrong   | 1000 | 0 | 0 | **1300** |

---

## 🚀 Setup & Run

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
python app.py
```

---

## 📁 Project Structure

```
raja-mantri-game/
├── app.py
├── models.py
├── game_logic.py
├── database.py
├── requirements.txt
├── data/
│   ├── rooms.csv
│   ├── players.csv
│   └── games.csv
└── README.md
```

---

## 📡 API Documentation

### 1️⃣ Create Room  
**POST** `/room/create`

### 2️⃣ Join Room  
**POST** `/room/join`

### 3️⃣ Get Room Players  
**GET** `/room/players/<room_id>`

### 4️⃣ Assign Roles  
**POST** `/room/assign/<room_id>`

### 5️⃣ View My Role  
**GET** `/role/me/<room_id>/<player_id>`

### 6️⃣ Submit Guess  
**POST** `/guess/<room_id>`
    
### 7️⃣ Get Results  
**GET** `/result/<room_id>`

### 8️⃣ Leaderboard  
**GET** `/leaderboard/<room_id>`

### 9️⃣ Health Check  
**GET** `/health`

---

## 🛠️ Troubleshooting

- Ensure `data/` folder exists  
- Change port if needed  
- Recreate virtual environment if broken  

---

## 📄 License
Free for personal and educational use.
