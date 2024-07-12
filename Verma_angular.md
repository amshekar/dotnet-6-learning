# angular-intrview-learning

I.  . Angular architecture 

### 1. Modules
- *What*: Logical containers for a cohesive block of code dedicated to an application domain, a workflow, or a set of capabilities.
- *Why*: To organize an application into cohesive blocks of functionality.
- *How*: Use NgModule to define a module. Each Angular application has at least one module, the root module, which is typically named `AppModule`.

### 2. Components
- *What*: The basic building blocks of an Angular application. Each component consists of an HTML template, a CSS stylesheet, and a TypeScript class.
- *Why*: To define views, which are sets of screen elements that Angular can choose among and modify according to your program logic and data.
- *How*: Use the @Component decorator to define a component. Each component is associated with a template that defines a view.

### 3. Templates
- *What*: HTML views that define how the component's data is displayed.
- *Why*: To bind data from the component to the view.
- *How*: Use Angular's template syntax, including directives like *ngIf and *ngFor, to bind data and manage the DOM.

### 4. Services and Dependency Injection
- *What*: Classes that handle business logic and data retrieval, which can be injected into components.
- *Why*: To separate concerns and promote code reusability.
- *How*: Use the @Injectable decorator to define a service and Angular's dependency injection system to provide and inject services.

### 5. Routing
- *What*: A mechanism to navigate between different views or components.
- *Why*: To create a single-page application with multiple views.
- *How*: Use the RouterModule to define routes and the Router service to navigate between them.

### 6. Directives
- *What*: Classes that add behavior to elements in your Angular applications.
- *Why*: To extend the HTML vocabulary and create reusable components.
- *How*: Use the @Directive decorator to define a directive. There are structural directives (like *ngIf) and attribute directives (like ngClass).

### 7. Pipes
- *What*: Classes that transform data before displaying it in a view.
- *Why*: To format data in the template.
- *How*: Use the @Pipe decorator to define a pipe and use it in templates with the pipe operator (|).

II.	. Error Handling

### 1. RxJS catchError Operator
- *What*: A function to catch and handle errors in Observable streams.
- *Why*: To manage errors in data streams gracefully without crashing the app.
- *How*: Use it within the pipe() function to catch errors and return a fallback value or handle the error.

### 2. Global Error Handler
- *What*: A custom class that catches unhandled exceptions across the app.
- *Why*: To log errors or show user-friendly messages for unexpected issues.
- *How*: Implement the ErrorHandler interface and override the handleError method.

### 3. HTTP Interceptors
- *What*: A service that intercepts HTTP requests and responses.
- *Why*: To handle HTTP errors globally, ensuring consistent error management for all API calls.
- *How*: Implement the HttpInterceptor interface and use the intercept method to catch errors.

### 4. Reactive Forms Validation
- *What*: Validators for form inputs.
- *Why*: To ensure user inputs are valid and provide immediate feedback.
- *How*: Use built-in or custom validators in form controls.

### 5. Component-Level Error Handling
- *What*: Error handling specific to a component.
- *Why*: To manage errors that occur within a particular component.
- *How*: Use lifecycle hooks like ngOnDestroy to detect and handle errors.

III.  . Log Explanation

### 1. Console Logging
- *What*: Using console.log() to output messages to the browser console.
- *Why*: To quickly debug and understand what's happening in your application.
- *How*: Insert console.log() statements in your code to log variables, function calls, or any other information.

### 2. Custom Logging Service
- *What*: A dedicated Angular service for logging.
- *Why*: To centralize logging logic and make it easier to manage and extend.
- *How*: Create an Angular service with methods like log(), error(), warn(), and info(). Inject this service wherever logging is needed.

### 3. Logging Levels
- *What*: Different levels of logging such as info, warn, error, and debug.
- *Why*: To categorize logs and control the verbosity of logging output.
- *How*: Implement methods in your logging service to handle different log levels and use them appropriately.

### 4. Environment-Specific Logging
- *What*: Adjusting logging behavior based on the environment (development, production).
- *Why*: To avoid exposing sensitive information in production and reduce log noise.
- *How*: Use Angular's environment configuration to enable or disable logging based on the environment.

### 5. External Logging Services
- *What*: Integrating with external logging services like Sentry or Loggly.
- *Why*: To collect and analyze logs from different environments and devices.
- *How*: Use the service's SDK to send logs from your Angular application to the external service.

IV.  . Unit testing 
### 1. What is Unit Testing?
- *What*: Testing individual parts (units) of an application in isolation.
- *Why*: To ensure each part of the application works correctly on its own.
- *How*: Write tests for components, services, and other classes using a testing framework like Jasmine and run them with a test runner like Karma.

### 2. Jasmine Testing Framework
- *What*: A behavior-driven development framework for testing JavaScript code.
- *Why*: To write readable and maintainable tests.
- *How*: Use Jasmine's functions like describe(), it(), expect(), and beforeEach() to structure and write your tests.

### 3. Karma Test Runner
- *What*: A tool that runs your tests in different browsers.
- *Why*: To automate the testing process and ensure your code works across various environments.
- *How*: Configure Karma in your Angular project and run tests using the ng test command.

### 4. TestBed Utility
- *What*: A utility provided by Angular to configure and initialize the environment for unit tests.
- *Why*: To create and configure components and services for testing.
- *How*: Use TestBed.configureTestingModule() to set up the testing environment and TestBed.createComponent() to create instances of components.

### 5. Mocking Dependencies
- *What*: Replacing real dependencies with mock objects.
- *Why*: To isolate the unit being tested and avoid side effects from real dependencies.
- *How*: Use Jasmine's spyOn() function to create mock methods and services.


V.  . End to end workflow of authentication

### 1. User Login
- *What*: The process where a user enters their credentials to access the application.
- *Why*: To verify the user's identity and grant access to protected resources.
- *How*: Create a login form where users input their username and password. Send these credentials to the backend API for verification.

### 2. Authentication Service
- *What*: A service that handles authentication logic.
- *Why*: To manage login, logout, and token storage centrally.
- *How*: Implement an Angular service with methods for logging in, logging out, and storing/retrieving tokens.

### 3. Token Storage
- *What*: Storing the authentication token received from the backend.
- *Why*: To maintain the user's authenticated state across different parts of the application.
- *How*: Store the token in local storage or session storage.

### 4. HTTP Interceptor
- *What*: A service that intercepts HTTP requests and adds the authentication token to the headers.
- *Why*: To ensure all API requests include the token for authentication.
- *How*: Implement the HttpInterceptor interface and modify the request headers to include the token if available.

### 5. Route Guards
- *What*: Guards that protect routes from unauthorized access.
- *Why*: To prevent unauthenticated users from accessing protected routes.
- *How*: Implement CanActivate guard to check if the user is authenticated before allowing access to a route.

### 6. User Logout
- *What*: The process where a user logs out of the application.
- *Why*: To end the user's session and clear authentication data.
- *How*: Implement a logout method in the authentication service to clear the token from storage and redirect the user to the login page.
