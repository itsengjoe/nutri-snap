# NutriSnap Development Setup

## Prerequisites

- Node.js (v16 or higher)
- Python (v3.8 or higher)
- PostgreSQL (v12 or higher)
- Git

## Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up environment variables:
   - Copy `.env.example` to `.env`
   - Update the values with your configuration

5. Initialize the database:
   ```bash
   alembic upgrade head
   ```

6. Start the backend server:
   ```bash
   uvicorn main:app --reload
   ```

## Frontend Setup

1. Navigate to the project root:
   ```bash
   cd ..
   ```

2. Install frontend dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables:
   - Copy `.env.example` to `.env`
   - Update the values with your configuration

4. Start the development server:
   ```bash
   npm run dev
   ```

## Development Workflow

1. Start both backend and frontend servers
2. Access the application at `http://localhost:5173`
3. The backend API will be available at `http://localhost:8000`

## Database Migrations

To create a new migration:
```bash
alembic revision --autogenerate -m "Description of changes"
```

To apply migrations:
```bash
alembic upgrade head
```

To downgrade migrations:
```bash
alembic downgrade -1
```

## Code Structure

### Backend
- `main.py`: Application entry point
- `core/`: Configuration and security utilities
- `models/`: Database models
- `schemas/`: Pydantic schemas for validation
- `routers/`: API route handlers
- `services/`: Business logic and external service integrations
- `database.py`: Database connection and session management
- `dependencies.py`: FastAPI dependencies

### Frontend
- `src/App.tsx`: Main application component with routing
- `src/pages/`: Page components for each route
- `src/components/`: Reusable UI components
- `src/hooks/`: Custom React hooks
- `src/lib/`: Utility functions and context providers

## API Documentation

When the backend is running, API documentation is available at:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

## Testing

### Backend
Run tests with:
```bash
pytest
```

### Frontend
Run tests with:
```bash
npm test
```

## Deployment

### Backend
```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Frontend
```bash
npm run build
```

The build output will be in the `dist/` directory.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Write tests if applicable
5. Commit your changes
6. Push to the branch
7. Create a pull request