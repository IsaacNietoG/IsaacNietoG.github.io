---
layout: default
---
# People Counter
### [Github link](https://github.com/DystopianRescuer/PeopleCounter)

This was a project in which we decided to build a real-time people counter. Using AI models and computer vision techniques.
You can open this program, trace a line and get a real-time counter of the people that crosses this line.

This project combines Ultralytics YOLO8, a state-of-the-art object detection model with SORT, a robust tracking algorithm that accurately counts individuals crossing the virtual boundary.

## About the technology used
[Ultralytics YOLO8](https://docs.ultralytics.com/) is one of the crown jewels we used for the project. This is a very cool and cutting edge object detection model that gives a pretty good and fast insight of the objects detected by the camera/video used as input. This was the first step for our project, cause we obviously needed to know what was a person and what wasn't.
Then, we used [SORT](https://github.com/abewley/sort), the second crown jewel. This is, a grosso modo, a tracking algorith that enables us to keep a track of which persons have already crossed the line and which ones didn't.
Those were the two main crown jewels we used for almost all the functionality and with those we had the main function of the project finished.

## Features
### Real-Time Detection
This program can process both video streams or camera feeds. And it tracks the people from these input almost instantly.
### Customizable Virtual Line
The line is customizable, allowing the application to adapt to various scenarios.
### Accurate tracking
The SORT library ensures that individuals are counted only once, even if they constantly linger around the counting line.

## How to use
The github repository has a very good README that you can use for the instructions to prepare your device for the program and simple instructions on how to run it. But mainly:
1. Run the program with the wanted input
2. Draw the line
3. Watch the magic :D

## Challenges and insights
One of the trickiest aspects was ensuring that individuals lingering near the line weren't counted multiple times. To tackle this, I remembered that we had SORT (yeah, until this problem appeared I didn't knew why we were using SORT lol). Using SORT, I used a dictionary to track each unique ID and its state relative to the line. In this challenge, I highlighted the importance of meticulous data handling.
Then, I had a very hard time preparing the dependencies needed to run this project. My intention was that anyone could run this project only with a few command lines and little to no other things apart from this. For this, I had to make a very good README and a very good requirements.txt (for automatic dependencies download with Python pip), and although it should have been easy, I am not very proud to admit that I had more troubles and challenges in this than in the rest of the project elaboration. But at the end, we achieved to make a very good and decent installation experience, something that I always want to achieve in all my projects, aside with a good documentation. (because I like a lot to talk with myself.)

## Final thoughts
This was an incredibly rewarding experience where we applied the power of modern AI tools and their potential in everyday scenarios.
