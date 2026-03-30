# Instructions

## Setup Instructions

1. Open the project in your IDE (VSCode recommended)
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up MongoDB:
   - Install MongoDB locally or use a cloud service (MongoDB Atlas)
   - Ensure MongoDB is running on the default port (27017) or configure your connection
4. Configure environment variables (optional):
   - Create a `.env` file in the root directory
   - Add `PORT=3001` (or your preferred port)
   - Add MongoDB connection string if needed

## Running the Application

### Development Mode

Start the server with hot reload:
```bash
npm run watch
```

Or with environment variables:
```bash
npm run watch:prod
```

### Production Mode

Start the server:
```bash
npm start
```

Or with environment variables:
```bash
npm run start:prod
```

The application will start on port 3001 (or the port specified in your environment).

## Testing

### Run All Tests
```bash
npm test
```

### Run Unit Tests Only
```bash
npm run test:unit
```

### Run Component Tests Only
```bash
npm run test:component
```

## Code Quality

### Linting
```bash
npm run lint
```

The project uses ESLint with Airbnb configuration and Prettier for code formatting.

## API Endpoints

### Books Collection

**GET /books**
- Returns list of all books
- Supports both HTML and JSON responses
- Content negotiation via Accept header

**POST /books**
- Creates or updates a book
- Request body:
  ```json
  {
    "title": "Book Title",
    "authors": ["Author Name"],
    "isbn": "1234567890",
    "description": "Book description"
  }
  ```
- Validates input using Joi schema
- Redirects to book details after success

**GET /books/:isbn**
- Returns details of a specific book by ISBN
- Supports both HTML and JSON responses
- Returns 404 if book not found

## Project Structure

```
nodejs-layered-architecture/
├── src/
│   ├── controllers/       # HTTP request handlers
│   │   └── bookController.js
│   ├── services/          # Business logic
│   │   └── bookService.js
│   ├── repositories/      # Data access layer
│   │   ├── bookRepository.js (MongoDB)
│   │   └── inMemoryBookRepository.js
│   ├── middlewares/       # Express middlewares
│   │   ├── errorMiddleware.js
│   │   ├── layoutMiddleware.js
│   │   └── validateBookMiddleware.js
│   ├── routes/            # Route definitions
│   │   └── bookRoutes.js
│   ├── utils/             # Utility functions
│   │   ├── makeSlug.js
│   │   └── validateBook.js
│   ├── views/             # Handlebars templates
│   │   ├── layout.hbs
│   │   ├── books.hbs
│   │   └── book.hbs
│   ├── links/             # Link/URL helpers
│   │   └── links.js
│   ├── connection.js      # Database connection
│   ├── app.js             # Express app setup
│   └── server.js          # Server entry point
├── test/
│   ├── unit/              # Unit tests
│   └── component/         # Integration tests
└── package.json
```

## Architecture Layers

### 1. Controller Layer
- Handles HTTP requests and responses
- Performs content negotiation (HTML/JSON)
- Delegates business logic to services
- Uses dependency injection

### 2. Service Layer
- Contains business logic
- Independent of HTTP concerns
- Transforms data (e.g., creates slugs)
- Calls repositories for data access

### 3. Repository Layer
- Abstracts data access
- Provides a clean interface for data operations
- Can be swapped (MongoDB, in-memory, etc.)
- Handles database queries

### 4. Middleware Layer
- Input validation
- Error handling
- Layout management
- Cross-cutting concerns

## Database

The application uses MongoDB with the following schema:

**Books Collection:**
```javascript
{
  title: String,
  slug: String,      // Auto-generated from title
  authors: [String],
  isbn: String,      // Unique identifier
  description: String
}
```

## Development Tips

1. **Adding a new resource:**
   - Create repository in `src/repositories/`
   - Create service in `src/services/`
   - Create controller in `src/controllers/`
   - Create routes in `src/routes/`
   - Add tests in `test/unit/` and `test/component/`

2. **Error handling:**
   - All errors are caught by the error middleware
   - Use try-catch in controllers with `wrapWithTryCatch`
   - Return appropriate HTTP status codes

3. **Testing:**
   - Unit tests should mock dependencies
   - Component tests should test the full stack
   - Use Supertest for HTTP testing

4. **Code style:**
   - Husky runs pre-commit hooks automatically
   - Lint-staged formats code before commit
   - Follow Airbnb JavaScript style guide

## Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running: `mongod`
- Check connection string in code
- Verify port 27017 is available

### Port Already in Use
- Change the port in environment variables
- Kill the process using the port: `lsof -ti:3001 | xargs kill`

### Tests Failing
- Ensure MongoDB is running for component tests
- Check that all dependencies are installed
- Verify Node version compatibility

## Author

* **Or Assayag** - *Initial work* - [orassayag](https://github.com/orassayag)
* Or Assayag <orassayag@gmail.com>
* GitHub: https://github.com/orassayag
* StackOverflow: https://stackoverflow.com/users/4442606/or-assayag?tab=profile
* LinkedIn: https://linkedin.com/in/orassayag
