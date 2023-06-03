+++
title = "JavaScript"
description = "JavaScript Notes"
weight = 2
+++

{{< lead >}}
JavaScript is a versatile and widely used programming language that primarily runs on web browsers. It enables interactive and dynamic elements on websites, providing functionalities like validating forms, creating animations, and handling user interactions. JavaScript is also utilized in server-side development, allowing the creation of web applications and APIs. Its syntax is easy to learn and read, making it accessible for beginners. JavaScript's extensive ecosystem includes libraries and frameworks like React, Angular, and Node.js, empowering developers to build robust and scalable applications. With its cross-platform compatibility and continuous growth, JavaScript has become a fundamental language for both front-end and back-end web development.
{{< /lead >}}

---

{{< panel title="WIP" style="danger" >}}
This site is a work in progress, notes are being actively added, formatted and reorganized at the moment.
{{< /panel >}}

{{< panel title="FreeCodeCamp Code of Conduct" style="danger" >}}

Before we issue our verified certification to a camper, he or she must accept our Academic Honesty Pledge, which reads:

"I understand that plagiarism means copying someone else’s work and presenting the work as if it were my own, without clearly attributing the original author.

"I understand that plagiarism is an act of intellectual dishonesty, and that people usually get kicked out of university or fired from their jobs if they get caught plagiarizing.

"Aside from using open source libraries such as jQuery and Bootstrap, and short snippets of code which are clearly attributed to their original author, 100% of the code in my projects was written by me, or along with another camper with whom I was pair programming in real time.

"I pledge that I did not plagiarize any of my freeCodeCamp work. I understand that freeCodeCamp’s team will audit my projects to confirm this."

In the situations where we discover instances of unambiguous plagiarism, we will replace the camper in question’s certification with a message that "Upon review, this account has been flagged for academic dishonesty."

As an academic institution that grants achievement-based certifications, we take academic honesty very seriously. If you have any questions about this policy, or suspect that someone has violated it, you can email team@freecodecamp.org and we will investigate.

{{< /panel >}}

## How I learned JavaScript

JavaScript was and is confusing to learn, I still struggle with numerous aspects of the language. However, it is essential when it comes to Front End interaction. I have taken and finished a number of FreeCodeCamp courses as part of my self directed study and found The JS Course chalenging and informative. I will likely refer back to it in the future, because it is well structured and available.

## FreeCodeCamp Course Description

While HTML and CSS control the content and styling of a page, JavaScript is used to make it interactive. In the JavaScript Algorithm and Data Structures Certification, you'll learn the fundamentals of JavaScript including variables, arrays, objects, loops, and functions.

Once you have the fundamentals down, you'll apply that knowledge by creating algorithms to manipulate strings, factorialize numbers, and even calculate the orbit of the International Space Station.

Along the way, you'll also learn two important programming styles or paradigms: Object Oriented Programming (OOP) and Functional Programming (FP).

##

{{< panel title="Spoiler Alert!" style="danger" >}}

## Personal Learning Notes

Some of this material is copied and pasted from some of the modules in the course in combination with my own notes.
Be aware that I might be giving away some of the answers, so if you are adhering the the Academic Honesty Policy posted by FCC, overt your eyes.

{{< /panel >}}

## Variables

Variables can container many different data types

### Declare JavaScript Variables

In computer science, data is anything that is meaningful to the computer. JavaScript provides eight different data types which are undefined, null, boolean, string, symbol, bigint, number, and object.

For example, computers distinguish between numbers, such as the number 12, and strings, such as "12", "dog", or "123 cats", which are collections of characters. Computers can perform mathematical operations on a number, but not on a string.

Variables allow computers to store and manipulate data in a dynamic fashion. They do this by using a "label" to point to the data rather than using the data itself. Any of the eight data types may be stored in a variable.

Variables are similar to the x and y variables you use in mathematics, which means they're a simple name to represent the data we want to refer to. Computer variables differ from mathematical variables in that they can store different values at different times.

We tell JavaScript to create or declare a variable by putting the keyword var in front of it, like so:

var ourName;

creates a variable called ourName. In JavaScript we end statements with semicolons. Variable names can be made up of numbers, letters, and $ or _, but may not contain spaces or start with a number.


### Declaring a sting variable

Variables can be declared in multiple ways.

var myName;
var myName = "your name";

### Initializing Variable with the Assignment Operator

var myVar = 0;

### Declare String Variables

var myName = "your name";

### Understanding Uninitialized Variables

When JavaScript variables are declared, they have an initial value of undefined. If you do a mathematical operation on an undefined variable your result will be NaN which means "Not a Number". If you concatenate a string with an undefined variable, you will get a string of undefined.

## Camelcase

In camelCase, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.

exampleCamelCase
anotherExampleOfThis

## JS mathematics



The remainder operator % gives the remainder of the division of two numbers.

Example

    5 % 2 = 1 because
    Math.floor(5 / 2) = 2 (Quotient)
    2 * 2 = 4
    5 - 4 = 1 (Remainder)

Usage
In mathematics, a number can be checked to be even or odd by checking the remainder of the division of the number by 2.

    17 % 2 = 1 (17 is Odd)
    48 % 2 = 0 (48 is Even)

Note: The remainder operator is sometimes incorrectly referred to as the modulus operator. It is very similar to modulus, but does not work properly with negative numbers.

## Golf script

    const names = ["Hole-in-one!", "Eagle", "Birdie", "Par", "Bogey", "Double Bogey", "Go Home!"];

    function golfScore(par, strokes) {
    // Only change code below this line

    if (strokes == 1) {
        return names[0];
    } else if (strokes <= par - 2) {
        return names[1];
    } else if (strokes === par - 1) {
        return names[2];
    } else if (strokes === par) {
        return names[3];
    } else if (strokes === par + 1) {
        return names[4];
    } else if (strokes === par + 2) {
        return names[5];
    } else {
        return names[6];
    }

    // Only change code above this line
    }

    golfScore(5, 4);
