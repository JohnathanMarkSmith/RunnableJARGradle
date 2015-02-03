How to create a runnable JAR file with Gradle
Java, Gradle

This post will show you how we can compile and package a simple Java Project using Gradle.


Project Layout
The default project layout of a Java project with Gradle is following (just like Maven):

The src/main/java directory contains the source code.
The src/main/resources directory contains the resources (such as properties files).
The src/test/java directory contains the test classes.
The src/test/resources directory contains the test resources.

so know make a new folder where you would like the project to start..

mkdir runnablejar
cd runnablejar

Now lets create the project layout by using the following commands
mkdir -p src/main/java
mkdir -p src/main/resources
mkdir -p src/test/java
mkdir -p src/test/resources

As you can see from above the project layout looks just like a Maven project.

Creating the Main Class
Lets create the main class for this project and lets have it display "Hello World"

Now cd into src/main/java

and create the package layout

mkdir -p com/johnathanmarksmith/gradle

Now we have the project layout created and also the package layout so now lets create the Main Class

vi com/johnathanmarksmith/gradle/HelloWorld.java

and insert the following lines
package com.johnathanmarksmith.gradle;
public class HelloWorld {
    public static void main(String[] args) {
          System.out.println("Hello World!");
    }
}

Creating the Gradle Build File..
Now its time to create the Gralde Build file, Go back to the root of the project.
cd ../../..

Now lets create the build file
vi build.gradle

and add the following lines

apply plugin: 'java'
jar {
baseName = 'smith'
version = '1.0'
manifest {
attributes 'Main-Class': 'com.johnathanmarksmith.gradle.HelloWorld'
}
}


Building the project and creating the JAR

To build the project and to create the JAR you need to run the following command
gradle build

Executeing the JAR
java -jar ./build/libs/smith-1.0.jar



