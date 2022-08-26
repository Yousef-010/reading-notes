# Reading 32 : React 2 


> React - Conditional Rendering
- Conditional rendering in React works the same way conditions work in JavaScript.
- Example
```
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}
```
- Ternary if statment ` condition ? true : false.`
- Logical operation like `&& , ||`


> React - Lists & Keys
- Rendering Multiple Components
  - You can build collections of elements and include them in JSX using curly braces {}.
  - Example 
```
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
```
- Keys 
  - Keys help React identify which items have changed, are added, or are removed
  - Keys should be given to the elements inside the array to give the elements a stable identity
  - Keys used within arrays should be unique among their siblings
  - Keys serve as a hint to React but they don’t get passed to your components



> React - Forms
- In React, mutable state is typically kept in the state property of components, and only updated with setState().
- you can use the values inside the forms inputs by targeting their name to get th values 
  - `event.target.name of the element.value`
- Alternatives to Controlled Components
  - It can sometimes be tedious to use controlled components,because you need to write an event handler for every way your data can change and pipe all of the input state through a React component.
  - This can become particularly annoying when you are converting a preexisting codebase to React, or integrating a React application with a non-React library.
  - In these situations, you might want to check out uncontrolled components, an alternative technique for implementing input forms.
- Fully-Fledged Solutions 
  - If you’re looking for a complete solution including validation, keeping track of the visited fields, and handling form submission
  - `Formik` is one of the popular choices. 
    


> React - Lifting State
- every component in React has its own state.
- Because of this sometimes data can be redundant and inconsistent.
- by Lifting up the state we make the state of the parent component as a single source of truth and pass the data of the parent in its children.
- Time to use Lift up the State: If the data in “parent and children components” or in “cousin components” is Not in Sync



> React - Composition vs Inheritance
- Containment
  - Some components don’t know their children ahead of time.
  - This is especially common for components like `Sidebar` or `Dialog` that represent generic `boxes`
- Specialization 
  - achieved by composition, where a more “specific” component renders a more “generic” one and configures it with props
- Inheritance
  - Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way.
  - reuse non-UI functionality between components
    - extracting it into a separate JavaScript module
    - The components may import it and use that function, object, or a class, without extending it


> Thinking in React
- Steps : 
  - Break The UI Into A Component Hierarchy 
    - The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names.
  - Build A Static Version in React
    - The easiest way is to build a version that takes your data model and renders the UI but has no interactivity.
  - Identify The Minimal (but complete) Representation Of UI State
    - it is the time to think of the minimal set of mutable state that your app needs 
  - Identify Where Your State Should Live
    - dentify which component mutates, or owns, this state
  - Add Inverse Data Flow
    -  support data flowing the other way: the form components deep in the hierarchy need to update the state in `FilterableProductTable`.



> Resources 
- https://reactjs.org/docs/conditional-rendering.html
- https://reactjs.org/docs/lists-and-keys.html
- https://reactjs.org/docs/forms.html
- https://reactjs.org/docs/lifting-state-up.html
- https://reactjs.org/docs/composition-vs-inheritance.html
- https://reactjs.org/docs/thinking-in-react.html