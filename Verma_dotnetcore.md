# dotnetcore-intrview-learning

## I.  . dotnetcore architecture

### 1. Middleware
- *What*: Components that handle HTTP requests and responses.
- *Why*: To process requests through a pipeline, allowing for modular and reusable processing logic.
- *How*: Configure middleware in the Startup.cs file using methods like app.UseRouting(), app.UseAuthentication(), and `app.UseEndpoints()`.

### 2. Dependency Injection (DI)
- *What*: A design pattern to manage dependencies between classes.
- *Why*: To promote loose coupling and enhance testability.
- *How*: Register services in the Startup.cs file using services.AddTransient(), services.AddScoped(), or services.AddSingleton(), and inject them via constructors.

### 3. Configuration
- *What*: A system to manage application settings.
- *Why*: To separate configuration from code and support different environments.
- *How*: Use appsettings.json files and environment variables, and access them via the IConfiguration interface.

### 4. Logging
- *What*: A system to record application events.
- *Why*: To diagnose issues and monitor application behavior.
- *How*: Configure logging providers in Program.cs using builder.Logging.AddConsole(), builder.Logging.AddDebug(), etc.

### 5. MVC (Model-View-Controller)
- *What*: A design pattern to separate concerns in web applications.
- *Why*: To organize code into models (data), views (UI), and controllers (logic).
- *How*: Use Controller classes for logic, View files for UI, and Model classes for data. Configure routes in Startup.cs using `app.UseEndpoints(endpoints => { endpoints.MapControllerRoute(...); })`.

### 6. Entity Framework Core (EF Core)
- *What*: An Object-Relational Mapper (ORM) for database access.
- *Why*: To interact with databases using .NET objects.
- *How*: Define DbContext and DbSet classes, configure the database connection in Startup.cs, and use LINQ to query the database.

### 7. Authentication and Authorization
- *What*: Systems to verify user identity and control access to resources.
- *Why*: To secure the application and protect sensitive data.
- *How*: Use services.AddAuthentication() and services.AddAuthorization() in Startup.cs, and apply [Authorize] attributes to controllers or actions.

##  II.	. Error Handling

### 1. Developer Exception Page
- *What*: A page that shows detailed error information during development.
- *Why*: To help developers debug issues by providing detailed error information.
- *How*: Enable it in the Startup.cs file using app.UseDeveloperExceptionPage() when in the Development environment.

### 2. Exception Handler Middleware
- *What*: Middleware to handle exceptions and show a custom error page.
- *Why*: To provide a user-friendly error page in production and log errors.
- *How*: Use app.UseExceptionHandler("/Error") in the Startup.cs file to redirect to a custom error page.

### 3. Logging
- *What*: A system to log errors and other information.
- *Why*: To keep track of errors and diagnose issues.
- *How*: Use built-in logging providers like Serilog or NLog to log errors in various formats.

### 4. Model Validation
- *What*: Validation of user inputs in models.
- *Why*: To ensure data integrity and provide immediate feedback to users.
- *How*: Use data annotations and custom validation attributes in your models.

### 5. Global Exception Handling Middleware
- *What*: Middleware to catch and handle all unhandled exceptions globally.
- *Why*: To ensure consistent error handling across the application.
- *How*: Create custom middleware to catch exceptions and return appropriate HTTP responses.

##  II.  . Log Explanation

### 1. Console Logging
- *What*: Logging messages to the console.
- *Why*: To quickly see log output during development.
- *How*: Configure it in Program.cs using `builder.Logging.AddConsole()`.

### 2. Logging Providers
- *What*: Services that store or display logs, like Console, Debug, or third-party providers.
- *Why*: To manage logs in different environments and formats.
- *How*: Add providers in Program.cs using `builder.Logging.AddProvider(new CustomProvider())`.

### 3. Logging Levels
- *What*: Categories of log severity (e.g., Debug, Info, Warn, Error).
- *Why*: To filter and manage logs based on their importance.
- *How*: Use ILogger methods like LogDebug(), LogInformation(), LogWarning(), and `LogError()`.

### 4. Dependency Injection
- *What*: Injecting the ILogger service into classes.
- *Why*: To enable logging in any part of the application.
- *How*: Use constructor injection to get an ILogger<T> instance.

### 5. External Logging Services
- *What*: Integrating with services like Serilog or NLog.
- *Why*: To enhance logging capabilities and store logs externally.
- *How*: Install the necessary NuGet packages and configure them in `Program.cs`.

##  IV.  . Unit testing 

### 1. What is Unit Testing?
- *What*: Testing individual parts (units) of an application in isolation.
- *Why*: To ensure each part of the application works correctly on its own.
- *How*: Write tests for controllers, services, and other classes using a testing framework like xUnit or NUnit.

### 2. xUnit Testing Framework
- *What*: A popular testing framework for .NET applications.
- *Why*: To write readable and maintainable tests.
- *How*: Use xUnit's attributes like [Fact] and [Theory] to define test methods.

### 3. Mocking Dependencies
- *What*: Replacing real dependencies with mock objects.
- *Why*: To isolate the unit being tested and avoid side effects from real dependencies.
- *How*: Use libraries like Moq to create mock objects and set up expected behaviors.

### 4. Test Server and Client
- *What*: Tools to simulate HTTP requests and responses.
- *Why*: To test API endpoints without needing a running server.
- *How*: Use TestServer and HttpClient from the Microsoft.AspNetCore.TestHost namespace to create and send requests.

### 5. Arrange, Act, Assert Pattern
- *What*: A common pattern for structuring tests.
- *Why*: To make tests clear and consistent.
- *How*: 
  - *Arrange*: Set up the test data and environment.
  - *Act*: Execute the method being tested.
  - *Assert*: Verify the result is as expected.


##  V.  . End to end workflow of authentication

### 1. User Login
- *What*: The process where a user enters their credentials to access the API.
- *Why*: To verify the user's identity and grant access to protected resources.
- *How*: Create a login endpoint that accepts user credentials and verifies them against stored data. If valid, generate a JSON Web Token (JWT) and return it to the user.

### 2. Authentication Middleware
- *What*: Middleware that handles authentication logic.
- *Why*: To manage the authentication process centrally.
- *How*: Use the AddAuthentication and AddJwtBearer methods in Startup.cs to configure JWT authentication.

### 3. Token Storage
- *What*: Storing the JWT received from the API.
- *Why*: To maintain the user's authenticated state across requests.
- *How*: The client (e.g., Angular app) stores the token in local storage or session storage.

### 4. HTTP Interceptor
- *What*: A service that intercepts HTTP requests and adds the JWT to the headers.
- *Why*: To ensure all API requests include the token for authentication.
- *How*: Implement an HTTP client handler or middleware to add the token to the Authorization header of each request.

### 5. Authorization
- *What*: Checking if the authenticated user has permission to access specific resources.
- *Why*: To protect resources from unauthorized access.
- *How*: Use the [Authorize] attribute on controllers or actions to enforce authorization policies.

### 6. User Logout
- *What*: The process where a user logs out of the API.
- *Why*: To end the user's session and invalidate the token.
- *How*: The client can simply delete the token from storage. Optionally, implement token invalidation on the server side if using refresh tokens.
