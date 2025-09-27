# Cookie Session Auth Example

This repository demonstrates user authentication using Express, MongoDB and cookies.

## Setup

1. **Install dependencies:**

   ```sh
   npm install
   ```

2. **Start MongoDB:**  
   Make sure MongoDB is running locally on port 27017.

3. **Start the server:**

   ```sh
   node app.js
   ```

   The server runs at [http://localhost:3000](http://localhost:3000).

## API Endpoints

All endpoints are prefixed with `/auth`.

### 1. Register

- **URL:** `POST /auth/register`
- **Body (JSON):**
  ```json
  {
    "username": "your_username",
    "password": "your_password"
  }
  ```
- **Response:**  
  `{ "message": "User registered successfully!" }`

### 2. Login

- **URL:** `POST /auth/login`
- **Body (JSON):**
  ```json
  {
    "username": "your_username",
    "password": "your_password"
  }
  ```
- **Response:**  
  `{ "message": "Login successful!" }`  
  A session cookie (`connect.sid`) will be set.

### 3. Profile

- **URL:** `GET /auth/profile`
- **Headers:**  
  The request must include the session cookie from login.
- **Response:**  
  User info (without password).

### 4. Logout

- **URL:** `GET /auth/logout`
- **Headers:**  
  The request must include the session cookie from login.
- **Response:**  
  `{ "message": "Logout successful!" }`

## Testing with Postman

1. **Register a user:**  
   - Method: `POST`  
   - URL: `http://localhost:3000/auth/register`  
   - Body: Select `raw` and `JSON`, enter username and password.

2. **Login:**  
   - Method: `POST`  
   - URL: `http://localhost:3000/auth/login`  
   - Body: Same as above.
   - **Important:**  
     - After login, Postman will save the session cookie automatically if "Enable cookies" is on.

3. **Access profile:**  
   - Method: `GET`  
   - URL: `http://localhost:3000/auth/profile`  
   - The session cookie from login will be sent automatically.

4. **Logout:**  
   - Method: `GET`  
   - URL: `http://localhost:3000/auth/logout`  
   - The session cookie from login will be sent automatically.

## Notes

- If you get `Unauthorized` on `/auth/profile`, make sure you are logged in and sending the session cookie.
- The session cookie is named `connect.sid`.
- All of results put in `public/results`