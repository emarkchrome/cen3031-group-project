# Deployment & Setup Guide

This guide covers how to set up the StudySmart application for development and deployment.

## Prerequisites
- **Node.js**: Version 18 or higher is recommended.
- **Oracle Database**: Access to an Oracle database (specifically the UF CISE Oracle instance for this project).
- **VPN**: If accessing the UF CISE database from off-campus, you must be connected to the UF VPN.

## Environment Variables

### Server (`server/.env`)
Create a `.env` file in the `server` directory with the following:

```env
# Database Credentials
DB_USER=your_db_username
DB_PASSWORD=your_db_password

# OpenAI API Key (for content generation)
OPENAI_API_KEY=your_openai_api_key

# Port (Optional, defaults to 3000)
PORT=3000
```

### Client (`client/.env.local`)
Create a `.env.local` file in the `client` directory:

```env
# Clerk Authentication Key
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
```

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/cen3031-studysmart/cen3031-group-project.git
   cd cen3031-group-project
   ```

2. **Install Root Dependencies** (if any):
   ```bash
   npm install
   ```

3. **Install Client Dependencies**:
   ```bash
   cd client
   npm install
   ```

4. **Install Server Dependencies**:
   ```bash
   cd ../server
   npm install
   ```

## Running the Application

### Development Mode
You need to run both the client and server concurrently.

1. **Start the Server**:
   ```bash
   cd server
   npm run dev # or node app.js
   ```
   The server will start on `http://localhost:3000`.

2. **Start the Client**:
   Open a new terminal window.
   ```bash
   cd client
   npm run dev
   ```
   The client will start on `http://localhost:5173` (typically).

### Production Build

1. **Build Client**:
   ```bash
   cd client
   npm run build
   ```
   This generates static files in `client/dist`.

2. **Serve**:
   You can serve the static files using a static file server or configure the Express backend to serve them.
