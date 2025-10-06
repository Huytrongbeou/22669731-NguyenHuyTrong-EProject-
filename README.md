# E-Commerce Microservices Project

A distributed e-commerce system built with Node.js microservices architecture, featuring user authentication, product management, and order processing with message queuing.
## 📸 Screenshots & Demonstrations

<!-- Add your screenshots here -->

### User Registration
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/23cec98c-8332-46e5-90e8-74674032f6ae" />
### -> Check in database:
<img width="1909" height="1064" alt="image" src="https://github.com/user-attachments/assets/cb1ab3ac-01b3-417b-bcf9-ed9e6a5d77f6" />


### User Login and create token for user
<img width="1917" height="1077" alt="image" src="https://github.com/user-attachments/assets/c83ac83a-ce21-4a5d-9314-1b4892ce28e6" />


### User dashboard after login and authorized with token
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/768a92ec-9c2c-4409-b136-4e615b37194a" />


### Product Creation
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ac4e55c9-736b-48da-89d3-600399346b25" />
### -> Check in database:
<img width="1902" height="1058" alt="image" src="https://github.com/user-attachments/assets/69043687-5ad3-4939-b90f-0657c274025f" />

### Product Catalog with GET method
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/095583cb-4fe8-4056-b768-320edab04fe8" />


### Order Completion
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e00290b7-0db0-4f1f-99be-a083a1047ab8" />

### RabbitMQ Message Queues
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5d5760fa-39f5-4b31-9288-59199284df36" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/921471f1-efa2-44e1-829a-dff030489926" />



## 🏗️ Architecture Overview

This project implements a microservices architecture with the following components:

- **API Gateway** (Port 3003) - Single entry point for all client requests
- **Authentication Service** (Port 3000) - User registration, login, and JWT token management
- **Product Service** (Port 3001) - Product CRUD operations and order initiation
- **Order Service** (Port 3002) - Order processing and persistence
- **Message Broker** (RabbitMQ) - Asynchronous communication between services
- **Database** (MongoDB) - Separate databases for each service

## 📋 Features

### User Authentication
- User registration and login
- JWT-based authentication
- Protected routes and middleware
- Token-based authorization across services

### Product Management
- Create, read, update, delete products
- Product catalog browsing
- Product search and filtering

### Order Processing
- Shopping cart functionality
- Order creation and processing
- Asynchronous order fulfillment
- Order status tracking
- Message queue integration for reliable processing

### Microservices Communication
- HTTP-based synchronous communication via API Gateway
- Asynchronous messaging with RabbitMQ
- Service-to-service authentication
- Error handling and resilience

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Message Broker**: RabbitMQ (AMQP)
- **Authentication**: JWT (JSON Web Tokens)
- **Testing**: Mocha, Chai
- **API Gateway**: HTTP Proxy

## 📁 Project Structure

```
EProject-Phase-1/
├── api-gateway/
│   ├── index.js              # API Gateway entry point
│   └── package.json
├── auth/
│   ├── src/
│   │   ├── app.js           # Auth service application
│   │   ├── config/          # Configuration files
│   │   ├── controllers/     # Auth controllers
│   │   ├── middlewares/     # Auth middleware
│   │   ├── models/          # User models
│   │   ├── repositories/    # Data access layer
│   │   ├── services/        # Business logic
│   │   └── test/           # Auth service tests
│   ├── index.js
│   ├── package.json
│   └── .env                # Auth environment variables
├── product/
│   ├── src/
│   │   ├── app.js          # Product service application
│   │   ├── controllers/    # Product controllers
│   │   ├── models/         # Product models
│   │   ├── repositories/   # Data access layer
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   ├── utils/          # Utilities and middleware
│   │   └── test/          # Product service tests
│   ├── index.js
│   ├── package.json
│   └── .env               # Product environment variables
├── order/
│   ├── src/
│   │   ├── app.js         # Order service application
│   │   ├── models/        # Order models
│   │   ├── utils/         # Message broker utilities
│   │   └── config.js      # Order service configuration
│   ├── index.js
│   ├── package.json
│   └── .env              # Order environment variables
├── utils/
│   └── isAuthenticated.js # Shared authentication utility
├── package.json          # Root package.json
└── README.md            # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- RabbitMQ (v3.8 or higher)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd EProject-Phase-1
   ```

2. **Install root dependencies**
   ```bash
   npm install
   ```

3. **Install service dependencies**
   ```bash
   # Install API Gateway dependencies
   cd api-gateway && npm install && cd ..
   
   # Install Auth service dependencies
   cd auth && npm install && cd ..
   
   # Install Product service dependencies
   cd product && npm install && cd ..
   
   # Install Order service dependencies
   cd order && npm install && cd ..
   ```

4. **Setup environment variables**
   
   Create `.env` files in each service directory:
   
   **auth/.env**
   ```env
   MONGODB_AUTH_URI=mongodb://localhost:27017/auth_service
   JWT_SECRET=your_super_secret_jwt_key_for_auth_service_2024
   ```
   
   **product/.env**
   ```env
   MONGODB_PRODUCT_URI=mongodb://localhost:27017/product_service
   JWT_SECRET=your_super_secret_jwt_key_for_auth_service_2024
   ```
   
   **order/.env**
   ```env
   MONGODB_ORDER_URI=mongodb://localhost:27017/order_service
   JWT_SECRET=your_super_secret_jwt_key_for_auth_service_2024
   ```

### Running the Application

1. **Start MongoDB**
   ```bash
   # Make sure MongoDB is running on localhost:27017
   mongod
   ```

2. **Start RabbitMQ**
   ```bash
   # Make sure RabbitMQ is running on localhost:5672
   rabbitmq-server
   ```

3. **Start all microservices** (in separate terminals)
   
   ```bash
   # Terminal 1: Auth Service
   cd auth && node index.js
   
   # Terminal 2: Product Service
   cd product && node index.js
   
   # Terminal 3: Order Service
   cd order && node index.js
   
   # Terminal 4: API Gateway
   cd api-gateway && node index.js
   ```

4. **Verify services are running**
   - API Gateway: http://localhost:3003
   - Auth Service: http://localhost:3000
   - Product Service: http://localhost:3001
   - Order Service: http://localhost:3002

## 📖 API Documentation

### Base URL
All API requests should be made through the API Gateway:
```
http://localhost:3003
```

### Authentication Endpoints

#### Register User
```http
POST /auth/register
Content-Type: application/json

{
  "username": "testuser",
  "password": "testpass123",
  "email": "test@example.com"
}
```

#### Login User
```http
POST /auth/login
Content-Type: application/json

{
  "username": "testuser",
  "password": "testpass123"
}

Response:
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

#### Access Protected Dashboard
```http
GET /auth/dashboard
Authorization: Bearer <jwt_token>
```

### Product Endpoints

#### Get All Products
```http
GET /products/api/products
Authorization: Bearer <jwt_token>
```

#### Create Product
```http
POST /products/api/products
Authorization: Bearer <jwt_token>
Content-Type: application/json

{
  "name": "Product Name",
  "price": 29.99,
  "description": "Product description"
}
```

#### Create Order (Buy Products)
```http
POST /products/api/products/buy
Authorization: Bearer <jwt_token>
Content-Type: application/json

{
  "ids": ["product_id_1", "product_id_2"]
}
```

## 🔄 Message Flow

The system implements the following message flow for order processing:

1. **Client** → **API Gateway** → **Product Service** (initiate purchase)
2. **Product Service** → **Order Queue** → **Order Service** (process order)
3. **Order Service** saves order to database
4. **Order Service** → **Products Queue** → **Product Service** (order completion)
5. **Product Service** updates order status and returns response to client



## 🧪 Testing

### Running Tests

```bash
# Run all tests
npm test

# Run specific service tests
cd auth && npm test
cd product && npm test
```

### Manual Testing with Postman

1. Import the Postman collection (if available)
2. Set up environment variables for base URL and tokens
3. Test the complete workflow:
   - Register a user
   - Login and get JWT token
   - Create products
   - Place orders
   - Verify order processing

## Troubleshooting

### Common Issues

1. **JWT Token Issues**
   - Ensure all services use the same JWT_SECRET
   - Get fresh tokens after service restarts
   - Check token expiration

2. **Service Communication**
   - Verify all services are running on correct ports
   - Check API Gateway routing configuration
   - Ensure MongoDB and RabbitMQ are accessible

3. **Database Connection**
   - Verify MongoDB is running
   - Check database connection strings
   - Ensure proper database permissions

4. **Message Queue Issues**
   - Verify RabbitMQ is running
   - Check queue connections in service logs
   - Monitor message processing

## 🔮 Future Enhancements

- [ ] Docker containerization
- [ ] Service discovery and load balancing
- [ ] API rate limiting
- [ ] Logging and monitoring
- [ ] Unit and integration test coverage
- [ ] CI/CD pipeline
- [ ] Frontend application
- [ ] Payment processing integration
- [ ] Inventory management
- [ ] User profile management

## 👥 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request


**Note**: This is a learning project demonstrating microservices architecture patterns. For production use, additional security, monitoring, and scalability considerations should be implemented.
