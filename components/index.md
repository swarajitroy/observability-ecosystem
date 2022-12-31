
# Data Types for Observability
---

## Logs
---
If you are in Java - one of the best way to start with **Simple Logging Facade for Java (SLF4J)**

- The Simple Logging Facade for Java (SLF4J) serves as a simple facade or abstraction for various logging frameworks (e.g. java.util.logging, logback, log4j) allowing the end user to plug in the desired logging framework at deployment time
- Note that SLF4J-enabling your library implies the addition of only a single mandatory dependency, namely slf4j-api.jar. If no binding/provider is found on the class path, then SLF4J will default to a no-operation implementation
- logback 

### Import SLF4J 
---

`<!-- https://mvnrepository.com/artifact/org.slf4j/slf4j-api -->
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>2.0.6</version>
</dependency>
`
