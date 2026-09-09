# ML Railway Deployment

A machine learning API for house price prediction deployed on Railway, built with FastAPI.

## Project Structure

```
m4_s3_ml_railway/
├── app_1.py              # Basic ML prediction API
├── app_2.py              # CRUD API with SQLite
├── app_3.py              # Production API with MySQL (deployed version)
├── requirements.txt      # Python dependencies
├── railway.toml          # Railway deployment configuration
├── linear_regression.joblib  # Trained model
├── selected_features.csv     # Feature selection metadata
└── .env                      # Environment variables (not in repo)
```

## Applications

### app_1.py - Basic ML API
- Simple endpoint for house price predictions
- Upload CSV file and get predictions
- Health check endpoint

### app_2.py - CRUD API
- Full CRUD operations for items
- SQLite database integration
- Pagination and search functionality

### app_3.py - Production API (Deployed)
- House price prediction with MySQL database
- Stores predictions in database
- Health check with database connectivity
- Timezone-aware timestamps (America/Lima)

## API Endpoints

### app_3.py (Production)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/health` | Health check |
| POST | `/predict` | Upload CSV for predictions |

### app_2.py (CRUD)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/items/` | List items with pagination |
| GET | `/items/{id}` | Get item by ID |
| POST | `/items/` | Create new item |
| PUT | `/items/{id}` | Update item |
| DELETE | `/items/{id}` | Delete item |
| GET | `/items/search/{query}` | Search items by name |

## Local Development

1. Clone the repository:
```bash
git clone https://github.com/Josephnicolay/m4_s3_ml_railway.git
cd m4_s3_ml_railway
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the development server:
```bash
uvicorn app_3:app --reload
```

## Deployment

This project is configured for deployment on Railway. The `railway.toml` file specifies:
- Build using Nixpacks
- Start command: `uvicorn app_3:app --host 0.0.0.0 --port $PORT`
- Health check endpoint: `/health`

## Environment Variables

For production deployment, set the following environment variable:
- `SQLALCHEMY_DATABASE_URL` - MySQL connection string

## License

MIT
