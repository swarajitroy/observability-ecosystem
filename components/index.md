
# Data Types for Observability
---

## Logs
---
If you are in Java - one of the best way to start with **Simple Logging Facade for Java (SLF4J)**

- The Simple Logging Facade for Java (SLF4J) serves as a simple facade or abstraction for various logging frameworks (e.g. java.util.logging, logback, log4j) allowing the end user to plug in the desired logging framework at deployment time
- Note that SLF4J-enabling your library implies the addition of only a single mandatory dependency, namely slf4j-api.jar. If no binding/provider is found on the class path, then SLF4J will default to a no-operation implementation
- Add a specific provider of your choice (I used logback) 

### Import SLF4J + SLF4J provider
---

In the pom.xml - add these two dependenices
```
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>2.0.6</version>
</dependency>

<dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.4.5</version>
</dependency>

```

### Basic Java Code
---

```
package org.ulearnuhelp.observability;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class App {

    private static Logger logger = LoggerFactory.getLogger(App.class);

    public static void main(String[] args) {

        logger.info("This is an info level log message!");
    }
}
```
When we run the program, we get an output in the terminal like, 

```
20:35:00.335 [main] INFO org.ulearnuhelp.observability.App - This is an info level log message!
```

### Log Configuration
---

Using a logback.xml file (available in classpath) - we can configure the logging line. 
The following configuration logs to, 

- Standard Output 
- Level - DEBUG - that means INFO etc will be automatically printed
- Pattern (Details explanation https://logback.qos.ch/manual/layouts.html) 

%d{HH:mm:ss.SSS} - date format 
%thread - the java thread name
%-5level - The log level within 5 characters
%logger{36} - The logger name within 36 character

 ```
<configuration>

  <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
    <!-- encoders are assigned the type
         ch.qos.logback.classic.encoder.PatternLayoutEncoder by default -->
    <encoder>
      <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} -%kvp- %msg%n</pattern>
    </encoder>
  </appender>

  <root level="debug">
    <appender-ref ref="STDOUT" />
  </root>
</configuration>
```

### JSON Output
---
java -Dlogback.configurationFile=/path/to/config.xml <Your Main Class/ Exe. JAR>
Or,
System.setProperty("logback.configurationFile", "/path/to/config.xml");
