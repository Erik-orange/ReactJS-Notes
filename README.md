# ReactJS-Notes
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
