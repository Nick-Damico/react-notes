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
  const age = 22;
  const barAdmission = (
    <ul>
      <h2>You are aloud to:</h2>
      { age < 18 && <li>Buy Food</li> }
      { age > 21 && <li>Buy Drinks</li> }
    </ul>
  )
```

Result of code above:
```HTML
  <ul>
    <h2>You are aloud to:</h2>
    <li>Buy Food</li>
    <li>Buy Drinks</li>
  </ul>
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

### Keys

When you make a list in JSX, sometimes your list will need to include something called keys:
```JavaScript
<ul>
  <li key="li-01">Example1</li>
  <li key="li-02">Example2</li>
  <li key="li-03">Example3</li>
</ul>
```

A key is a JSX attribute. The attribute's name is key. The attribute's value should be something unique, similar to an id attribute.

keys don't do anything that you can see! React uses them internally to keep track of lists. If you don't use keys when you're supposed to, React might accidentally scramble your list-items into the wrong order.

Not all lists need to have keys. A list needs keys if either of the following are true:

- The list-items have memory from one render to the next. For instance, when a to-do list renders, each item must "remember" whether it was checked off. The items shouldn't get amnesia when they render.

- A list's order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don't have to worry about keys. If you aren't sure then it never hurts to use them!

### Writing React code without JSX!!

This isn't common practice among developers, but some developers are disturbed by mixing languages together and so they choose to write their React code the way it gets compiled instead of using JSX, which makes it much more difficult for others to read... and in my opinion code should be easy to read and understand that is good code, making code vague and near impossible to understand is not so good.

With JSX:
```JavaScript
  const hello = <h1>Hello All</h1>;
```

Without JSX:
```JavaScript
  const h1 = React.createElement(
    "h1",
    {},
    "Hello All"
  );
```

# React Components

React applications are made out of components.

A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML to the DOM.

```JavaScript
  import React from 'react';
  import ReactDOM from 'react-dom';

  class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
  };

  ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
  );
```

### Breaking Down the Above code...

Bringing in the React library

```JavaScript
  import React from 'react';
```

This above line of code creates a new variable, `React`, this variables value is the imported JavaScript object:

```JavaScript
// create a variable named React:
import React from 'react';
  // evaluate this variable and get a particular,
  imported JavaScript object:
  React // { imported object properties here... }
```

This `React` imported object contains methods that you need in order to use React. The object is called the `React Library`.

So just remember if you are writing React Code this will need to be in each file at the top. `import React from 'react';`.

#### So What methods do you get from React object?

 We have encountered a few so far:
 - React.createElement() - This is for creating React elements without the JSX elements.This is what gets created when JSX is compiled.
 - Include more later.


### Import ReactDOM.

  So we have the `React` library thanks to `import React from 'react';`. But something is amiss... We can write React code but how do we render it to the `DOM`?

  ```JavaScript
    import ReactDOM from 'react-dom';
  ```

  This import statement works much the same as the one above with React library but here its a different library object `React DOM` which gives us access to methods for manipulating the *DOM*.

  You are already familiar with one of them `ReactDOM.render()`;

  So the library imported from `react` have methods for writing **React**, the library imported from `react-dom` deal with Rendering the React code to the DOM.

  **To clarify:** the DOM is used in React applications, but it isn't part of React. After all, the DOM is also used in countless non-React applications. Methods imported from 'react' are only for pure React purposes, such as creating components or writing JSX elements.


## Create A Component class

Once again, Component? Small, reusable chunk of code that has one job, rendering some HTML.

One More thing, A **Component** must come from a component class.

Think inheritance, We are inheriting from a previously defined class and what we end up creating is a *subclass*.

`React.Component` is a JavaScript class. This is the class we inherit from:

```JavaScript
  class YourComponentClass extends React.Component { }
```

**React Components are BLUE PRINTS or Factories whichever way is easier to rememeber! We create instances of this object, instances of this class get rendered to the DOM**

### Name a Component Class

When you declare a new component class, you need to give that component class a name. Component class variables **names must begin with captial letters!**

This first letter class names adhere to JavaScript ES2015 Class syntax.

#### Recap on Classes INTRO.
- Import React from 'react' creates a JavaScript object. This object contains properties that are needed to make React work, such as React.createElement() and React.Component.

- Import ReactDOM from 'react-dom' creates another JavaScript object. This object contains methods that help React interact with the DOM, such as ReactDOM.render().

- By subclassing React.Component, you create a new component class. This is not a component! A component class is more like a factory that produces components. When you start making components, each one will come from a component class.

- Whenever you create a component class, you need to give that component class a name. That name should be written in UpperCamelCase. In this case, your chosen name is MyComponentClass.

```JavaScript
  import React from 'react';
  import ReactDOM from 'react-dom';

  class MyComponentClass extends React.Component {
    // Body of Class, think instructions for all classes instantiated from it.
  }
```

The body of the class will act as set of instructions explaining to your component class how it should build a React Component.

body example:
```JavaScript
  {
    render() {
      return <h1>Hello world</h1>;
    }
  }
```

The instructions must adhere to *ES2015 Class syntax*. There is only one property that is required: a render method. The render must return and it must return a *JSX element*!. And if multi-line it must adhere to what rules??
 - If multi-line, it must be surrounded by parentheses.
 - And the return can only return 1 element, so it must be enclosed with an single *JSX element*, like a `<div>//JSX</div>`.

### Creating a Component Instance.

  From code above, we have a component class called, `MyComponentClass`:

  ```JavaScript
  import React from 'react';
  import ReactDOM from 'react-dom';

  class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
  }

  ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
  );
  ```

  We instantiate it in the `ReactDOM.render()`, if you rememeber correctly what is the first argument? A JSX Element! And what does the `MyComponentClass` render()? a JSX Element level one header of `Hello World`.

  **Important** We don't pass it in like before when dealing with a variable, we use a new syntax:

  ```JavaScript
  ReactDOM.render(
    <MyComponentClass />,
    document.getElementById('app')
  )
  ```

  JSX elements can be either HTML-like, or component instances. JSX uses capitalization to distinguish between the two! That is the React-specific reason why component class names must begin with capital letters. 
