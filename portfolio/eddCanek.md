---
layout: default
---
# Data Structures in Java
### [Github link](https://github.com/IsaacNietoG/estructuras-de-datos-practicas-2024)

### Data Structures Seen

During this course, I implemented in the Java language all the basic data structures seen here:

- AVL Trees
- Complete Binary Trees
- Ordered Binary Trees
- Red-Black Trees
- Arrays (some sorting algorithms for them and the theory behind them)
- Queues
- Stacks
- Dictionaries (with some hash functions)
- Sets
- Graphs
- Linked Lists
- Binary Heaps (two implementations)

### About the course

The course was given by Dr. Canek Pelaez Valdez, during the 2024-2 semester, in the Faculty of Sciences of the National Autonomous University of Mexico.

The course relied heavily on the corresponding [book](https://tienda.fciencias.unam.mx/es/home/437-estructuras-de-datos-con-java-moderno-9786073009157.html) written by the professor; throughout the course, this was the main reference material.

### About the structure of this project

Each exercise has its own pom.xml file, so you can build the exercise with Maven and Java. In the same fashion, each exercise has its own README.md, written in Spanish, by the professor, with a brief explanation about the exercise and which chapters of the book you could use to do the exercise.

### How to build the exercises
The instructions come in every README.md of each exercise, although they are in spanish, generally this is the procedure.

```
$ mvn compile
...
$ mvn install
...
$ java -jar target/practicaX.jar
```
Where X is the exercise number you want to compile

### Thins I learned during this project/course
I learnead a lot about how the most popular data structures seen in this course behave and which one should be used in each project, this according to the requirements of the project we are currently working on. (for example, which binary tree is the most convenient depending on the expected performance expected in each operation). This, also considering the time and space complexities of each associated algorithm to the data structure.
Also, I learned a lot about the quirks of the Java Programming Language and how to adequately use some of its features for a better performance and behavior of some algorithms.
