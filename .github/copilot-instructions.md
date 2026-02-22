# GitHub Copilot Instructions

## Project Overview
This is a Node.js/Express backend for a React blog application. It exposes a REST API for articles (fetch, upvote, add comments) and serves the React frontend static build. Data is stored in a local MongoDB instance (`react-blog-db`).

## Tech Stack
- **Runtime**: Node.js
- **Framework**: Express 5
- **Database**: MongoDB (via the `mongodb` driver, local instance on port `27017`)
- **Transpiler**: Babel (`@babel/core`, `@babel/node`, `@babel/preset-env`) — ES module `import/export` syntax is used throughout
- **Dev server**: nodemon

## Code Style & Conventions
- Use ES module syntax (`import`/`export`), not CommonJS (`require`).
- Use `async/await` for all asynchronous operations.
- Keep route handlers thin — delegate DB logic to helper functions (e.g. `withDB`).
- Use `res.status(200).json(data)` for successful API responses.
- Use `res.status(500).send(...)` for error responses.
- Use single quotes for strings in JS files.

## Project Structure
```
src/
  server.js     # Express app, route definitions, static file serving
  withDB.js     # MongoDB connection helper
  build/        # React frontend static build (served by Express)
```

## API Routes
| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/articles/:name` | Fetch a single article by name |
| POST | `/api/articles/:name/upvote` | Increment upvote count for an article |
| POST | `/api/articles/:name/add-comment` | Append a comment to an article |
| GET | `*` | Serve the React frontend (`build/index.html`) |

## Database
- **DB name**: `react-blog-db`
- **Collection**: `articles`
- **Article document shape**:
  ```json
  {
    "name": "string",
    "upvotes": "number",
    "comments": ["string"]
  }
  ```
- Always open and close the MongoDB client within each request using the `withDB` helper.

## Dev Scripts
- `npm run dev` — Start the dev server with nodemon + babel-node
