# 1. Registration and Login Features

## 1.1 Overview

| Feature Module          | Endpoint                   | Method   | Description                     |
|-------------------------|----------------------------|----------|---------------------------------|
| User Login              | `/login`                   | POST     | Email and password login        |
| User Registration       | `/register`                | POST     | Create a new user               |
| Send Verification Code  | `/password/resetCode`      | POST     | Send password reset code        |
| Update Password         | `/password/update`         | POST     | Reset password via code         |

---

## 1.2 User Login

**URL:** `/login`  
**Method:** POST  

### Request Parameters  
```json
{
  "email": "user@example.com",
  "password": "yourPassword123"
}
```

### Response Examples  
**Success:**  
```json
{
  "code": 1,
  "message": "Login Successful",
  "data": {
    "id": 123,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9"
  }
}
```

**Error:**  
```json
{
  "code": 0,
  "message": "Email or password is incorrect"
}
```

---

## 1.3 User Registration

**URL:** `/register`  
**Method:** POST  

### Request Parameters  
```json
{
  "email": "newuser@example.com",
  "password": "SecurePass123!",
  "invitedCode": "REF12345"
}
```

### Parameter Requirements  
- Password: 8-20 characters, must include uppercase, lowercase, and numbers  
- Invitation Code: 6-12 alphanumeric characters (field name: `invitedCode`)  

### Response Examples  
**Success:**  
```json
{
  "code": 1,
  "message": "Registration Successful",
  "data": {
    "id": 124,
    "email": "newuser@example.com"
  }
}
```

**Error:**  
```json
{
  "code": 0,
  "message": "Invitation code does not exist"
}
```

---

## 1.4 Send Reset Verification Code

**URL:** `/password/resetCode`  
**Method:** POST  

### Request Parameters  
```json
{
  "email": "user@example.com"
}
```

### Response Example  
```json
{
  "code": 1,
  "message": "Verification code sent"
}
```

---

## 1.5 Update Password

**URL:** `/password/update`  
**Method:** POST  

### Request Parameters  
```json
{
  "email": "user@example.com",
  "verificationCode": "A1B2C3",
  "newPassword": "NewPass123!"
}
```

### Response Examples  
**Success:**  
```json
{
  "code": 1,
  "message": "Password updated successfully"
}
```

**Error:**  
```json
{
  "code": 0,
  "message": "Invalid or expired verification code"
}
```

