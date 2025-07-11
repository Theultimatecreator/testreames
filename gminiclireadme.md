# Mobile SmartPOS ERA KKM

This repository contains the source code for the Mobile SmartPOS ERA KKM application, a modern Android application designed for Point of Sale (POS) operations, likely integrating with fiscal registers (KKM). The project is built with a modular architecture to ensure scalability, maintainability, and clear separation of concerns.

## Features

*   **Point of Sale Operations:** Core functionalities for processing sales transactions.
*   **Modular Design:** Features are organized into independent modules for better development and testing.
*   **Hardware Integration:** Support for various POS hardware devices.
*   **User Management:** (Assumed) Login and account management.
*   **Cash Operations:** (Assumed) Handling cash-related transactions.
*   **Payment Processing:** (Assumed) Integration with payment systems.
*   **Receipt Generation:** (Assumed) Printing or displaying receipts.

## Technologies Used

*   **Kotlin:** The primary programming language for Android development.
*   **Android Jetpack Compose:** Modern toolkit for building native Android UI.
*   **Gradle Kotlin DSL:** Build automation system for managing dependencies and build processes.
*   **Detekt:** Static code analysis tool for Kotlin.
*   **GitLab CI:** Continuous Integration/Continuous Deployment pipeline.

## Architecture

The project follows a clean architecture approach, separating the application into distinct layers:

*   **`app`**: The main application module, responsible for assembling the features and providing the entry point.
*   **`common`**: Contains reusable components, base classes, UI elements, and themes shared across multiple modules.
*   **`data`**: Handles data sources (local databases, remote APIs), data models, and repository implementations.
*   **`domain`**: Encapsulates the core business logic and use cases, independent of any specific framework.
*   **`features`**: Each subdirectory within `features` represents a distinct feature module (e.g., `login`, `home`, `payment`), containing its own UI, view models, and feature-specific logic.
*   **`hardware`**: Manages integrations with various POS hardware devices.
*   **`libraries`**: Contains shared UI components, framework utilities, and scanner functionalities that can be reused across features.
*   **`build-logic`**: Custom Gradle build logic and convention plugins to standardize configurations across modules.

## Getting Started

Follow these instructions to set up and run the project on your local machine.

### Prerequisites

*   **Java Development Kit (JDK):** Version 17 or higher.
*   **Android Studio:** Latest stable version recommended.

### Cloning the Repository

```bash
git clone https://github.com/your-username/mobile-smartpos-era-kkm.git
cd mobile-smartpos-era-kkm
```

### Opening in Android Studio

1.  Open Android Studio.
2.  Select `File` > `Open` and navigate to the cloned `mobile-smartpos-era-kkm` directory.
3.  Android Studio will automatically sync the Gradle project.

### Building the Project

To build the project from the command line:

```bash
./gradlew assembleDebug
```

### Running the Application

To run the application on an emulator or a connected device from Android Studio, select the `app` module and click the `Run` button.

Alternatively, from the command line:

```bash
./gradlew installDebug
```

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

This project uses [Detekt](https://detekt.dev/) for static code analysis to maintain code quality and consistency.

To run Detekt checks:

```bash
./gradlew detekt
```

Configuration for Detekt can be found in `config/detekt/detekt.yml`.

## CI/CD

The project uses GitLab CI for continuous integration and deployment. The configuration is defined in `.gitlab-ci.yml`.

## Contributing

Contributions are welcome! Please follow the existing code style and submit pull requests for any new features or bug fixes.

## License

(Add your project's license information here, e.g., MIT, Apache 2.0)
