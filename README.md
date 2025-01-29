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
```
{
    "status": "success",
    "data": {
        // Response data
    }
}
```

### Error Response
```
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

## API Specifications 📋

### 1. Server Configuration
- Server must run on port 9000
- Application must be started using `npm run start` command
- Package.json should contain:
  ```
  {
    "scripts": {
      "start": "node src/server.js",
      "start-dev": "nodemon src/server.js"
    }
  }
  ```

### 2. API Endpoints Detail

#### Create Book (POST /books)
**Request Body:**
```
{
    "name": string,
    "year": number,
    "author": string,
    "summary": string,
    "publisher": string,
    "pageCount": number,
    "readPage": number,
    "reading": boolean
}
```

**Stored Book Structure:**
```
{
    "id": "Qbax5Oy7L8WKf74l",
    "name": "Buku A",
    "year": 2010,
    "author": "John Doe",
    "summary": "Lorem ipsum dolor sit amet",
    "publisher": "Dicoding Indonesia",
    "pageCount": 100,
    "readPage": 25,
    "finished": false,
    "reading": false,
    "insertedAt": "2021-03-04T09:11:44.598Z",
    "updatedAt": "2021-03-04T09:11:44.598Z"
}
```

**Server-generated Properties:**
- `id`: Unique identifier (using nanoid)
- `finished`: Boolean based on pageCount === readPage
- `insertedAt`: Timestamp of book creation
- `updatedAt`: Timestamp of last update

**Error Responses:**
1. Missing name property:
   - Status: 400
   ```
   {
       "status": "fail",
       "message": "Gagal menambahkan buku. Mohon isi nama buku"
   }
   ```

2. ReadPage greater than pageCount:
   - Status: 400
   ```
   {
       "status": "fail",
       "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
   }
   ```

**Success Response:**
- Status: 201
```
{
    "status": "success",
    "message": "Buku berhasil ditambahkan",
    "data": {
        "bookId": "1L7ZtDUFeGs7VlEt"
    }
}
```

#### Get All Books (GET /books)
Returns a list of all books with basic information.

**Success Response:**
- Status: 200
```
{
    "status": "success",
    "data": {
        "books": [
            {
                "id": "Qbax5Oy7L8WKf74l",
                "name": "Buku A",
                "publisher": "Dicoding Indonesia"
            }
        ]
    }
}
```

#### Get Book Detail (GET /books/{bookId})
**Error Response:**
- Status: 404
```
{
    "status": "fail",
    "message": "Buku tidak ditemukan"
}
```

**Success Response:**
- Status: 200
```
{
    "status": "success",
    "data": {
        "book": {
            "id": "aWZBUW3JN_VBE-9I",
            "name": "Buku A Revisi",
            "year": 2011,
            "author": "Jane Doe",
            "summary": "Lorem Dolor sit Amet",
            "publisher": "Dicoding",
            "pageCount": 200,
            "readPage": 26,
            "finished": false,
            "reading": false,
            "insertedAt": "2021-03-05T06:14:28.930Z",
            "updatedAt": "2021-03-05T06:14:30.718Z"
        }
    }
}
```

#### Update Book (PUT /books/{bookId})
**Error Responses:**
1. Missing name:
   - Status: 400
   ```
   {
       "status": "fail",
       "message": "Gagal memperbarui buku. Mohon isi nama buku"
   }
   ```

2. Invalid readPage:
   - Status: 400
   ```
   {
       "status": "fail",
       "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
   }
   ```3. Book not found:
   - Status: 404
   ```
   {
       "status": "fail",
       "message": "Gagal memperbarui buku. Id tidak ditemukan"
   }
   ```

**Success Response:**
- Status: 200
```
{
    "status": "success",
    "message": "Buku berhasil diperbarui"
}
```

#### Delete Book (DELETE /books/{bookId})
**Error Response:**
- Status: 404
```
{
    "status": "fail",
    "message": "Buku gagal dihapus. Id tidak ditemukan"
}
```

**Success Response:**
- Status: 200
```
{
    "status": "success",
    "message": "Buku berhasil dihapus"
}
```

