# ReactJS-Notes
___
## Intro To JSX

JSX produces React “elements”.

```jsx
const element = <h1>Hello, world!</h1>;
```

### JSX is an Expression Too
After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

This means that you can use JSX inside of `if` statements and `for` loops, assign it to variables, accept it as arguments, and return it from functions.

```jsx
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  
  return <h1>Hello, Stranger.</h1>;
}
```

### Specifying Attributes with JSX
You may use quotes, `" "`, to specify string literals as attributes.
```jsx
const element = <div tabIndex="0"></div>;
```
You may also use curly braces, `{ }`, to embed a JavaScript expression in an attribute.
```jsx
const element = <img src={user.avatarUrl}></img>;
```

### Specifying Children with JSX
If a tag is empty, you may close it immediately with `/>`, like XML.
```jsx
const element = <img src={user.avatarUrl} />;
```
JSX tags may contain children.
```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

### JSX Represents Objects
Babel compiles JSX down to `React.createElement()` calls.

The following two code snippets are identical under the hood.
```jsx
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```jsx
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
`React.createElement()` creates objects called "_React elements_".
```jsx
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```
Think of these objects like descriptions of what you want to see on the screen. 

React reads these objects and uses them to construct the DOM and keep it up to date.

___

## Rendering Elements
Elements are the smallest building blocks of React apps.

An element describes what you want to see on the screen
```jsx
const element = <h1>Hello, world</h1>;
```
Unlike browser DOM elements, React elements are plain objects, and are cheap to create. 

### Rendering an Element into the DOM
Let’s say there is a `<div>` somewhere in your HTML file.
```html
<div id="root"></div>
```
To render a React element into a root DOM node, pass both to `ReactDOM.render()`.
```jsx
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

### Updating the Rendered Element
React elements are `immutable`. Once you create an element, you can’t change its children or attributes.

With our knowledge so far, the only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`.

Consider this ticking clock example.
```jsx
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);    // It calls ReactDOM.render() every second from a setInterval() callback.
```




