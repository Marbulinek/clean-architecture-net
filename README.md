# .NET Clean Architecture Project

This project is a .NET application built using the Clean Architecture pattern. It is organized into multiple layers to promote separation of concerns, making the codebase modular, testable, and easy to maintain. The project includes RESTful endpoints to support communication with the web client or other applications.

## Project Structure

The solution consists of the following projects:

1. **Domain**:
   - Contains the core business logic and entities. This layer is independent of any other project and does not depend on any external libraries, ensuring high reusability.
   - Defines domain entities, value objects, and interfaces that the `Application` and `Infrastructure` projects use.
   - Ensures the business rules are enforced across the entire application.

2. **Application**:
   - Houses the application logic, including use cases, commands, queries, and validation.
   - Uses **MediatR** for managing requests and responses across the application, allowing for a loosely coupled request handling mechanism.
   - Integrates **FluentValidation** to ensure that all commands and queries meet necessary validation requirements.
   - Contains interfaces for services that are implemented in the `Infrastructure` layer.

3. **Infrastructure**:
   - Implements interfaces defined in the `Application` layer, including data persistence and external service interactions.
   - Contains code for database access, file storage, external APIs, and any other system dependencies.
   - Keeps dependency details out of the core logic to ensure that the `Domain` and `Application` projects remain isolated from infrastructure concerns.

4. **Presentation**:
   - Manages the user-facing components such as UI or API controllers.
   - Uses controllers to define RESTful endpoints for handling client requests.
   - Bridges the `Application` layer to the outside world, handling HTTP requests and responses, and converting input/output as needed.

5. **WebApp**:
   - The main entry point of the application, responsible for configuring and running the application.
   - Registers services, middleware, and dependencies necessary for the application to function.
   - Configures dependency injection to link the various layers and libraries together in a cohesive manner.

## Key Technologies and Libraries

- **MediatR**: Used in the `Application` layer to implement the CQRS pattern, allowing the application to handle commands and queries independently.
- **FluentValidation**: Used in the `Application` layer to validate incoming requests before processing them.
- **Dependency Injection**: Dependency injection is set up in the `WebApp` project to connect all services and interfaces across layers.

## Getting Started

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Marbulinek/clean-architecture-net.git
