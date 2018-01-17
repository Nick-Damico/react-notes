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

#### Attributes in JSX

  JSX elements have attributes, think of attributes like for HTML elements.

  A JSX attribute is written using HTML-like syntax

    - a name
    - followed by an equals sign
    - followed by a value

  ```JavaScript
  <a href="http://www.nicholasdamico.net">FullStack Developer</a>

  const title = <h1 id="mainTitle">Intro to React</h1>;
  ```

  A JSX element can have many attributes like an HTML element:
  ```JavaScript
  const dogImg = <img src="img/doggy.png" alt="pic of my puppy" width="500px" height="500px" />;
  ```

### Nesting JSX

You nest JSX elements inside of each other.

```JavaScript
<a href="http://example.com">
  <h1>Logo</h1>
</a>
```

These can be saved to variables as well

```JavaScript
const logo = (
  <a href="https://example.com">
    <h1>
      Company Logo
    </h1>
  </a>
);
```

#### JSX NESTING RULES

- JSX elements which are longer then one line must be wrapped in a set of parentheses like the code above.
- JSX must have exactly one outermost element. This means if you have a multi-line expression or multiple JSX expressions they must contain a single out element.

**Valid JSX**
```JavaScript
const paragraph = (
  <div id="blog">
    <h2>Post Header</h2>
    <p>Post body</p>
  </div>
)
```

**Invalid JSX**
```JavaScript
const paragraph = (
  <h2>Post Header</h2>
  <p>Post body</p>
)
```


### JSX Rendering

Rendering a JSX element means to make it appear on screen.

To render an element on screen we use the following code:

```JavaScript
ReactDOM.render(<h1>Main Heading</h1>, document.getElementById('app'));
```

#### ReactDOM

  ReactDOM is a variable in the above code that references the ReactDOM library, this library contains several React-specific methods, all of which deal with the DOM in one way or another.

  *.render()* is the method we will focus on here. It is the most common way to render JSX.
  - it takes JSX expressions creates a corresponding tree of DOM nodes, and adds that tree to the DOM. That is how they appear on screen.

  *Breaking Down the statement Below:*
  ```JavaScript
  ReactDOM.render(
    <h1>Main Heading</h1>,
    document.getElementById('app')
  );
  ```

  - First, we call the ReactDOM.render() method. The first argument must be a JSX element or a JSX Component which returns a JSX expression.
  - Secondly, the second argument passed is a reference to the DOM node you want to append the JSX expression into, above it is a HTML element of `<div id="app"></app>` inside the DOM.


#### Passing a Variable to ReactDOM.render()

The first argument should evaluate to a JSX expression, it doesn't have to literally be one.

```JavaScript
const toDoList = (
  <ol>
    <li>Learn HTML and CSS</li>
    <li>Learn JavaScript</li>
    <li>Learn React.js</li>
  </ol>
)

ReactDOM.render(
  toDoList,
  document.getElementById('app')
);
```

**IMPORTANT**
  One of the special things about React is that the ReactDOM.render() only updates elements that have changed. This is what makes it so fast and efficient. React only updates necessary DOM element changes, no wiping out all existing elements in a DOM node to update only a small change in data. This is accomplished because of something called the `virtual DOM`.https://www.codecademy.com/articles/react-virtual-dom

## JSX Advanced

#### class vs className

Grammer in JSX is mostly the same as in HTML, but there can be conflicts between keywords used in HTML and JavaScript. One of those being the keyword `class`.

In HTML
```HTML
  <h1 class="greeting">Hello world</h1>
```

Since `class` is a reserved keyword in JavaScript and JSX is compiled to JavaScript this will cause an error, so in JSX we use the keyword `className` to set a class name on a JSX element which will compile to `class`.

JSX valid
```JavaScript
  <h1 className="greeting">Hello world</h1>
```
