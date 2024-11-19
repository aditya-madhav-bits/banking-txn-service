Based on your `TransactionController` class, here’s an updated and enriched README tailored to highlight the key functionalities provided by your service:

---

# Banking Transaction Service  

![Build](https://img.shields.io/badge/Build-Passing-brightgreen.svg) ![License](https://img.shields.io/github/license/aditya-madhav-bits/banking-txn-service)

This project serves as a robust backend service to manage and process banking transactions. Designed with Spring Boot, the service exposes a RESTful API to enable efficient transaction handling and querying.  

## Features ✨
- **Add Transactions**: Easily insert transactions into the system.  
- **Internal Transfers**: Facilitate internal transactions across accounts.  
- **Query Transactions by Account**: Fetch all transactions for a specific account.  
- **Query by Reference**: Retrieve transactions based on a transaction reference ID.  

## Tech Stack 🛠️
- **Framework**: Spring Boot  
- **Language**: Java  
- **Database**: MongoDB (or configurable)  
- **Logging**: SLF4J with Lombok  

## API Endpoints 📡

### Base URL: `/transactions`

#### 1. Add a Transaction  
- **Endpoint**: `POST /transactions`  
- **Request Body**:  
  ```json
  {
    "amount": 500,
    "accountId": "12345",
    "type": "DEPOSIT",
    "timestamp": "2024-11-19T12:00:00Z"
  }
  ```  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "data": {
      "transactionId": "txn_001",
      "message": "Transaction added successfully."
    }
  }
  ```  

#### 2. Make Internal Transactions  
- **Endpoint**: `POST /transactions/internal`  
- **Request Body**:  
  ```json
  [
    {
      "amount": 200,
      "fromAccountId": "12345",
      "toAccountId": "67890",
      "type": "TRANSFER",
      "timestamp": "2024-11-19T12:00:00Z"
    }
  ]
  ```  
- **Query Parameter**: `transactionReference=ref_001`  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "message": "Internal transactions processed successfully."
  }
  ```  

#### 3. Get Transactions by Account  
- **Endpoint**: `GET /transactions`  
- **Query Parameter**: `accountId=12345`  
- **Response**:  
  ```json
  [
    {
      "transactionId": "txn_001",
      "amount": 500,
      "type": "DEPOSIT",
      "timestamp": "2024-11-19T12:00:00Z"
    }
  ]
  ```  

#### 4. Get Transactions by Reference  
- **Endpoint**: `GET /transactions/{referenceId}`  
- **Path Variable**: `{referenceId}` = `ref_001`  
- **Response**:  
  ```json
  [
    {
      "transactionId": "txn_001",
      "amount": 200,
      "fromAccountId": "12345",
      "toAccountId": "67890",
      "type": "TRANSFER",
      "timestamp": "2024-11-19T12:00:00Z"
    }
  ]
  ```  

## Installation 🚀

1. Clone the repository:  
   ```bash
   git clone https://github.com/aditya-madhav-bits/banking-txn-service.git
   cd banking-txn-service
   ```  

2. Configure your application:  
   Update the `application.properties` file:  
   ```properties
   server.port=8080
   spring.data.mongodb.uri=mongodb://localhost:27017/transactions-db
   ```  

3. Build and run the application:  
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```  

4. Access the API:  
   Navigate to `http://localhost:8080/transactions`.  

## Testing 🧪
Run unit tests:  
```bash
mvn test
```  

## Contribution Guidelines 🤝
Contributions are welcome! Please fork this repo, create a feature branch, and submit a pull request.  

---

If you'd like to highlight other aspects, such as `TransactionService` or DTO structure, let me know!
