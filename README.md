# US Air Travel Analysis using Spark and MongoDB

A full-stack data analysis platform for exploring trends in U.S. air travel. The project leverages **Apache Spark** for large-scale processing, **MongoDB** for flexible storage, and a modern web interface built with **Next.js** to visualize insights. Deployed using **Docker Compose** for containerized orchestration.

---

## Architecture Overview

```
             +-------------------+
             |    Frontend UI    |
             |  (Next.js React)  |
             +--------+----------+
                      |
                      v
             +-------------------+
             |     Node.js API   |
             +--------+----------+
                      |
                      v
             +-------------------+
             |     MongoDB       |
             +-------------------+
                      ^
                      |
             +--------+----------+
             |   Apache Spark    |
             | (ETL + Analytics) |
             +-------------------+
```

---

## Features

- Process and clean large-scale air travel datasets using Apache Spark
- Store enriched data in MongoDB
- Visualize trends using a React + Next.js dashboard
- Use Docker Compose for full environment setup
- Data loading scripts with Python and Node.js
- Explore travel vs. economic indicators (GDP, employee count, etc.)

---

## Tech Stack

- **Backend**: Node.js, Express.js, MongoDB
- **Frontend**: Next.js, TypeScript
- **Data Processing**: Apache Spark, PySpark
- **Infrastructure**: Docker, Docker Compose
- **Database**: MongoDB
- **Languages**: Python, JavaScript, TypeScript

---

## Project Structure

```
US-Air-Travel-Analysis/
├── backend/                  # Node.js API server
│   ├── models/               # MongoDB schema models
│   ├── routes/               # API route definitions
│   └── index.js              # Express app entry point
│
├── frontend/air-data-analysis/  # Next.js frontend
│   ├── pages/                # App pages and components
│   └── public/               # Static files
│
├── data-dumping.ipynb        # Jupyter notebook for loading raw data
├── playaround.ipynb          # Exploratory notebook
├── downloadScript.py         # Data scraping utility
├── unzip.py                  # Helper to unzip bulk files
├── docker-compose.yml        # Docker orchestration
├── requirements.txt          # Python dependencies
```

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/US-Air-Travel-Analysis.git
cd US-Air-Travel-Analysis
```

### 2. Start the Environment

```bash
docker-compose up --build
```

This will spin up:
- MongoDB database
- Node.js backend API
- Frontend Next.js interface

### 3. Load Data

Run the Jupyter notebook `data-dumping.ipynb` to clean and insert initial data into MongoDB using PySpark.

---

## API Endpoints

- `GET /api/gdp` – Get GDP-related data
- `GET /api/flightEcon` – Fetch flight economics trends
- `GET /api/employees` – Fetch employee insights

---

## Sample Queries

```js
// Get passengers by year
db.CleanPassengerInfo.aggregate([
  { $group: { _id: "$Year", total: { $sum: "$Passengers" } } },
  { $sort: { _id: 1 } }
])
```

---

## Future Enhancements

- Add support for airline delays and weather correlation
- Real-time dashboard updates via WebSockets
- Deploy to cloud using Kubernetes or AWS ECS

---

## License

MIT License. See `LICENSE` file for more details.
