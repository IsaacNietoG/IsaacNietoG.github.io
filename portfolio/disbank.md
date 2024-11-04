---
layout: default
---
# Disbank
### [Github link](https://github.com/DystopianRescuer/disbank)

The project is designed to address the inaccessibility of card payments for local businesses, specifically for payments at the "Merkadita" of the UNAM Faculty of Sciences.

Through a shared terminal and the generation of payment links, all via a Telegram bot and using the CLIP API, we create a payment network that provides these resources to each of our clients so they can easily accept card payments with minimal or almost no registration requirements. At the end of the day, each associate's sales are delivered to them through the method that suits them best.

## Motives to make this project

We made this project as a deliverable work for our Modeling and Programming Course in college. The focus was mainly centered in learning about design patterns and API consumption from our Java Application.
The idea was of our own and all the lines we wrote were, for our bad luck, entirely made by us. (around 2k lines of code).

It currently has no documentation but I plan to change that in the future. For the moment and if you wanna test it, these are the compile instructions:

## How to compile
The program uses JDK 21, so this is a required tool to compile the project. Beyond that, since we use Maven to manage the project code, compilation is "trivial" and follows these steps:

Building the Project
For this, we simply run the following command in the project's root folder (disbank):
mvn clean install
(If we want to compile while skipping unit tests, we can use mvn clean install -Dmaven.test.skip=true).

It will first attempt to pass the unit tests. To do so, we need to pass these tests. Most of them are automated, but specifically for the Telegram API tests, a series of messages need to be sent. 

It is also important to note that the project is designed to be compiled with a Java 21 implementation, and Maven itself will not allow compilation if this version of Java is not present on the computer, so having this version installed is a prerequisite.

Importing Configurations
The project requires access to the Clip and Telegram APIs.
This API Keys should be put in target/config

Similarly, to ensure daily report files are stored properly, we create a reports folder with:
mkdir target/cortesDiarios

Following these instructions, the jar file generated during compilation is fully independent of the source code, and the entire target folder is the compiled program that we can use anywhere on our computer.

Running the Project
To run the project, execute the following command:
java -jar target/disbank.jar
