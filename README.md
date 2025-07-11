# Smart ERA

Smart ERA is a modular, production-grade Android application for smart POS (Point of Sale) terminals, built with Kotlin, Jetpack Compose, Hilt, and a clean architecture approach. The project is designed for extensibility, maintainability, and robust hardware integration, supporting a wide range of payment, fiscal, and business operations.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Architecture](#architecture)
- [Modules](#modules)
- [Features](#features)
- [Build & Run](#build--run)
- [Dependencies](#dependencies)
- [Configuration](#configuration)
- [ProGuard & Security](#proguard--security)
- [Contributing](#contributing)
- [License](#license)

---

## Project Overview
Smart ERA is a comprehensive POS solution for Android, supporting advanced payment flows, fiscalization, device management, and business operations. It is built as a multi-module Gradle project, leveraging modern Android development best practices.

- **Minimum SDK:** 22
- **Target SDK:** 34
- **Language:** Kotlin
- **UI:** Jetpack Compose
- **Dependency Injection:** Hilt
- **Build System:** Gradle (Kotlin DSL)
- **Main Application ID:** `uz.cdti.smart.era.app`

---

## Architecture
The project follows a clean, modular architecture:
- **App Layer:** Entry point, DI setup, navigation, and global configuration.
- **Feature Modules:** Each business domain (e.g., Home, Payment, Order, Fiscal, etc.) is a separate module.
- **Data Layer:** Handles local, remote, and repository data sources.
- **Domain Layer:** Contains business logic and use cases.
- **Common & Libraries:** Shared code, UI components, dialogs, and hardware abstractions.

### Main Entry Points
- **Application:** [`SmartposApp`](app/src/main/java/uz/uzkassa/smartpos/app/SmartposApp.kt)
- **Main Activity:** [`MainActivity`](app/src/main/java/uz/uzkassa/smartpos/app/MainActivity.kt)
- **Compose App:** [`SmartposComposeApp`](app/src/main/java/uz/uzkassa/smartpos/app/ui/SmartposComposeApp.kt)

---

## Modules
The project is organized into the following Gradle modules:

- **:app** — Main application module
- **:common:base, :common:provider, :common:theme** — Shared code and themes
- **:data:local, :data:model, :data:remote, :data:repository** — Data sources and repositories
- **:domain** — Business logic and use cases
- **:features:**
  - account, apay, cash_operations, cash_operations_management, credit_advance, fiscal, home, login, order, payment, profile, receipt, refund
- **:hardware** — Hardware abstraction and integration
- **:libraries:**
  - core-ui, core-ui-resources, dialogs, framework, scanner
- **:build-logic** — Gradle build logic and conventions

---

## Features
- Modularized business features (Account, Payment, Order, Fiscal, etc.)
- Hardware integration (Bluetooth, USB, Camera, etc.)
- Secure data handling and backup
- WorkManager-based background jobs (sync, backup, notifications)
- Jetpack Compose UI with custom theming
- Multi-language support
- Dependency injection with Hilt
- ProGuard/R8 configuration for release builds
- Firebase integration (Config, Analytics, Crashlytics)
- Device and firmware management

---

## Build & Run

### Prerequisites
- **JDK 17+**
- **Android Studio Giraffe or newer**
- **Android SDK 34**
- **Gradle 8.4+**

### Setup
1. **Clone the repository:**
   ```sh
   git clone <repo-url>
   cd mobile-smartpos-era-kkm
   ```
2. **Configure local properties:**
   - Copy `local.properties.example` to `local.properties` and fill in the required values.
3. **Run setup script (Linux/macOS):**
   ```sh
   sh ./scripts/setup.sh
   ```
   Or on Windows, ensure Git Bash is installed and run the script.
4. **Build the project:**
   ```sh
   ./gradlew clean build
   ```
5. **Run on device/emulator:**
   ```sh
   ./gradlew :app:installDebug
   ```

### APK Output
- APKs are output to `app/build/outputs/apk/` with names like `app-debug-v3-3.apk` or `app-release-v3-3.apk`.

---

## Dependencies
Key libraries and frameworks:
- **Jetpack Compose** (UI)
- **Hilt** (DI)
- **Room** (Database)
- **WorkManager** (Background tasks)
- **Firebase** (Config, Analytics, Crashlytics)
- **Retrofit, OkHttp** (Networking)
- **Coil** (Image loading)
- **Timber** (Logging)
- **Custom hardware SDKs:** gtpos, era, kozen, nexgo, fiscal, etc.
- **Testing:** JUnit, Espresso, MockK

See [`gradle/libs.versions.toml`](gradle/libs.versions.toml) for all versions and libraries.

---

## Configuration
- **ProGuard rules:** See [`app/proguard-rules.pro`](app/proguard-rules.pro)
- **Detekt (static analysis):** Configured in [`config/detekt/detekt.yml`](config/detekt/detekt.yml)
- **Signing config:** Release signing uses `app/appkeystore/appkeystore.jks` (see `app/build.gradle.kts`)
- **Environment variables:** Some Maven credentials and URLs are loaded from `local.properties` or environment variables.

---

## ProGuard & Security
- ProGuard rules are provided for all major libraries and custom SDKs.
- Sensitive keys and passwords should be managed securely and not committed to VCS.
- Ensure to update `local.properties` and keystore files for production builds.

---

## Contributing
1. Fork the repository and create your branch from `main`.
2. Follow the code style and Detekt rules.
3. Write clear commit messages and document your code.
4. Test your changes thoroughly.
5. Submit a merge request with a clear description.

---

## License
This project is proprietary and confidential. All rights reserved.
