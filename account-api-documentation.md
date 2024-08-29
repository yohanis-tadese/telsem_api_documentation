Here’s a comprehensive Postman API documentation based on the provided code. This will help you test each endpoint thoroughly:

---

## **API Documentation**

### **1. Create Account**

**Endpoint**: `POST /api/create`

**Description**: Registers a new user and sends an email verification PIN if the user does not already exist.

**Request Body**:

```json
{
  "phone_number": "string",
  "email_address": "string",
  "password": "string",
  "first_name": "string",
  "last_name": "string",
  "gender": "string",
  "dob": "YYYY-MM-DD"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "message": "mail sent"
  }
  ```
- **201 Conflict**:
  ```json
  {
    "success": false,
    "message": "User already exist with similar email/phone number!"
  }
  ```

---

### **2. Verify Account**

**Endpoint**: `POST /api/verify`

**Description**: Verifies the email address using a PIN and registers the user.

**Request Body**:

```json
{
  "pin": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "message": "Registered successfully!"
  }
  ```
- **200 OK** (Invalid PIN):
  ```json
  {
    "status": false,
    "message": "Invalid pin detected"
  }
  ```

---

### **3. Login**

**Endpoint**: `POST /api/login`

**Description**: Logs in a user with email or phone number and password.

**Request Body**:

```json
{
  "phone_number": "string",
  "email_address": "string",
  "password": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "success": true,
    "message": "Login successful",
    "token": "string",
    "data": {
      "id": "number",
      "email": "string"
    }
  }
  ```
- **401 Unauthorized**:
  ```json
  {
    "success": false,
    "message": "Account not found"
  }
  ```
- **401 Unauthorized** (Wrong Password):
  ```json
  {
    "success": false,
    "message": "Wrong password"
  }
  ```

---

### **4. Forget Password**

**Endpoint**: `POST /api/forget-password`

**Description**: Initiates a password reset by sending a PIN to the user's email.

**Request Body**:

```json
{
  "email_address": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "message": "mail sent"
  }
  ```
- **401 Unauthorized**:
  ```json
  {
    "success": false,
    "message": "Account not found"
  }
  ```

---

### **5. Verify Password Reset**

**Endpoint**: `POST /api/verify-password-reset`

**Description**: Verifies the password reset PIN.

**Request Body**:

```json
{
  "pin": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "email_address": "string",
    "message": "Password reset pin verification is successful"
  }
  ```
- **200 OK** (Invalid or Expired PIN):
  ```json
  {
    "status": false,
    "message": "invalid pin / expired pin"
  }
  ```

---

### **6. Reset Password**

**Endpoint**: `POST /api/reset-password`

**Description**: Resets the password for a user using the email address.

**Request Body**:

```json
{
  "email_address": "string",
  "new_password": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "message": "Password reset is successful"
  }
  ```
- **401 Unauthorized**:
  ```json
  {
    "success": false,
    "message": "Account not found"
  }
  ```

---

### **7. Change Password**

**Endpoint**: `POST /api/change-password`

**Description**: Changes the user's password with the old and new passwords.

**Request Body**:

```json
{
  "id": "number",
  "old_password": "string",
  "new_password": "string"
}
```

**Responses**:

- **200 OK**:
  ```json
  {
    "status": true,
    "message": "Password updated successfully! Please login with your new password"
  }
  ```
- **200 OK** (Wrong Old Password):
  ```json
  {
    "status": false,
    "message": "Wrong old password!"
  }
  ```
- **200 OK** (Account Not Found):
  ```json
  {
    "status": false,
    "message": "We couldn't find this account. please try again"
  }
  ```
- **200 OK** (Invalid Password Detected):
  ```json
  {
    "status": false,
    "message": "Invalid password detected!"
  }
  ```

---

This documentation should help you test and understand each endpoint in Postman. If you need more details or have specific scenarios to cover, feel free to ask!
