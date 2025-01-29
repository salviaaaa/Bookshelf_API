# Bookshelf API 📚

A RESTful API service for managing your digital book collection. Built with Hapi.js framework and Node.js, this API allows you to organize and track your reading materials efficiently.

## Features ✨

- Create and manage book entries
- Track reading progress
- Organize books by various attributes
- Filter and search capabilities
- RESTful API architecture

## Tech Stack 🛠️

- Node.js
- Hapi.js Framework
- Nodemon
- Postman (for testing)

## Quick Start 🚀

1. **Setup**
   ```bash
   # Clone repository
   git clone [repository-url]

   # Install dependencies
   npm install

   # Start server
   npm run start
   ```

2. **Testing**
   - Import provided Postman collection and environment files
   - Select "Bookshelf API Test" environment
   - Run the test suite

Server runs at `localhost:9000` by default.

## API Endpoints 🔌

### Books Management

#### Create Book
- **POST** `/books`
- Creates new book entry
- Required fields: name, pageCount
- Returns: Book ID

#### Get Books
- **GET** `/books`
- Lists all books
- Supports filtering and pagination
- Returns: Array of books

#### Get Book Details
- **GET** `/books/{bookId}`
- Retrieves detailed book information
- Returns: Complete book data

#### Update Book
- **PUT** `/books/{bookId}`
- Updates existing book information
- Returns: Success status

#### Delete Book
- **DELETE** `/books/{bookId}`
- Removes book from collection
- Returns: Success status

## Response Format 📝

### Success Response
```json
{
    "status": "success",
    "data": {
        // Response data
    }
}
```

### Error Response
```json
{
    "status": "fail",
    "message": "Error description"
}
```

## Project Structure 📁

```
src/
├── handler.js   # Request handlers
├── books.js     # Data management
├── server.js    # Server configuration
└── routes.js    # API routes
```

## Development 👨‍💻

### Prerequisites
- Node.js v14+
- npm
- Postman

### Local Development
1. Clone repository
2. Install dependencies: `npm install`
3. Start development server: `npm run start`

## Testing Guide 🧪

1. Import test files from `./test/` directory
2. Configure Postman environment
3. Execute test suite

Test files:
- Collection: `./test/Bookshelf API Test.postman_collection.json`
- Environment: `./test/Bookshelf API Test.postman_environment.json`

## Contributing 🤝

1. Fork repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Submit pull request

## Credits 📜

- Developed for Dicoding Indonesia course
- [View Certification](https://www.dicoding.com/certificates/53XEDJ40YPRN)

## Resources 📚

- [Hapi.js Documentation](https://hapi.dev/)
- [Node.js Documentation](https://nodejs.org/)
- [Dicoding Indonesia](https://www.dicoding.com/)