# Backend - Employee Management System

Express.js REST API with MongoDB

## Quick Start

```bash
npm install
npm start
```

Server: `http://localhost:4000`

## Setup

**.env file:**
```env
PORT=4000
DB_URL=mongodb://localhost:27017/demobackend
```

## API Routes

**Base URL:** `http://localhost:4000/employee-api`

| Method | Endpoint | Action |
|--------|----------|--------|
| POST | `/employees` | Create |
| GET | `/employees` | Get all |
| PUT | `/employees/:id` | Update |
| DELETE | `/employees/:id` | Delete |

## Create Employee

```bash
curl -X POST http://localhost:4000/employee-api/employees \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John",
    "email": "john@test.com",
    "mobile": 9876543210,
    "designation": "Developer",
    "companyName": "TechCorp"
  }'
```

Response: `{ "message": "Employee created" }`

## Get All

```bash
curl http://localhost:4000/employee-api/employees
```

## Update

```bash
curl -X PUT http://localhost:4000/employee-api/employees/ID \
  -H "Content-Type: application/json" \
  -d '{"name": "Jane"}'
```

## Delete

```bash
curl -X DELETE http://localhost:4000/employee-api/employees/ID
```

## Employee Schema

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| name | String | Yes | - |
| email | String | Yes | Unique |
| mobile | Number | Yes | - |
| designation | String | Yes | - |
| companyName | String | Yes | - |

## File Structure

```
backend/
├── APIs/EmployeeAPI.js      # Routes
├── Models/EmployeeModel.js   # Schema
├── .env                      # Config
├── server.js                 # Main
└── package.json
```

## Tech Stack

- Express 5.2.1
- MongoDB
- Mongoose 9.3.3
- CORS 2.8.6
- dotenv 17.3.1

## Error Responses

**ValidationError (400):** Missing fields or duplicate email
**CastError (400):** Invalid ObjectId
**Not Found (404):** Employee doesn't exist
**Server Error (500):** Database issues

## Troubleshooting

**MongoDB not running?**
```bash
mongod
```

**Port 4000 in use?**
- Change `PORT` in `.env`

**CORS error?**
- Frontend must be `http://localhost:5173`

## Development

API responses include payloads with employee data. Use REST Client extension in VS Code to test with `req.http` file.

### Running

```bash
npm start
# Check terminal for: "DB connection successful"
# Server listening to port 4000...
```
   - Start HTTP server on PORT
   ↓
6. On failure:
   - Log connection error
   - Suggest solutions
```

---

## 🔐 Security Notes

1. **Never commit .env file** - Add to .gitignore
2. **Validate all inputs** - Mongoose schema validates
3. **Use unique indexes** - Email has unique constraint
4. **CORS whitelist** - Only allow trusted origins
5. **Error messages** - Don't expose sensitive info
6. **Environment variables** - Use for sensitive data

---

## 📈 Performance Optimization

1. **Database Indexes:**
   - Email field has unique index
   - _id has auto index

2. **Query Optimization:**
   - find() returns all documents
   - Consider pagination for large datasets

3. **Connection Pooling:**
   - Mongoose manages connection pool
   - Auto handles connection reuse

---

## 🚀 Production Deployment Checklist

- [ ] Use production MongoDB URL
- [ ] Set NODE_ENV=production
- [ ] Configure CORS with production frontend URL
- [ ] Enable logging/monitoring
- [ ] Set proper PORT environment variable
- [ ] Use process manager (PM2)
- [ ] Enable HTTPS/SSL
- [ ] Set up database backups
- [ ] Configure environment variables on server

---

## 📝 API Testing Examples

### Using cURL

```bash
# Get all employees
curl http://localhost:4000/employee-api/employees

# Create employee
curl -X POST http://localhost:4000/employee-api/employees \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John",
    "email": "john@test.com",
    "mobile": 9876543210,
    "designation": "Developer",
    "companyName": "TechCorp"
  }'

# Update employee
curl -X PUT http://localhost:4000/employee-api/employees/507f1f77bcf86cd799439011 \
  -H "Content-Type: application/json" \
  -d '{"name": "John Updated"}'

# Delete employee
curl -X DELETE http://localhost:4000/employee-api/employees/507f1f77bcf86cd799439011
```

### Using Postman

1. Create new collection "Employee API"
2. Add requests for each endpoint
3. Set environment variable: `{{baseUrl}}` = `http://localhost:4000`
4. Use `{{baseUrl}}/employee-api/employees` in requests
5. Save responses for documentation

---

## 📞 Support & Documentation

- **Express Docs**: https://expressjs.com/
- **Mongoose Docs**: https://mongoosejs.com/
- **MongoDB Docs**: https://docs.mongodb.com/
- **CORS Info**: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

---

## 📄 License

ISC

---

## ✅ Backend Checklist

- [x] Express server configured
- [x] MongoDB connection established
- [x] CORS enabled for frontend
- [x] All CRUD operations implemented
- [x] Validation implemented
- [x] Error handling implemented
- [x] Environment variables configured
- [x] API documentation complete
- [x] Database schema defined
- [x] Middleware configured
