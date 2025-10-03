## Project Overview
This project is a command-line train booking system. It allows users to:
Sign up and log in.
Search for trains between specified stations.
Book seats on a selected train.
Cancel existing bookings.
Fetch and view their bookings.

## Key Components and Functionality
app/build.gradle
Plugins: Uses the application plugin for building a CLI application.
Repositories: Relies on mavenCentral() for dependency resolution.
Dependencies:
com.google.guava:guava
com.fasterxml.jackson.core:jackson-databind
org.projectlombok:lombok
org.mindrot:jbcrypt
Testing: Configured to use JUnit 4.
Java Toolchain: Specifies Java version 8.
Main Class: ticket.booking.App is defined as the entry point.

## app/src/main/java/ticket/booking/App.java
Main Application Logic: Contains the main method that drives the application.
User Interaction: Uses Scanner for user input.
Menu-Driven Interface: Presents a numbered menu of options to the user.
Core Services: Interacts with UserBookingService for most operations.
User Management: Handles user sign-up and login.
Train Search: Allows users to input source and destination to find trains.
Seat Booking: Displays available seats and allows users to select a seat for booking.

## app/src/main/java/ticket/booking/entities
Ticket.java: Represents a booking ticket with details like ticket ID, user ID, source, destination, date of travel, and the associated train.
Train.java: Represents a train with properties such as train ID, train number, seat availability (represented as a 2D integer list), station times, and a list of stations.
User.java: Represents a user with attributes like name, password, hashed password, a list of booked tickets, and a user ID.

## app/src/main/java/ticket/booking/service
TrainService.java:
Manages train data, loading it from ../localDB/trains.json.
Provides functionality to search trains based on source and destination.
Supports adding and updating train information, saving changes back to the JSON file.
Includes a validTrain method to check if a train route is valid between given stations.
UserBookingService.java:
Handles user authentication (login and sign-up) using BCrypt for password hashing.
Manages user data, loading from app/src/main/java/ticket/booking/localDb/users.json.
Provides methods for fetching user bookings, canceling bookings, searching trains (by delegating to TrainService), fetching seat availability, and booking train seats.
Updates seat availability in the Train object and persists changes via TrainService.

## app/src/main/java/ticket/booking/util/UserServiceUtil.java
Password Hashing: Utilizes jbcrypt library for securely hashing passwords using BCrypt.hashpw.
Password Verification: Provides a method checkPassword to verify a plain-text password against a hashed password.

## Build and Configuration Files
gradle/libs.versions.toml: Defines versions for project dependencies, specifically guava.
gradle/wrapper/gradle-wrapper.properties: Configures the Gradle wrapper, specifying the Gradle distribution URL (gradle-8.5-bin.zip).
gradle.properties: Contains general Gradle build configurations, enabling parallel execution and caching.
settings.gradle: Configures the project structure, setting the root project name to ticket-booking and including the app module. It also applies the foojay-resolver-convention plugin.
gradlew and gradlew.bat: These are the Gradle wrapper scripts for POSIX (Linux/macOS) and Windows, respectively, allowing the project to be built and run without a local Gradle installation.

## Data Storage
User Data: Stored in app/src/main/java/ticket/booking/localDb/users.json.
Train Data: Stored in ../localDB/trains.json.

## Key Libraries Used
Jackson: For JSON serialization and deserialization of data objects.
Lombok: To reduce boilerplate code (e.g., getters, setters, constructors).
jBCrypt: For secure password hashing and verification.
Guava: For general utility functions.

## Tech stack- Core Java, Advanced Java
