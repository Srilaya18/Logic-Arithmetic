transmit-between-ports/
│── pom.xml
└── src/
    ├── main/java/com/socketapp/LogicApp.java
    └── test/java/com/socketapp/AppTest.java

LogicApp.java
package com.socketapp;

import java.util.Scanner;

public class LogicApp {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter two boolean values (true/false):");
        boolean a = sc.nextBoolean();
        boolean b = sc.nextBoolean();
        System.out.println("Choose operation:");
        System.out.println("1. AND");
        System.out.println("2. OR");
        System.out.println("3. NOT");
        int choice = sc.nextInt();
        switch (choice) {
            case 1:
                System.out.println("Result: " + (a && b));
                break;
            case 2:
                System.out.println("Result: " + (a || b));
                break;
            case 3:
                System.out.println("Result: " + (!a));
                break;
            default:
                System.out.println("Invalid choice");
        }
        sc.close();
    }
}

pom.xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.socketapp</groupId>
    <artifactId>transmit-between-ports</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0</version>
            </plugin>
        </plugins>
    </build>
</project>

AppTest.java
package com.socketapp;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;
public class AppTest {
    @Test
    void testAnd() {
        assertFalse(true && false);
    }
    @Test
    void testOr() {
        assertTrue(true || false);
    }
    @Test
    void testNot() {
        assertFalse(!true);
    }
}

TERMINAL -> mvn clean
mvn compile
mvn test
mvn package

CREATE AND LINK GIT REPO

PIPELINE SCRIPT
pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/your-username/transmit-between-ports.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }
}

Dockerfile
FROM eclipse-temurin:17
WORKDIR /app
COPY target/transmit-between-ports-1.0-SNAPSHOT.jar app.jar
CMD ["java", "-cp", "app.jar", "com.socketapp.LogicApp"]

COMMIT CHANGE TO GIT
git add Dockerfile
git commit -m "Added Dockerfile"
git push

UPDATE SCRIPT
pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/your-username/transmit-between-ports.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
        stage('Docker Build') {
            steps {
                bat 'docker build -t transmit-app .'
            }
        }
        stage('Docker Run') {
            steps {
                bat 'docker run -it transmit-app'   //or try bat 'docker run transmit-app'
            }
        }
    }
}



FOR ARITHMETIC
LogicApp.java
package com.socketapp;

import java.util.Scanner;

public class ArithmeticApp {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter two numbers:");
        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.println("Choose operation:");
        System.out.println("1. Add");
        System.out.println("2. Subtract");
        System.out.println("3. Multiply");
        System.out.println("4. Divide");

        int choice = sc.nextInt();

        switch (choice) {
            case 1:
                System.out.println("Result: " + (a + b));
                break;
            case 2:
                System.out.println("Result: " + (a - b));
                break;
            case 3:
                System.out.println("Result: " + (a * b));
                break;
            case 4:
                if (b != 0)
                    System.out.println("Result: " + (a / b));
                else
                    System.out.println("Cannot divide by zero");
                break;
            default:
                System.out.println("Invalid choice");
        }

        sc.close();
    }
}

JUnit
@Test
void testAdd() {
    assertEquals(5, 2 + 3);
}

@Test
void testMultiply() {
    assertEquals(6, 2 * 3);
}
