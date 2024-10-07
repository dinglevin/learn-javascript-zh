---
chapter: 1
pageNumber: 9
description: JavaScript is a high-level, interpreted, and dynamically-typed programming language primarily used for web development. It is one of the core technologies used to create interactive and dynamic websites and web applications. 
---
# 第一章·介绍

{% tooltips %}
计算机在当今世界中非常普遍，因为它们能够快速准确地执行各种任务。它们被广泛应用于多个行业，如商业、医疗、教育和娱乐，已经成为许多人日常生活中不可或缺的一部分。除此之外，计算机还用于执行复杂的科学和数学计算、存储和处理大量数据，以及与全球各地的人进行交流。
@@
Computers are common in today's world, as they are able to perform a wide variety of tasks quickly and accurately. They are used in many different industries, such as business, healthcare, education, and entertainment, and have become an essential part of daily life for many people. Besides this, they are also used to perform complex scientific and mathematical calculations, to store and process large amounts of data, and to communicate with people around the world.
{% endtooltips %}

{% tooltips %}
编程是为计算机创建一组指令（称为程序）的过程。编写程序有时可能会非常繁琐和令人沮丧，因为计算机非常精确，需要特定的指令才能完成任务。
@@
Programming involves creating a set of instructions, called a program, for a computer to follow. Writing a program can be tedious and frustrating at times because computers are very precise and need specific instructions in order to complete tasks.
{% endtooltips %}

![Intro Page](../.gitbook/assets/intro.png)

{% tooltips %}
编程语言是用于向计算机发出指令的人造语言。它们用于大多数编程任务，基于人类之间的交流方式。像人类语言一样，编程语言允许通过组合单词和短语来表达新的概念。有趣的是，与计算机进行最有效的交流方式涉及使用与人类语言相似的语言。
@@
Programming languages are artificial languages used to give instructions to computers. They are used in most programming tasks and are based on the way humans communicate with each other. Like human languages, programming languages allow words and phrases to be combined to express new concepts. It is interesting to note that the most effective way to communicate with computers involves using a language that is similar to human language.
{% endtooltips %}

{% tooltips %}
过去，主要与计算机交互的方式是通过基于语言的接口，如 BASIC 和 DOS 提示符。这些接口大多已被视觉界面取代，后者更易于学习但灵活性较低。然而，像 _JavaScript_ 这样的计算机语言仍在使用中，并且可以在现代 Web 浏览器和大多数设备上找到。
@@
In the past, the primary way to interact with computers was through language-based interfaces like BASIC and DOS prompts. These have been largely replaced by visual interfaces, which are easier to learn but offer less flexibility. However, computer languages like _JavaScript_ are still in use and can be found in modern web browsers and on most devices.
{% endtooltips %}

{% tooltips %}
JavaScript（_简称 JS_）是一种编程语言，用于在开发网页、游戏、应用程序甚至服务器时创建动态交互。JavaScript 起源于 1990 年代开发的网页浏览器 Netscape，如今是最著名和使用最广泛的编程语言之一。
@@
JavaScript (_JS for short_) is the programming language that is used to create dynamic interaction while developing webpages, games, applications, and even servers. JavaScript started at Netscape, a web browser developed in the 1990s, and is today one of the most famous and used programming languages.
{% endtooltips %}

{% tooltips %}
最初，它是为让网页变得生动而创建的，只能在浏览器中运行。而现在，任何支持 JavaScript 引擎的设备都可以运行它。JavaScript 中提供了标准对象，如 [Array](./arrays/README.md)、[Date](./date-and-time.md) 和 [Math](./numbers/math.md)，以及运算符、控制结构和语句。_客户端 JavaScript_ 和_服务器端 JavaScript_ 是核心 JavaScript 的扩展版本。
@@
Initially, it was created for making webpages alive and was able to run only on a browser. Now, it runs on any device that supports the JavaScript engine. Standard objects such as [Array](./arrays/README.md), [Date](./date-and-time.md), and [Math](./numbers/math.md) are available in JavaScript, as well as operators, control structures, and statements. _Client-side JavaScript_ and _Server-side JavaScript_ are the extended versions of core JavaScript.
{% endtooltips %}

{% tooltips %}
* _客户端 JavaScript_ 使网页和客户端浏览器的增强和操作成为可能。响应用户事件，如鼠标点击、表单输入和页面导航，便是其一些示例。
* [_服务器端 JavaScript_](./server-side/README.md) 则允许访问服务器、数据库和文件系统。
@@
* _Client-side JavaScript_ enables the enhancement and manipulation of web pages, and client browsers. Responses to user events such as mouse clicks, form input, and page navigation are some of its examples.
* [_Server-side JavaScript_](./server-side/README.md) enables access to servers, databases, and file systems.
{% endtooltips %}

{% tooltips %}
JavaScript 是一种解释型语言。在运行 JavaScript 时，解释器逐行解释并执行代码。现代浏览器使用[即时编译器（JIT 编译器）](https://hacks.mozilla.org/2017/02/a-crash-course-in-just-in-time-jit-compilers/)来编译，将 JavaScript 编译成可执行的字节码。
@@
JavaScript is an interpreted language. While running Javascript an interpreter interprets each line and runs it. The modern browser uses [Just In Time (JIT)](https://hacks.mozilla.org/2017/02/a-crash-course-in-just-in-time-jit-compilers/) compilers for compilation, which compiles JavaScript into executable bytecode.
{% endtooltips %}

{% tooltips hintStyle="info" %}
JavaScript 最初的名字是 "LiveScript"。
@@
"LiveScript" was the initial name given to JavaScript.
{% endtooltips %}

{% tooltips %}
### 代码、如何处理以及如何排版
@@
Code, and what to do with it and Typographic conventions
{% endtooltips %}

{% tooltips %}
_代码_是构成程序的书面指令。在这里，许多章节包含大量代码，阅读和编写代码是学习编程的重要组成部分。你不应该只是快速浏览例子，而是要认真阅读并尝试理解它们。刚开始时这可能会有些困难，但通过练习，你会有所进步。练习题也是如此——确保在假设你理解之前，实际尝试写出解决方案。将你的解决方案在 JavaScript 解释器中运行也是有帮助的，这样可以让你查看代码是否正确工作，并鼓励你进行实验，超越练习内容。
@@
_Code_ is the written instructions that make up a program. Here, many chapters contain a lot of code, and it is important to read and write code as part of learning how to program. You should not just quickly scan the examples - read them carefully and try to understand them. This may be difficult at first, but with practice, you will improve. The same goes for the exercises - make sure you actually try to write a solution before assuming you understand them. It is also helpful to try running your solutions to the exercises in a JavaScript interpreter, as this will allow you to see if your code is working correctly and may encourage you to experiment and go beyond the exercises.
{% endtooltips %}

{% tooltips %}
在这里，使用等宽字体书写的文本表示程序的元素。这可以是一个独立的片段，也可以是对附近程序部分的引用。程序，如下所示，都是这样书写的：
@@
Here, text is written in a monospaced font represents elements of a program. This can be a self-contained fragment or a reference to part of a nearby program. Programs, like the one shown below, are written in this way:
{% endtooltips %}

```javascript
const numbers = [45, 4, 9, 16, 25];
let txt = "";
for (let x in numbers) {
  txt += numbers[x];
}
```

{% tooltips %}
有时，程序的预期输出会写在代码后面，前面加上两个斜杠和_Result_，如下所示：
@@
Sometimes, the expected output of a program is written after it, preceded by two slashes with a _Result_, like this:
{% endtooltips %}

```javascript
console.log(txt);

// Result: txt = '45491625'
```
