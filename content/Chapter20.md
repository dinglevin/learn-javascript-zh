# 第二十章·服务端代码

**Server-side code** refers to the code that runs on a *web server* rather than in a user's web browser. It is responsible for processing requests from clients (typically web browsers) and generating dynamic web pages or providing data to the client.

**Client-side code** refers to the code that runs in a user's *web browser* rather than on a web server. It is responsible for generating the user interface and handling user interactions. Client-side code is typically written in JavaScript and is executed by the browser.

## Why do we need server-side code?

Server-side code is essential in web development for several reasons:

- **Security**: Server-side code is not visible to the user, so it is more secure than client-side code. 
- **Performance**: Server-side code can be used to perform computationally expensive tasks, such as data processing, without affecting the user's experience.
- **Data Storage**: Server-side code can be used to store data in a database, which can then be accessed by the client-side code.
- **User Authentication**: Server-side code can be used to authenticate users and restrict access to certain parts of the website.
- **Dynamic Content**: Server-side code can be used to generate dynamic web pages, which can be customized for each user.

## Server-side vs. Client-side

The differences are summarized in the table below:

| Server-side Code | Client-side Code |
| ----------- | ----------- |
| Runs on a web server | Runs in a web browser |
| Has access to server resources (file system, databases, etc.). | Has access to client resources (cookies, local storage, etc.). |
| Can be written in a variety of languages (PHP, Python, Ruby, Java, C#, etc.). | Can only be written in JavaScript. |
| May use server-side rendering (SSR) to generate HTML on the server. | Uses client-side rendering (CSR) to generate HTML in the browser. |
| Better for SEO as content is readily available for search engines. | Worse for SEO as content is not readily available for search engines. |
| Can leverage caching and Content Delivery Networks (CDNs) for performance. | Limited control over caching, relies on browser cache. |

## Why use JavaScript for server-side code?

Unlike client-side code, which can only be written in JavaScript, server-side code can be written in a variety of languages, including PHP, Python, Ruby, Java, C#, and many more. So why use JavaScript for server-side code? There are several reasons:

- **Unified Language**: Developers can use the same language and programming paradigms throughout the entire application stack, which can lead to code reusability and easier collaboration among front-end and back-end developers.

- **Large Ecosystem**: JavaScript has a vast ecosystem of libraries and packages available through npm (Node Package Manager). This rich ecosystem simplifies the development process by providing pre-built modules for various functionalities, from server routing to database connectivity.

- **JSON**: JavaScript Object Notation (JSON) is a popular data format that is used to transmit data between a server and a web application. JSON is based on JavaScript, so it is easy to work with JSON data in JavaScript.

Up next, we will learn how to use JavaScript for server-side code with Node.js and how to use Server Side Rendering (SSR) to generate HTML on the server.

In this chapter, we will explore following topics:
* [Node.js](./nodejs.md)
* [Server Side Rendering (SSR)](./server-side-rendering.md)

# Node.js

**Node.js** is a JavaScript runtime environment that allows developers to run JavaScript code outside of a web browser. It is built on top of the V8 JavaScript engine, which is the same engine used by Google Chrome. Node.js is open-source and cross-platform, which means it can run on Windows, macOS, and Linux.

## Node.js is not a programming language

Many people mistakenly believe that Node.js is a programming language. This is not true. Node.js is a JavaScript runtime environment, which means it provides an environment for JavaScript code to run. It is not a programming language itself.

Node.js is **not** the only JavaScript runtime environment. There are many others, including Deno, Nashorn, and most recently, Bun. But Node.js is by far the most popular and widely used JavaScript runtime environment.

## Getting started with Node.js

To get started with Node.js, you will need to install it on your computer. You can download the latest version of Node.js from the official website at [nodejs.org](https://nodejs.org/en/). Once you have downloaded and installed Node.js, you can verify the installation by running the following command in your terminal:

```bash
node --version
```

This should print the version number of Node.js like this:

```bash
v20.7.0
```
## Node.js REPL

REPL is a command line interface that stands for Read Evaluate Print Loop, which enables you to run code from the terminal. To get started, type the following command into your terminal:

```bash
node
```
Once you enter this prompt, you can run code, like this:

```js
> console.log("Hello World")
```
You can leave the REPL by typing CTRL + d

## Writing your first Node.js program

Now that you have installed Node.js, let's write our first Node.js program. Create a new file called `hello.js` and add the following code:

```js
console.log('Hello World!');
```

To run this program, open your terminal and navigate to the directory where you saved the `hello.js` file. Then run the following command:

```bash
node hello.js
```

This should print the following output:

```bash
Hello World!
```

## Writing a simple web server using Express and Node.js

Express is a popular web framework for Node.js. It provides a simple and elegant API for building web applications. Let's use Express to create a simple web server that will respond to HTTP requests with a "Hello World!" message.

First, we need to initialize npm by running npm init.

```bash
npm init
```

Then, install express

```bash
npm install express
```

This will install Express and all its dependencies. Once the installation is complete, create a new file called `server.js` and add the following code:

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000, () => {
  console.log('Server is listening on port 3000');
});
```

This code creates a new Express application and defines a route for the root path (`/`). When a request is made to this route, the server will respond with a "Hello World!" message.

To run this program, open your terminal and navigate to the directory where you saved the `server.js` file. Then run the following command:

```bash
node server.js
```

This should print the following output:

```bash
Server is listening on port 3000
```

Now open your web browser and go to [http://localhost:3000](http://localhost:3000). You should see a "Hello World!" message.


# Server Side Rendering (SSR)

Normally, when a user visits a website, the browser sends a request to the server, which responds with HTML, CSS, and JavaScript. But with libraries like *React* and *Vue*, the server only sends a blank HTML page along with a JavaScript file. The JavaScript file then renders the page in the browser. This is called **Client Side Rendering (CSR)**.

**Server Side Rendering (SSR)** is a technique where the server processes the request and generates the HTML on the server from the React or Vue components. The server then sends the generated HTML to the browser, which can then render the page without having to wait for the JavaScript to load.

## Why use SSR?

There are several advantages to using SSR over CSR:

- **Better for SEO**: Search engines can crawl and index the content of your website more easily if it is rendered on the server. This can lead to better search engine rankings and more traffic from search engines.

- **Faster initial page load**: Since the HTML is generated on the server, the browser does not have to wait for JavaScript to load before rendering the page. This can lead to a faster initial page load time.

- **Better performance on low-end devices**: Since the HTML is generated on the server, the browser does not have to do as much work to render the page. This can lead to better performance on low-end devices, such as mobile phones and tablets.

## Disadvantages of SSR

There are also some disadvantages to using SSR:

- **More complex development process**: SSR requires more work on the server side, which can make the development process more complex.

- **More server resources**: SSR requires more server resources, which can lead to higher hosting costs.

- **Limited client-side functionality**: SSR does not allow you to use client-side libraries, such as jQuery or Bootstrap, since they are not available on the server.

## How to implement SSR?

Each library has its own way of implementing SSR. For example, for React, you can use [Next.js](https://nextjs.org/) or [Gatsby](https://www.gatsbyjs.com/). For Vue, you can use [Nuxt.js](https://nuxtjs.org/). For Svelte you can use [SvelteKit](https://kit.svelte.dev/).
