# My Blog Backend

A Node.js backend server for a React blog application with MongoDB integration.

## Features

- RESTful API endpoints for blog articles
- MongoDB database integration
- Article upvoting functionality
- Comment system
- Static file serving for React frontend
- Development server with hot reload

## Tech Stack

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Babel** - JavaScript transpilation
- **Nodemon** - Development server

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (running on localhost:27017)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd my-blog-backend
```

2. Install dependencies:
```bash
npm install
```

3. Make sure MongoDB is running on your local machine:
```bash
mongod
```

## Usage

### Development Mode

Start the development server with hot reload:
```bash
npm run dev
```

The server will start on port 8000. You can access it at `http://localhost:8000`.

### Production Mode

Build the React frontend and start the server:
```bash
npm start
```

## API Endpoints

### Hello Endpoints
- `GET /hello` - Returns "Hello!"
- `POST /hello` - Returns "Hello {name}!" (expects JSON body with `name` field)
- `GET /hello/:name` - Returns "Hello {name}!"

### Article Endpoints
- `GET /api/articles/:name` - Get article by name
- `POST /api/articles/:name/upvote` - Upvote an article
- `POST /api/articles/:name/add-comment` - Add a comment to an article (expects JSON body with `comment` field)

## Database

The application uses MongoDB with the database name `react-blog-db`. The main collection is `articles` which stores:
- Article name
- Upvote count
- Comments array

## Project Structure

```
src/
├── server.js          # Main server file
├── withDB.js          # Database connection utility
└── build/             # React frontend build files
    ├── index.html
    ├── static/
    └── ...
```

## Development

The project uses Babel for ES6+ transpilation and Nodemon for automatic server restarts during development.

## License

All Rights Reserved. This software is proprietary and confidential. 
See LICENSE file for details.
