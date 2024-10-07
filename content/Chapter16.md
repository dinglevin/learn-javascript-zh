# 第十六章·浏览器对象模型(BOM)

The browser object model lets us interact with the browser window. The `window` object represents the browser's window and is supported by all browsers.

Object `window` is the default object for a browser, so we can specify `window` or call directly all the functions.

```javascript
window.alert("Welcome to Learn JavaScript");  

alert("Welcome to Learn JavaScript")
```

In this chapter, we are going to talk about various properties and methods of browser object model.
* [Cookies](./cookies.md)
* [History](./history.md)
* [Location](./location.md)
* [Navigator](./navigator.md)
* [Popup](./popup.md)
* [Screen](./screen.md)
* [Window](./window.md)


# Cookies 🍪

Cookies are pieces of information that are store on a computer and can be accessed by the browser.

Communication between a web browser and the server is stateless meaning that it treats each request independently. There are cases where we need to store user information and make that information available to the browser. With cookies, information can be fetched from the computer whenever it is required.

Cookies are saved in name-value pair

```javascript
book = Learn JavaScript
```

The `document.cookie` property is used to create, read and delete cookies. Creating cookie is pretty easy you need to provide the name and value

```javascript
document.cookie = "book=Learn JavaScript";
```

By default, a cookie gets deleted when the browser is closed. To make it persistent, we need to specify the expiry date (in UTC time).

```javascript
document.cookie = "book=Learn JavaScript; expires=Fri, 08 Jan 2022 12:00:00 UTC";
```

We can add a parameter to tell which path the cookie belongs to. By default, the cookie belongs to the current page.

```javascript
document.cookie = "book=Learn JavaScript; expires=Fri, 08 Jan 2022 12:00:00 UTC; path=/";
```

Here is a simple example of a cookie.

```javascript
let cookies = document.cookie;
// a simple way to retrieve all cookie.

document.cookie = "book=Learn JavaScript; expires=Fri, 08 Jan 2022 12:00:00 UTC; path=/";
// setting up a cookie
```

# History

When we open a web browser and surf a web page it creates a new entry in the history stack. As we keep navigating to different pages new entries get pushed into the stack. 

To access the history object we can use

```javascript
window.history
// or
history
```

To navigate  between the different history stack we can use   `go()` , `forward()` and  `back()`methods of **history** object.  

1. **go\(\)**: It is used to navigate the specific URL of the history stack.

   ```javascript
   history.go(-1); // moves page backward
   history.go(0);  // refreshes the current page
   history.go(); // refreshes the current page
   history.go(1) // moves page forward
   ```

   > _**Note:**_ the current  page position in history stack is  **0**.

2. **back\(\)** : To navigate page backward we use `back()` method.

   ```javascript
   history.back();
   ```

3. **forward\(\)**: It loads the next list in the browser history. It is similar to clicking the forward button in the browser.

   ```javascript
   history.forward();
   ```

# Location

The `location` object is used to retrieve the current location (URL) of the document and provides different methods to manipulate document location. One can access the current location by

```javascript
window.location
//or
document.location
//or
location
```

> _**Note**_: `window.location` and `document.location` references the same location object.

Let's take an example of the following URL and explore the different properties of `location`

[`http://localhost:3000/js/index.html?type=listing&page=2#title`](http://localhost:8080/js/index.html?type=listing\&page=2#title)

```javascript
location.href //prints current document URL
location.protocol //prints protocol like http: or https:
location.host //prints hostname with port like localhost or localhost:3000
location.hostname //prints hostname like localhost or www.example.com
location.port //prints port number like 3000
location.pathname //prints pathname like /js/index.html
location.search //prints query string like ?type=listing&page=2
location.hash //prints fragment identifier like #title
```

# Navigator

The `window.navigator`  or `navigator`   is a **read-only** property and contains different methods and functions related to the browser.&#x20;

Let's look at a  few examples of navigation.

1.  **navigator.appName**: It gives the name of the browser application

    ```javascript
    navigator.appName; 
    // "Netscape"
    ```

    > _**Note:**_ "Netscape" is the application name for IE11, Chrome, Firefox, and Safari.
2.  **navigator.cookieEnabled**: Returns a boolean value based on the cookie value in the browser.

    ```javascript
    navigator.cookieEnabled;
    //true
    ```
3.  **navigator.platform**: Provides information about the browser operating system.

    ```javascript
    navigator.platform;
    "MacIntel"
    ```

# Popup

Popups are an additional way to show information, take user confirmation, or take user input from additional documents. A popup can navigate to a new URL and send information to the opener window. **Alert box**, **Confirmation box**,  and **Prompt box** are the global functions where we can show the popup information.

1.  **alert()**: It displays information to the user and has an  "**OK**" button to proceed.

    ```javascript
    alert("Alert message example");
    ```
2.  **confirm()**: Use as a dialog box to confirm or accept something. It has "**Ok**" and "**Cancel**" to proceed. If the user clicks "**Ok**" then it returns `true`, if click "**Cancel**" it returns  `false`.&#x20;

    ```javascript
    let txt;
    if (confirm("Press a button!")) {
      txt = "You pressed OK!";
    } else {
      txt = "You pressed Cancel!";
    }
    ```
3.  **prompt()**: Takes user input value with "**Ok"** and "**Cancel"** buttons. It returns `null` if the user does not provide any input value.

    ```javascript
    //syntax 
    //window.prompt("sometext","defaultText");

    let person = prompt("Please enter your name", "Harry Potter");

    if (person == null || person == "") {
      txt = "User cancelled the prompt.";
    } else {
      txt = "Hello " + person + "! How are you today?";
    }
    ```

# Screen

The `screen` object contains the information about the screen on which the current window is being rendered. To access `screen` object we can use the `screen` property of `window` object.

```javascript
window.screen
//or
screen
```

The `window.screen` object has different properties, some of them are listed here:

| Property       | Description                                                                       |
| -------------- | --------------------------------------------------------------------------------- |
| `availTop`     | A read-only property that returns the first pixel from the top that is not taken up by system elements. |
| `availWidth`   | A read-only property that returns the pixel width of the screen excluding system elements. |
| `colorDepth`   | A read-only property that returns the number of bits used to represent colors.    |
| `height`       | Represents the pixel height of the screen.                                         |
| `left`         | Represents the pixel distance of the current screen’s left side.                   |
| `orientation`  | Returns the screen orientation as specified in the Screen Orientation API.         |
| `pixelDepth`   | A read-only property that returns the bit depth of the screen.                     |
| `top`          | Represents the pixel distance of the current screen’s top.                         |
| `width`        | Represents the pixel width of the screen.                                          |

# Window

The `window` object represents the browser window and is supported by the browsers. Global variables, objects, and functions are also part of the window object. 

Global **variables** are **properties** and **functions** are **methods** of the window object.

Let's take an example of the screen properties. It is used to determine the size of the browser window and is measured in pixels.    

* `window.innerHeight` - the inner height of the browser window
* `window.innerWidth` - the inner width of the browser window

> _**Note**_:  `window.document` is same as   `document.location` as  the document object model\(DOM\) is part of window object.

Few examples of the window methods

* `window.open()` - open a new window
* `window.close()` - close the current window
* `window.moveTo()` - move the current window
* `window.resizeTo()` - resize the current window

