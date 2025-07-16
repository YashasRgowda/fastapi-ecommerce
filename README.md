# 🛍️ Full-Stack Ecommerce Application

A modern, full-stack ecommerce application built with **FastAPI** (Python) backend and **React** frontend, featuring a clean architecture and responsive design.

![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

## 📋 Table of Contents

- [✨ Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [📁 Project Structure](#-project-structure)
- [📋 Prerequisites](#-prerequisites)
- [🚀 Installation & Setup](#-installation--setup)
- [🔧 Environment Variables](#-environment-variables)
- [🏃‍♂️ Running the Application](#️-running-the-application)
- [🌐 Access Points](#-access-points)
- [📚 API Documentation](#-api-documentation)
- [📱 Usage](#-usage)
- [🐛 Troubleshooting](#-troubleshooting)
- [🔄 Development Workflow](#-development-workflow)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## ✨ Features

### 🔒 Authentication & Security
- JWT-based authentication system
- User registration and login
- Password hashing with bcrypt
- Protected routes and middleware

### 🛒 Product Management
- Browse products with responsive card layout
- Detailed product views
- Product search and filtering
- Admin product management (CRUD operations)

### 🎨 Modern UI/UX
- Fully responsive design
- Clean, modern interface
- Smooth animations and transitions
- Mobile-first approach

### 🗄️ Database & API
- RESTful API architecture
- MongoDB integration with Motor (async)
- Data validation with Pydantic
- Comprehensive error handling

## 🛠️ Tech Stack

### Backend
- **FastAPI** - Modern, fast web framework for building APIs
- **Motor** - Asynchronous MongoDB driver
- **MongoDB** - NoSQL database
- **Pydantic** - Data validation and settings management
- **JWT** - JSON Web Tokens for authentication
- **Bcrypt** - Password hashing
- **Uvicorn** - ASGI server

### Frontend
- **React 18** - JavaScript library for building user interfaces
- **Vite** - Next generation frontend tooling
- **TailwindCSS** - Utility-first CSS framework
- **React Router** - Declarative routing
- **React Query** - Data fetching and caching
- **Redux Toolkit** - State management
- **React Icons** - Icon library

### DevOps & Tools
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **Mongo Express** - Web-based MongoDB admin interface

## 📁 Project Structure

```
ecommerce-app/
├── backend/
│   ├── src/
│   │   ├── app.py                 # FastAPI application factory
│   │   ├── main.py                # Application entry point
│   │   ├── auth/                  # Authentication module
│   │   │   ├── __init__.py
│   │   │   ├── models.py          # Auth Pydantic models
│   │   │   ├── router.py          # Auth routes
│   │   │   └── utils.py           # Auth utilities
│   │   ├── config/                # Configuration
│   │   │   └── __init__.py
│   │   ├── database/              # Database connection
│   │   │   └── __init__.py
│   │   ├── middlewares/           # Custom middlewares
│   │   │   └── cors.py
│   │   ├── models/                # Pydantic models
│   │   │   ├── common.py          # Base models
│   │   │   ├── products.py        # Product models
│   │   │   └── users.py           # User models
│   │   └── routers/               # API routes
│   │       ├── __init__.py
│   │       ├── products.py        # Product endpoints
│   │       └── users.py           # User endpoints
│   ├── requirements.txt           # Python dependencies
│   └── venv/                      # Virtual environment
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── api/                   # API configuration
│   │   ├── auth/                  # Auth providers
│   │   ├── components/            # Reusable components
│   │   │   ├── Footer/
│   │   │   ├── Header/
│   │   │   ├── Layout/
│   │   │   └── Products/
│   │   ├── hooks/                 # Custom hooks
│   │   ├── pages/                 # Page components
│   │   │   ├── Home/
│   │   │   ├── Login/
│   │   │   └── Product/
│   │   ├── redux/                 # State management
│   │   ├── services/              # API services
│   │   └── styles/                # Global styles
│   ├── package.json               # Node.js dependencies
│   └── tailwind.config.cjs        # Tailwind configuration
├── docker-compose.yml             # Docker services
├── .env.example                   # Environment variables template
└── README.md                      # Project documentation
```

## 📋 Prerequisites

Before running this application, make sure you have the following installed:

- **Python 3.12+** 
- **Node.js 16+** 
- **Docker & Docker Compose** (for MongoDB)
- **Git**

### Check your versions:
```bash
python3 --version
node --version
docker --version
docker-compose --version
```

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd ecommerce-app
```

### 2. Backend Setup

#### Create Virtual Environment
```bash
cd backend
python3.12 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

#### Install Dependencies
```bash
pip install -r requirements.txt
```

#### Install Additional Dependencies (if needed)
```bash
pip install "passlib[bcrypt]" "python-jose[cryptography]"
pip install 'pydantic[email]'
```

### 3. Frontend Setup
```bash
cd ../frontend
npm install
```

## 🔧 Environment Variables

### Create Backend Environment File
Create `.env` in the root directory:
```bash
# MongoDB Configuration
MONGO_USERNAME=admin
MONGO_PASSWORD=password123
MONGO_DB_NAME=ecommerce
MONGO_DB_HOST=localhost
MONGO_DB_PORT=27017

# CORS Configuration
CORS=http://localhost:5173

# JWT Configuration
SECRET_KEY=your-super-secret-key-change-in-production
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

### Create Frontend Environment File
Create `frontend/.env.local`:
```bash
VITE_API_URL=http://localhost:8000
VITE_TOKEN_KEY=ecommerce_token
```

## 🏃‍♂️ Running the Application

### 1. Start MongoDB (using Docker)
```bash
# From the root directory
docker-compose up -d
```

This starts:
- MongoDB on port `27017`
- Mongo Express (web admin) on port `8081`

### 2. Start the Backend
```bash
cd backend
source venv/bin/activate
cd src
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

### 3. Start the Frontend
```bash
# In a new terminal
cd frontend
npm run dev
```

## 🌐 Access Points

Once everything is running:

| Service | URL | Description |
|---------|-----|-------------|
| **Frontend** | http://localhost:5173 | React application |
| **Backend API** | http://localhost:8000 | FastAPI server |
| **API Docs** | http://localhost:8000/docs | Interactive API documentation |
| **MongoDB Admin** | http://localhost:8081 | Mongo Express interface |

## 📚 API Documentation

The API is fully documented with Swagger/OpenAPI. Visit http://localhost:8000/docs for:

- Interactive API explorer
- Request/response schemas
- Authentication testing
- Live API testing

### Main Endpoints

#### Authentication
- `POST /auth/login` - User login
- `POST /auth/signup` - User registration

#### Products
- `GET /api/v1/products/` - Get all products
- `GET /api/v1/products/{id}` - Get product by ID
- `POST /api/v1/products/` - Create new product
- `PUT /api/v1/products/{id}` - Update product
- `DELETE /api/v1/products/{id}` - Delete product

## 📱 Usage

### Adding Test Data

1. Visit http://localhost:8000/docs
2. Navigate to `POST /api/v1/products/`
3. Click "Try it out"
4. Use this sample data:

```json
{
  "name": "MacBook Pro 16-inch",
  "description": "Apple MacBook Pro with M2 chip, 16GB RAM, 512GB SSD",
  "price": 2499.99
}
```

5. Click "Execute"
6. Check the frontend to see your product

### User Authentication

1. Go to http://localhost:5173/login
2. Create a new account or login
3. Browse products and features

## 🐛 Troubleshooting

### Common Issues

#### Backend won't start
```bash
# Check if virtual environment is activated
source backend/venv/bin/activate

# Reinstall dependencies
pip install -r requirements.txt

# Check Python version
python --version  # Should be 3.12+
```

#### Frontend build errors
```bash
# Clear node modules and reinstall
rm -rf node_modules package-lock.json
npm install

# Check Node version
node --version  # Should be 16+
```

#### Database connection issues
```bash
# Restart Docker containers
docker-compose down
docker-compose up -d

# Check container status
docker-compose ps
```

#### CORS errors
- Ensure `.env` file has correct CORS setting
- Check frontend is running on port 5173
- Restart backend after changing environment variables

## 🔄 Development Workflow

### Making Changes

1. **Backend changes**: Server auto-reloads with `--reload` flag
2. **Frontend changes**: Vite provides hot module replacement
3. **Database changes**: Use Mongo Express at http://localhost:8081

### Code Style
- Backend: Follow PEP 8 Python style guide
- Frontend: Use ESLint and Prettier (configure as needed)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Run tests (when available)
5. Commit changes: `git commit -m 'Add feature'`
6. Push to branch: `git push origin feature-name`
7. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- FastAPI documentation and community
- React and Vite teams
- MongoDB team
- TailwindCSS team
- All open-source contributors

---
