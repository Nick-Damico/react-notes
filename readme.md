# React Notes From Learn.co and Codecademy

## JSX 101

### What is JSX?
JSX is a syntax extension for JavaScript. It was created to be used with React. Jsx code looks like HTML, but its not.

It is also not valid JavaScript which means web browsers cannot read it. If a JavaScript file contains JSX code, then that file will have to be compiled. This means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

### JSX Elements

A basic unit of JSX is called a JSX element.
```JavaScript
<h1>Hello world</h1>
```
**This only looks like HTML, It IS NOT. It's a JSX element and must be compiled down to Browser readable JavaScript first**

*JSX Elements* are treated as JavaScript expressions. They can go anywhere a JS expression can go.

This means they can:
  - saved to a variable
  - passed to a function
  - stored in an object as a value.
  - stored in an Array

**Examples**
```JavaScript
const navBar = <nav>I am a nav bar</nav>;
```

```JavaScript
const myTeam = {
center: <li>Benzo Walli</li>,
powerForward: <li>Rasha Loa</li>,
smallForward: <li>Tayshaun Dasmoto</li>,
shootingGuard: <li>Colmar Cumberbatch</li>,
pointGuard: <li>Femi Billon</li>
};
```
