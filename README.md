# maven-quick-start
Sample maven project


# Udemy - Maven

## 2. Maven Key Concepts
- Java und andere
- Dependency Mgmt
- Repository
- Plugins
    - + functionality
    - More goals
    - Furhter dependencies
- Convention/Configuration —> best practices
- POM - Project Object Model
    -



## 2.7 Mac Env
- Git
- Git Editor
git config --global core.editor "atom -w"
git config --global -e
- Java
java -version
JAVA_HOME —> .bashrc —> export JAVA_HOME=`/usr/libexec/java_home`
- Maven
.bashrc:
export MAVEN_HOME=/Development/maven
export PATH="${PATH}:${MAVEN_HOME}/bin"

## 3 Abschnitt 13


- Goals = Task in Ant
    - plugin + goal name
    - „compile goal on compiler plugin“
- Phases
    - 1.. Goals
- Lifecylces
￼

Maven directories:
￼
 - root -> src ->
   - main
     - java
     - resources
     - webapp (Web Application Location)
     - groovy (Groovy Source)
  - test
    - java
    - resources

￼
￼
￼

Convention over Configuration Model = Maven hat Standardwerte, die nicht konfiguriert werden. zB., dass src/main/java Source Dateien beinhaltet.

Create Source folder

	   mkdir -p src/main/java

Create Source file in package structure

	   tobi/programming/training/Application.java

Compile package —> /target folder is created

	   mvn package

Run Java class with Classpath (-cp)

    macbook-pro:maven-quick-start tobi$ java -cp target/maven-quick-		start-1.0.jar  tobi.programming.training.Application
    Starting Application
    Inside Application

Clean project from /target folder

    mvn clean

Multiple goals: clean + package
- Clean from clean Lifecycle
- Package from JAR Lifecycle

      mvn clean package

#### Maven Local Repository
- Clean = cleans up
- Package = erstellt target folder + JAR file
- Install = takes JAR file and puts into special location
    - Into Maven Local Repo —> .m2 folder


    macbook-pro:maven-quick-start tobi$ pwd
    /Users/tobi/.m2/repository/learn/tobi/maven-quick-start
    macbook-pro:maven-quick-start tobi$ ls -al
    total 8
    drwxr-xr-x  4 tobi  staff  128 11 Okt 16:45 .
    drwxr-xr-x  3 tobi  staff   96 11 Okt 16:45 ..
    drwxr-xr-x  5 tobi  staff  160 11 Okt 16:45 1.0
    -rw-r--r--  1 tobi  staff  303 11 Okt 16:45 maven-metadata-local.xml

    macbook-pro:maven-quick-start tobi$ cd 1.0/
    macbook-pro:1.0 tobi$ ls -al
    total 24
    drwxr-xr-x  5 tobi  staff   160 11 Okt 16:45 .
    drwxr-xr-x  4 tobi  staff   128 11 Okt 16:45 ..
    -rw-r--r--  1 tobi  staff   190 11 Okt 16:45 _remote.repositories
    -rw-r--r--  1 tobi  staff  2406 11 Okt 16:45 maven-quick-start-1.0.jar
    -rw-r--r--  1 tobi  staff   360 10 Okt 23:17 maven-quick-start-1.0.pom



## Kapitel 4 - Plugins
￼
- Compile Source Code
- Run Unit Testing
- Publish to Artifact Repository
- Deploy to Remote Server
- Publish Documenation
- ...


- https://maven.apache.org/plugins/
- Compile: Standard Java version 1.5 is used —> manually set it to 1.8



## Kapitel 5 - Dependencies
￼
- Maven = Dependency Mgmt
￼- Finding Dependencies (External repositories)
- COntorolling when used (Scopes)
￼

#### Maven Repository
1. local first
2. Maven Central
3. other Repos



## Scopes

Source: Udemy Trainging: https://www.udemy.com/maven-quick-start/learn/v4/content 

￼![Compile Scope](/pics/Scope_Compile.png)
￼￼![Runtime Scope](/pics/Scope_Runtime.png)￼
![Test Scope](/pics/Scope_Test.png)
￼￼![Provided Scope](/pics/Scope_Provided.png)
￼![System Scope](/pics/Scope_System.png)
￼![Import Scope](/pics/Scope_Import.png)
￼

￼

- Maven Central Repository: http://search.maven.org
- Dependency Tree:
- „mvn dependency:tree“


    macbook-pro:maven-quick-start tobi$ mvn dependency:tree
    [INFO] Scanning for projects...
     …
    [INFO] tobi.lern:maven-quick-start:jar:1.0
    [INFO] \- org.apache.commons:commons-lang3:jar:3.6:compile

    mvn dependency:tree > dependency-list.txt




## JUnit Testing with Maven
- Junit depdendency
    - https://search.maven.org/#artifactdetails%7Cjunit%7Cjunit%7C4.12%7Cjar
    - In pom.xml eintragen
- „mvn test“ —> explizit testing
- „mvn clean install“ —> auch test als Part des JAR Lifecycles
- „Surefire-reports“ —> /target/surefire-reports
    - XML + TXT file
    - XML —> kann von externen System gelesen werden (Sonar?)
    - TXT —>
-
-


## Maven Eclipse MacOS
- „Effektive POM“ —> Projekt POM + Super POM von Maven + Dependent POM => alles in einem
- „pom.xml“ —> Project POM




## Archetypes
- Maven Project Templates
- https://maven.apache.org/archetype/index.html
- „Mvn archetype:generate“ —> im Plugin archetype das Goal generate ausführen
- Generiert nach Auswählen eines Templates das Maven Projekt —> Name, GroupID usw. wird abgefragt
    - pom.xml
    - Src-Folder
