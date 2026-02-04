# Gradle Essential Commands

## Project Introspection

* **List tasks:** `./gradlew tasks`
* **List dependencies:** `./gradlew dependencies`
* **Check properties:** `./gradlew properties`
* **Task help:** `./gradlew help --task <taskName>`

## Build & Execution

* **Build project:** `./gradlew build`
* **Stop demon threads** `gradle --stop`
* **Clean:** `./gradlew clean`
* **Clean build:** `./gradlew clean build`
* **Clean Publish:** `./gradle clean publish`
* **Compile only:** `./gradlew classes`
* **Run application:** `./gradlew run`
* **Exclude task:** `./gradlew build -x test`

## Dependency Management

* **Refresh dependencies:** `./gradlew build --refresh-dependencies`
* **Verify specific dependency:** `./gradlew dependencyInsight --dependency <name>`

## Testing

* **Run all tests:** `./gradlew test`
* **Run single test:** `./gradlew test --tests "com.example.ClassName"`
* **Continuous testing:** `./gradlew test -t`

## Debugging & Performance

* **Stacktrace:** `./gradlew <task> --stacktrace`
* **Debug level info:** `./gradlew <task> --info`
* **Build scan:** `./gradlew <task> --scan`
* **Dry run:** `./gradlew <task> -m`
* **Parallel build:** `./gradlew <task> --parallel`

---
