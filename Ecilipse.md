# Eclipse - spring boot

## Useful Commands

### mvn clean package

Perform two main actions

1. `Clean the Project:` The clean phase removes the target directory, which is where Maven stores all the compiled files and packaged artifacts from previous builds. This ensures that the build starts from a clean slate, eliminating any potential issues caused by leftover files from previous builds.

2. `Package the Project:` The package phase compiles the source code, runs tests, and packages the compiled code into a distributable format, such as a JAR or WAR file. This is done after cleaning, ensuring that only fresh and up-to-date code is included in the final package. (`mvn clean package -DskipTests` to not run test)

### Run the JAR with environment variables

Command: `java jar target/[jarName.jar] [--EnvVar1=99999] [--EnvVar2=77777]`

## Shorthands

- `Alt+Shift+R` --> To rename a variable/method/class all the places at once.
- `Alt+Shift+F` --> Format document/selected section.
- `Alt+Shift+L` --> Create a seperate varibale for following equation.
- `Alt+Shift+M` --> Create a function for the selected lines of code and write the name of that code on it's location.
- `Ctrl+Shift+O` --> Minimize the code after the whole work is done.
- `Ctrl+D` --> Delete a whole line of code.

## Swagger

How to add swagger to a spring boot application.

## Environment variables

### Use

Environment variables in Spring Boot allows you to externalize your configuration and manage different environments like dev, test, staging, production, without having to change your code.

### How to use application.properties in code

No need to add any extra dependency.

1. Add the .env or profiled .envs
2. Access the code in the classes like:

```text
@Value("${client.UI_HOME_URL}")
private String UI_HOME_URL;
// OR
@Autowired
private final Environment env = null;

system.out.print("UI_HOME_URL value: {} | {}", UI_HOME_URL, env.getProperty("client.UI_HOME_URL"));
```

### How to use the .env keys in application.properties

Add configuration in application.properties or application.yml

```text
spring:
  config: # Reads .env
    import: classpath:.env[.properties]

#classpath: --Read from the src>main>resources
#file: use file for the project base
```

Now use the key in resource like: client.work=${EnvKey}

## RestTemplate -- WebClient

RestTemplate is old and WebClient is new.

### RestTemplate

### WebClient
