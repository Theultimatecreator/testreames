# Mobile SmartPOS ERA KKM

This repository contains the source code for the Mobile SmartPOS ERA KKM application, a modern Android application designed for Point of Sale (POS) operations, likely integrating with fiscal registers (KKM). The project is built with a modular architecture to ensure scalability, maintainability, and clear separation of concerns.

## Features

This application is composed of several distinct feature modules, each handling a specific part of the POS functionality:

*   **Account:** Manages user accounts and related settings.
*   **APay:** Handles specific payment functionalities, possibly related to a custom payment system.
*   **Cash Operations:** Manages cash-in and cash-out transactions.
*   **Cash Operations Management:** Provides tools for managing and reporting on cash operations.
*   **Credit Advance:** Functionality related to credit advances or loans.
*   **Fiscal:** Integrates with fiscal registers (KKM) for legal compliance and transaction recording.
*   **Home:** The main dashboard or landing screen of the application.
*   **Login:** Handles user authentication and session management.
*   **Order:** Manages order creation, modification, and processing.
*   **Payment:** Core payment processing functionalities, supporting various payment         
methods including card payments, QR code payments,  
 and potentially integrations with specific local    
 payment systems. Details on supported payment       
methods (e.g., Humo, Uzcard, or other apps) would   
be found within this module's implementation.   
*   **Profile:** Allows users to view and edit their profile information.
*   **Receipt:** Generates and manages transaction receipts.
*   **Refund:** Handles the process of refunding transactions.

## Technologies Used

*   **Kotlin:** The primary programming language for Android development, known for its conciseness and safety.
*   **Android Jetpack Compose:** Google's modern toolkit for building native Android UI. It simplifies UI development with a declarative approach.
*   **Gradle Kotlin DSL:** The build automation system used to manage dependencies, build processes, and project configurations. Using Kotlin DSL provides type-safety and better IDE support compared to Groovy DSL.
*   **Detekt:** A static code analysis tool for Kotlin. It helps maintain code quality, detect code smells, and enforce coding standards.
*   **GitLab CI:** A powerful tool for Continuous Integration and Continuous Deployment, automating the build, test, and deployment processes.

## Architecture

The project follows a clean architecture approach, separating the application into distinct layers to promote modularity, testability, and maintainability:

*   **`app`**: The main application module, responsible for assembling the features and providing the entry point. It orchestrates the navigation and overall application flow.
*   **`common`**: Contains reusable components, base classes, UI elements, and themes that are shared across multiple modules. This promotes consistency and reduces code duplication.
    *   `base`: Common base classes and utilities.
    *   `provider`: Generic providers or factories.
    *   `theme`: Centralized UI theme and styling.
*   **`data`**: Handles data sources (local databases, remote APIs), data models, and repository implementations. It abstracts the data retrieval and storage logic from the business logic.
    *   `local`: Local data sources (e.g., Room database).
    *   `model`: Data transfer objects (DTOs) and domain models.
    *   `remote`: Remote data sources (e.g., Retrofit for REST APIs).
    *   `repository`: Abstractions for data operations, providing a clean API to the domain layer.
*   **`domain`**: Encapsulates the core business logic and use cases, independent of any specific framework or UI. This layer defines the application's rules and operations.
*   **`features`**: Each subdirectory within `features` represents a distinct feature module (e.g., `login`, `home`, `payment`), containing its own UI, view models, and feature-specific logic. This modularization allows for independent development and testing of features.
*   **`hardware`**: Manages integrations with various POS hardware devices, abstracting device-specific implementations.
*   **`libraries`**: Contains shared UI components, framework utilities, and scanner functionalities that can be reused across features. These are generally low-level, reusable components.
    *   `core-ui`: Core UI components.
    *   `core-ui-resources`: UI resources like drawables, strings, etc.
    *   `dialogs`: Reusable dialog components.
    *   `framework`: General framework utilities.
    *   `scanner`: Functionality related to barcode or QR code scanning.
*   **`build-logic`**: Custom Gradle build logic and convention plugins to standardize configurations across modules. This ensures consistent build settings and dependency management.

## Getting Started

Follow these instructions to set up and run the project on your local machine.

### Prerequisites

*   **Java Development Kit (JDK):** Version 17 or higher. Ensure `JAVA_HOME` is set correctly.
*   **Android Studio:** Latest stable version recommended for the best development experience.

### Cloning the Repository

```bash
git clone https://github.com/your-username/mobile-smartpos-era-kkm.git
cd mobile-smartpos-era-kkm
```

### Opening in Android Studio

1.  Open Android Studio.
2.  Select `File` > `Open` and navigate to the cloned `mobile-smartpos-era-kkm` directory.
3.  Android Studio will automatically sync the Gradle project and download necessary dependencies. This might take some time on the first run.

### Building the Project

To build the project from the command line:

```bash
./gradlew assembleDebug
```

This command will build the debug version of the application. You can find the generated APK in `app/build/outputs/apk/debug/`.

### Running the Application

To run the application on an emulator or a connected device from Android Studio, select the `app` module in the toolbar and click the `Run` button (green play icon).

Alternatively, from the command line, after building:

```bash
./gradlew installDebug
```

This command will install the debug APK on any connected device or running emulator.

## Project Structure

Here's a brief overview of the top-level directories:

*   `app/`: Main application module.
*   `build-logic/`: Custom Gradle build logic and convention plugins.
*   `common/`: Shared common modules (base, provider, theme).
*   `data/`: Data layer modules (local, model, remote, repository).
*   `domain/`: Domain layer module containing business logic.
*   `features/`: Individual feature modules (e.g., `account`, `login`, `payment`).
*   `gradle/`: Gradle wrapper and version catalog (`libs.versions.toml`).
*   `hardware/`: Hardware integration module.
*   `libraries/`: Reusable UI and utility libraries.
*   `scripts/`: Utility scripts (e.g., `pre-push.sh`, `setup.sh`).

## Code Quality and Style

This project uses [Detekt](https://detekt.dev/) for static code analysis to maintain code quality and consistency. It helps identify potential bugs, code smells, and enforces a consistent coding style.

To run Detekt checks:

```bash
./gradlew detekt
```

Configuration for Detekt can be found in `config/detekt/detekt.yml`. You can customize rules and baselines there.

## CI/CD

The project uses GitLab CI for continuous integration and deployment. The configuration is defined in `.gitlab-ci.yml`. This file outlines the stages for building, testing, and deploying the application automatically.

## Contributing

Contributions are welcome! Please follow the existing code style and project conventions. Before submitting a pull request, ensure your code passes all Detekt checks and tests.

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'feat: Add new feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

## License

(Add your project's license information here, e.g., MIT, Apache 2.0)
