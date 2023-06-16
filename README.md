
# Login and Signup REST API with security features
# greenstitch assessment

## Tasks:
1. User login and registration with JWT
2. Sign up feature and authentication
3. Data Models and association for Authentication and Authorization
4. Way to use Spring Data JPA to interact with H2 Database







### These are APIs that we need to provide:


The database we will use is H2 by configuring project dependency & datasource.

Repository contains UserRepository & RoleRepository to work with Database, will be imported into Controller.

Controller receives and handles request after it was filtered by OncePerRequestFilter.

– AuthController handles signup/login requests

– TestController has accessing protected resource methods with role based validations.

#### Technology used:

Java 17

Spring Boot 3 (with Spring Security, Spring Web, Spring Data JPA)

jjwt 0.11.5

H2 – embedded database

Maven


### Setup new Spring Boot Login project:

Use Spring web tool or your development tool ( Intellij) to create a Spring Boot project.
Configure Spring Datasource, JPA, App properties
1. Create the models
Define these models.
In models package, create 3 files:
ERole enum in ERole.java.
Role model in Role.java
User model in User.java.

2. Implement Repositories
Each model above needs a repository for persisting and accessing data. In repository package, create 2 repositories.

UserRepository
RoleRepository

3. Configure Spring Security
Without WebSecurityConfigurerAdapter
In security package, create WebSecurityConfig class.

5. Implement UserDetails & UserDetailsService 
If the authentication process is successful, we can get User’s information such as username, password, authorities from an Authentication object.

6. Filter the Requests
Define a filter that executes once per request. So we create AuthTokenFilter class that extends OncePerRequestFilter and override doFilterInternal() method.

7. Create JWT Utility class
This class has 3 main funtions:

getJwtFromCookies: get JWT from Cookies by Cookie name
generateJwtCookie: generate a Cookie containing JWT from username, date, expiration, secret
getCleanJwtCookie: return Cookie with null value (used for clean Cookie)
getUserNameFromJwtToken: get username from JWT
validateJwtToken: validate a JWT with a secret

8. Define payloads for Authentication Controller
create AuthEntryPointJwt class that implements AuthenticationEntryPoint interface. Then we override the commence() method.

9. Create Spring Rest Controllers

10. Run & Check
Run Spring Boot application with command: mvn spring-boot:run

Let’s check H2 database with url: http://localhost:8080/h2-ui:

Click on Connect button, tables that we define in models package will be automatically generated in Database.

Register some users with /signup API:

admin with ROLE_ADMIN
mod with ROLE_MODERATOR and ROLE_USER
green with ROLE_USER

Check users and user_roles tables
### The project should be running for the given tasks.
