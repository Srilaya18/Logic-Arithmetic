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
