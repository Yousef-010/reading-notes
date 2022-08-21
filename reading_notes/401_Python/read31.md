# Readings: React 1 

> ES6 Syntax and Feature Overview 
- ECMAScript 2015, also known as ES6, introduced many changes to JavaScript.
- `let` keyword, which allows for block-scoped variables which cannot be hoisted or redeclared
- `const` keyword, which cannot be redeclared or reassigned, but is not immutable.
- Arrow functions
  - The arrow function expression syntax is a shorter way of creating a function expression
  - Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods.
- `return` keyword is implied and can be omitted if using arrow functions without a block body.
- `class` syntax on top of the prototype-based constructor function.
- `extends` keyword creates a subclass.



> React - Hello World 
- React is a JavaScript library


> React – JSX
- This funny tag syntax is neither a string nor HTML.
- it is a syntax extension to JavaScript
- JSX may remind you of a template language, but it comes with the full power of JavaScript.
- Why JSX?
  - React embraces the fact that rendering logic is inherently coupled with other UI logic
  - Instead of artificially separating technologies by putting markup and logic in separate files,
    - React separates concerns with loosely coupled units called “components” that contain both
  - React doesn’t require using JSX

> Embedding Expressions in JSX 
- Example
```
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```


> React - Rendering Elements
- Elements are the smallest building blocks of React apps.
- To render a React element, first pass the DOM element to `ReactDOM.createRoot()`, then pass the React element to `root.render()`
- Example
```
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```


> React - Components & Props
- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation
- The simplest way to define a component is to write a JavaScript function:
- Example
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
- This function is a valid React component because it accepts a single `props`, `(which stands for properties)`
- Class based example
```
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
- React is pretty flexible but it has a single strict rule:
- **All React components must act like pure functions with respect to their props.**



> React - State & Lifecycle
- we need to add “state” to the `Clock` component
- State is similar to props, but it is private and fully controlled by the component.
- Converting a Function to a Class 
  - Create an ES6 class, with the same name, that extends React.Component.
  - Add a single empty method to it called render().
  - Move the body of the function into the render() method.
  - Replace props with this.props in the render() body.
  - Delete the remaining empty function declaration.
- Using State Correctly 
  - Do Not Modify State Directly
  - State Updates May Be Asynchronous
  - State Updates are Merged
- **Each Clock sets up its own timer and updates independently.**


> React - Handling Events
- Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences 
  - React events are named using camelCase, rather than lowercase.
  - With JSX you pass a function as the event handler, rather than a string.
- Passing Arguments to Event Handlers
- Example
```
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```
- The above two lines are equivalent, and use arrow functions and Function.prototype.bind respectively 
- the e argument representing the React event will be passed as a second argument after the ID
- With an arrow function, we have to pass it explicitly, but with bind any further arguments are automatically forwarded.



> Utility First CSS
- With Tailwind, you style elements by applying pre-existing classes directly in your HTML
- Some examples
  - Tailwind’s `flexbox` and `padding` utilities `(flex, shrink-0, and p-6)` to control the overall card layout
  - The `max-width` and `margin` utilities `(max-w-sm and mx-auto)` to constrain the card width and center it horizontally
  - The `background color`, `border radius`, and `box-shadow` utilities `(bg-white, rounded-xl, and shadow-lg)` to style the card’s appearance
  - The `width` and `height` utilities `(w-12 and h-12)` to size the logo image
  - The `space-between` utilities `(space-x-4)` to handle the spacing between the logo and the text
  - The `font size`, `text color`, and `font-weight` utilities `(text-xl, text-black, font-medium, etc.)` to style the card text
- This approach allows us to implement a completely custom component design without writing a single line of custom CSS. 


> important benefits 
- You aren’t wasting energy inventing class names
- Your CSS stops growing
- Making changes feels safer.
- Designing with constraints
- Responsive design
- Hover, focus, and other states
- **Maintainability concerns** 
  - The biggest maintainability concern when using a utility-first approach is managing commonly repeated utility combinations
  - This is easily solved by extracting components and partials, and using editor and language features like multi-cursor editing and simple loops.


> Resources
- https://www.taniarascia.com/es6-syntax-and-feature-overview/
- https://reactjs.org/docs/introducing-jsx.html
- https://reactjs.org/docs/rendering-elements.html
- https://reactjs.org/docs/components-and-props.html
- https://reactjs.org/docs/state-and-lifecycle.html
- https://reactjs.org/docs/handling-events.html
- https://tailwindcss.com/docs/utility-first

