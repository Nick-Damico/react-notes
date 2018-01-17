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

### class vs className
  - Grammer in JSX is mostly the same as in HTML, but there can be conflicts between keywords used in HTML and JavaScript. One of those being the keyword `class`.

    In HTML
    ```HTML
      <h1 class="greeting">Hello world</h1>
    ```

    This is because JSX gets translated into JavaScript, and class is a reserved word in JavaScript.
    When JSX is rendered, JSX className attributes are automatically rendered as class attributes.

    JSX valid
```JavaScript
  <h1 className="greeting">Hello world</h1>
```

### Self Closing Tags

If an HTML element uses a self closing tag in `CSS3` adding a forward slash `/>` to close an element is no longer needed, but in JSX it is still required

  Invalid
  ```JavaScript
    <input type='submit' >
  ```

  Valid
  ```JavaScript
    <input type='submit' />
  ```


### JavaScript In Your JSX In Your JavaScript

  How to write JavaScript expressions within our JSX.

  - First, any code between JSX element tags will be considered JSX text.
  - If you want to have code that is evaluated as JavaScript you'll need to write code that says, "Even though I am located in between JSX tags, treat me like ordinary JavaScript and not like JSX."

  To write this code that is evaluated as JavaScript within a JSX state it must be wrapped between curly braces.

```JavaScript
  ReactDOM.render(
    <h1>Do Math 3 + 2 = {2+3}</h1>
  )
```

### Variables in your JSX

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

This means you can access variables while inside of a JSX expression, even if those variables were declared on the outside because they share lexical scope and outside of those functions they can be found up the scope chain.

```JavaScript
  // Declare Variables
  const name = 'Nick';

  // Access your variable
  // from inside of a JSX expression
  const greet = <h1 className="greeting">Hi, {name}</h1>;
```


### Setting Attributes with Variables in JSX

It's common to set the attributes of JSX elements with a variable that references an array or similar object.

```JavaScript
  // Use variable to set the width and height and src
  const imgSize = {
    width: '250px',
    height: '250px'
  }

  const imgSrc = 'images/kitty.jgp';

  const catImg = (
    <img
    src={imgSrc}
    width={imgSize[width]}
    height={imgSize[height]}/>
  );
```

### Event Listeners in JSX

JSX elements can have event listeners, just like HTML element can. Programming in React means constantly working with event listeners.

This is done with a special attribute of which typically starts with `on` and describes the type of event it will be listening for such as: `onClick`, `onSubmit`, `onMouseOver`.

 You can see a list of valid event names here https://reactjs.org/docs/events.html#supported-events.

 ```JavaScript
   function modalFunc() {
     alert('Model is now open');
   }

   <button onClick={modalFunc}>Modal</button>
 ```


### JSX Conditionals: (If statements don't work like you think).

You can NOT inject an `if` statement inside of a JSX expression.

This is no good:
```JavaScript
  (
    <h1>
      {
        if (user.loggedIn) {
          'Welcome to the Store'
        } else {
          'Please, log in.'
        }
      }
    </h1>
  )
```

The reason is due to how JSX is compiled, but that is a deep subject, so if we can't inject `if/else` statements.. How do we write conditionals?

**Conditional Option 1**

Write the `if` statement outside of the JSX, not inside of it.

```JavaScript
  if (user.loggedIn) {
    message = <h1 className="greeting">Welcome User!</h1>;
  } else {
    message = <h1 className="greeting">Please log In.</h1>;
  }

  ReactDOM.render(
    message,
    document.getElementById('app')
  );
```

**Ternary statements Option 2**

Ternary statements can be inside a JSX expression.

```JavaScript
    const greeting = (
      <h1>
        {user.loggedIn ? 'Welcome User' : 'Please log in.'}
      </h1>
    )
```

**JSX Conditionals: &&**

These evaluate in an unexpected way from how we typically use them in JavaScript as Logical Operators where we decided if a both JavaScript statements evaluate to either `true && true` or `false && false`.

`&&` JSX conditionals work best in conditions that sometimes do an action, but other times do nothing at all.

example:

```JavaScript
  const barAdmission = (
    <ul>
      <h2>You are aloud to:</h2>
      { age < 18 && <li>Buy Food</li> }
      { age > 21 && <li>Buy Drinks</li> }
    </ul>
  )
```
Every time that you see && in this example, either some code will run, or else no code will run.


### .map in JSX

The array method `.map()` comes up often in React. If you want to create a list of JSX elements, then `.map()` is often your best bet. It can look odd at first:


```JavaScript
  const strings = ['Home', 'About', 'Projects' 'Contact'];

  const navItems = strings.map(string => <a href={'#' + string}>string</a>);
  ReactDOM.render(
      <nav className="mainNav">{navItems}</nav>,
      document.getElementById('app')
  )

```
