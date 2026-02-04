# Maven Essential Commands

## Project Introspection

* **List active profiles:** `mvn help:active-profiles`
* **Display effective POM:** `mvn help:effective-pom`
* **List all goals:** `mvn help:describe -Dplugin=help`

## Build Lifecycle

* **Clean & Package:** `mvn clean package`
* **Install to local repo:** `mvn clean install`
* **Skip tests:** `mvn install -DskipTests`
* **Compile source:** `mvn compile`
* **Verify project:** `mvn verify`

## Dependency Management

* **Tree view:** `mvn dependency:tree`
* **Analyze unused/missing:** `mvn dependency:analyze`
* **Purge local repository:** `mvn dependency:purge-local-repository`
* **Download sources:** `mvn dependency:sources`

## Testing

* **Run all tests:** `mvn test`
* **Run single test:** `mvn test -Dtest=ClassName`
* **Run specific method:** `mvn test -Dtest=ClassName#methodName`

## Debugging & Performance

* **Produce error stacktrace:** `mvn <goal> -e`
* **Full debug logging:** `mvn <goal> -X`
* **Threaded/Parallel build:** `mvn <goal> -T 1C` (1 core per thread)
* **Offline mode:** `mvn <goal> -o`

---
