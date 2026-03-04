# 🚀 Clean Architecture & SOLID Authentication System

![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D)

## 📌 Overview
A production-ready Fullstack application demonstrating advanced software design patterns. This project moves away from traditional monolithic codebases by strictly adhering to **SOLID Principles** and **Clean Architecture**. 

Instead of relying on ES6 Classes and the confusing `this` context, the entire backend is built using **Factory Functions and Closures** to achieve true encapsulation and functional-style Dependency Injection (DI).

## ✨ Key Features & Architectural Highlights

### 🛡️ Backend (Node.js / Express / MongoDB)
* **Dependency Injection (DI) Container:** All modules (Controllers, Repositories, Services) are loosely coupled. Dependencies are injected during the bootstrapping phase, making the system 100% database-agnostic and highly testable.
* **Factory Functions over Classes:** Eliminates `this` binding issues and provides true private state using JavaScript Closures.
* **Global Error Handling:** Say goodbye to repetitive `try/catch` blocks. A custom `catchAsync` wrapper and a centralized `globalErrorHandler` manage all HTTP responses and operational errors cleanly.
* **Advanced JWT Authentication:** * Implements a secure dual-token system (Short-lived Access Token + Long-lived Refresh Token).
  * Robust `authMiddleware` for protecting private routes.

### 💻 Frontend (Vue 3 / Pinia / Vite)
* **Domain-Driven API Services:** API calls are not cluttered inside Vue components. They are separated into domain-specific services (`authService`, `userService`) and injected with a centralized Axios HTTP Client.
* **Interceptor & Request Queueing:** Features a bulletproof Axios Response Interceptor that gracefully handles `401 Unauthorized` errors. It pauses failed requests, silently refreshes the token in the background, and retries the queued requests without interrupting the User Experience (UX).
* **Custom Composables (`useAsync`):** Abstracts away repetitive loading, error, and data state management, keeping Vue components strictly focused on the UI layer.

## 📂 Project Structure

The project is strictly organized to enforce the **Separation of Concerns**:

### 🛡️ Backend (Express.js)
```text
backend/
├── server.js              # Entry point: DI Container & Server bootstrapping
├── database/              # DB connection setups (MongoDB/Mongoose)
├── controllers/           # Business logic coordinators (Agnostic to Express)
├── middlewares/           # Global & Route-specific middlewares (Auth protect)
├── repositories/          # Data access layer (Encapsulates DB queries)
├── routes/                # Route definitions (Adapters between HTTP & Controllers)
├── services/              # Domain-independent services (JWT, Email, etc.)
└── utils/                 # Utilities (AppError, catchAsync, Hasher, Validator)

frontend/
├── src/
│   ├── main.js            # Entry point: Wiring DI & Global configurations
│   ├── App.vue            # Root component
│   ├── assets/            # Global styles and static assets
│   ├── components/        # Reusable UI components (Buttons, Inputs, Modals)
│   ├── views/             # Page components (LoginView, ProfileView, HomeView)
│   ├── router/            # Vue Router definitions & Navigation guards
│   ├── stores/            # State management (Pinia stores: auth.js, user.js)
│   ├── composables/       # Reusable logic (useAsync.js, useForm.js)
│   └── services/          # API Communication layer
│       ├── index.js       # Service Factory: DI for all API services
│       ├── authService.js # Authentication endpoints (Login, Register)
│       ├── userService.js # User-related endpoints (Profile, CRUD)
│       └── core/          # Core HTTP configurations
│           ├── httpClient.js # Axios instance & Interceptor logic
│           └── TokenQueue.js # Handling concurrent token refresh requests
```

## ⚙️ Getting Started

### Prerequisites
* Node.js (v18+)
* MongoDB (Local instance or MongoDB Atlas)

### Installation

1. **Clone the repository:**
    git clone https://github.com/YourUsername/fullstack-solid-auth.git
    cd fullstack-solid-auth

2. **Setup Backend:**
    cd backend
    npm install
    # Create a .env file based on the provided .env.example
    npm run dev

3. **Setup Frontend:**
    cd ../frontend
    npm install
    npm run dev

## 🤝 Let's Connect
Built with passion and a relentless focus on clean code. If you're a recruiter or fellow developer, feel free to reach out to discuss software architecture!
