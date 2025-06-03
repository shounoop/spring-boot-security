# Spring Boot Security

A sample project demonstrating how to implement security in a Spring Boot application. This project showcases best practices for authentication, authorization, and secure configuration using Spring Security.

## Features
- User authentication and authorization
- Role-based access control
- Secure password storage
- JWT (JSON Web Token) support
- Custom login and error pages
- RESTful API security

## Getting Started

### Prerequisites
- Java 17 or higher
- Maven 3.6+

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/shounoop/spring-boot-security.git
   cd spring-boot-security
   ```
2. Build the project:
   ```bash
   ./mvnw clean install
   ```
3. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```

## Usage
- Access the application at `http://localhost:8080` after starting.
- Default credentials (if any) can be found in the application properties or configured in the database.
- Use the API endpoints as documented in the code or Swagger (if available).

## Security Schema
![Spring boot security schema](https://github.com/shounoop/spring-boot-security/assets/85869774/588e88c1-67b6-40df-8ea5-437455e4db8d)

## Flow: Spring Boot Security

1. **User Request**: A user tries to access a protected resource or endpoint.
2. **Authentication**:  
   - If not authenticated, Spring Security intercepts the request and redirects to the login page or returns a 401/403 for APIs.
   - User submits credentials (username/password or token).
3. **Credential Validation**:  
   - Spring Security validates credentials against the configured user store (in-memory, database, LDAP, etc.).
   - If valid, a session or JWT token is created.
4. **Authorization**:  
   - Spring Security checks user roles/authorities for the requested resource.
   - Access is granted or denied based on permissions.
5. **Access Granted/Denied**:  
   - If authorized, the user accesses the resource.
   - If not, an error or access denied page is shown.
6. **Logout**:  
   - User can log out, which invalidates the session or token.

## Flow: Spring Boot Security with JWT

1. **User Login Request**  
   - User sends credentials (username/password) to the authentication endpoint (e.g., `/login` or `/api/authenticate`).

2. **Authentication Manager & UserDetailsService**  
   - The authentication endpoint uses the `AuthenticationManager` to authenticate the user.
   - `AuthenticationManager` delegates to `UserDetailsService` to load user details from the database or another source.

3. **JWT Token Generation**  
   - If authentication is successful, a JWT token is generated and returned to the user.

4. **Subsequent Requests with JWT**  
   - The client includes the JWT token in the `Authorization` header (`Bearer <token>`) for subsequent requests.

5. **JWT Authentication Filter (`jwtAuthFilter`)**  
   - For each request, `jwtAuthFilter` intercepts and extracts the JWT token from the header.
   - The filter validates the token (signature, expiration, etc.).
   - If valid, it sets the authentication in the security context.

6. **Authorization**  
   - Spring Security checks user roles/authorities for the requested resource.
   - Access is granted or denied based on permissions.

7. **Access Granted/Denied**  
   - If authorized, the user accesses the resource.
   - If not, an error or access denied response is returned.

## Contributing
Contributions are welcome! Please open issues or submit pull requests for improvements and bug fixes.
