 
## JavaScript Interview Questions

 **Explain `var`, `let`, and `const`.**
   - `var`: Function-scoped variable declaration, can be re-declared and updated.
   - `let`: Block-scoped variable declaration, cannot be re-declared but can be updated.
   - `const`: Block-scoped variable declaration, cannot be re-declared or updated.

**What are closures in JavaScript?**
   - A closure is a function that retains access to its lexical scope even when the function is executed outside that scope.

 **What is the difference between `==` and `===`?**
   - `==` checks for equality after type coercion.
   - `===` checks for equality without type coercion (strict equality).

**What are promises in JavaScript?**
   - Promises are objects representing the eventual completion or failure of an asynchronous operation, allowing you to handle asynchronous operations more effectively.

**Explain the concept of hoisting in JavaScript.**
   - Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope (function or global scope) before code execution.
 
**What are arrow functions, and how do they differ from regular functions?**
   - Arrow functions are a shorthand syntax for writing functions in ES6. They do not have their own `this` context and cannot be used as constructors.

**Explain the concept of prototypal inheritance in JavaScript.**
    - Prototypal inheritance is a feature in JavaScript where objects can inherit properties and methods from other objects. This is achieved through the prototype chain.

**What is the difference between `call()`, `apply()`, and `bind()`?**
    - `call()`: Invokes a function with a given `this` value and arguments provided individually.
    - `apply()`: Invokes a function with a given `this` value and arguments provided as an array.
    - `bind()`: Returns a new function with a given `this` value and optionally prepended arguments.

**What are generators in JavaScript?**
    - Generators are special functions that can be paused and resumed, allowing you to manage the function's execution state. They are defined using the `function*` syntax.

**Explain the concept of async/await.**
    - `async/await` is syntactic sugar built on top of promises, making asynchronous code look and behave more like synchronous code. `async` functions return promises, and `await` is used to pause the execution until the promise is resolved.


**How do you debounce a function?**
    - Debouncing is a technique to ensure that a function is not called too frequently. It is achieved by delaying the function execution until a specified time has passed since the last call.

``` 
javascript
function debounce(func, wait) {
  let timeout;
  return function(...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), wait);
  };
}


```


 **How do you throttle a function?**
    - Throttling ensures a function is called at most once in a specified time interval.
```
  javascript
function throttle(func, limit) {
  let lastFunc;
  let lastRan;
  return function(...args) {
    if (!lastRan) {
      func.apply(this, args);
      lastRan = Date.now();
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func.apply(this, args);
          lastRan = Date.now();
        }
      }, limit - (Date.now() - lastRan));
    }
  };
}
``` 

**What are higher-order functions in JavaScript?**
    - Higher-order functions are functions that can take other functions as arguments or return functions as their result.

Explain the concept of currying in JavaScript.**
    - Currying is a technique of transforming a function that takes multiple arguments into a sequence of functions that each take a single argument.

```
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      };
    }
  };
}
```
**How do you handle asynchronous errors in JavaScript?**
    - Asynchronous errors can be handled using `try/catch` blocks with async/await, or `.catch()` with promises.

```
async function asyncFunction() {
  try {
    const result = await someAsyncOperation();
  } catch (error) {
    console.error(error);
  }
}

somePromiseFunction()
  .then(result => console.log(result))
  .catch(error => console.error(error));
```

## React Interview Questions

**What is React?**
   - React is a JavaScript library for building user interfaces, primarily used for single-page applications. It allows developers to create reusable UI components.

**What is JSX?**
   - JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML directly within React. It makes it easier to write and add HTML in React.

**Explain the virtual DOM.**
   - The virtual DOM is a lightweight representation of the real DOM. React uses the virtual DOM to optimize updates by only re-rendering parts of the DOM that have changed.

**What is state in React?**
   - State is an object that holds dynamic data and determines the component's behavior and rendering. State is managed within the component and can change over time.

**What are props in React?**
   - Props (short for properties) are read-only attributes passed from a parent component to a child component. They allow data to flow from one component to another.

**What is the difference between state and props?**
   - State is managed within the component and can change over time, while props are passed to the component and are immutable.

**What are hooks in React?**
   - Hooks are functions that let you use state and other React features in functional components. Examples include `useState`, `useEffect`, `useContext`, `useReducer`, and `useRef`.

**What is the useEffect hook used for?**
   - `useEffect` is used to perform side effects in functional components. It runs after the initial render and after every update, depending on the dependencies provided.

**Explain the lifecycle methods of a React component.**
    - Lifecycle methods are special methods in class components that allow you to run code at specific points in a component's life. Examples include `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

**What is context in React?**
    - Context provides a way to pass data through the component tree without having to pass props down manually at every level. It is useful for global state management.

**What is the difference between controlled and uncontrolled components?**
    - Controlled components are those where the form data is handled by the React component's state. Uncontrolled components store their own state internally and rely on refs to access the DOM elements.

**What are higher-order components (HOCs)?**
    - HOCs are functions that take a component and return a new component with additional props or behavior. They are used to reuse component logic.
 
**How do you optimize performance in a React application?**
    - Performance can be optimized by using techniques such as memoization with `React.memo` and `useMemo`, code-splitting with React.lazy and Suspense, and avoiding unnecessary re-renders by using the `useCallback` hook.

**What is the purpose of keys in React?**
    - Keys help React identify which items have changed, been added, or removed. They should be unique among siblings and help improve the performance of rendering lists.

**How do you fetch data in React?**
    - Data can be fetched in React using various methods, including the `fetch` API, Axios, or libraries like React Query. Data fetching is typically done inside the `useEffect` hook for functional components or lifecycle methods for class components.

**Explain the concept of lifting state up.**
    - Lifting state up involves moving the state to a common ancestor component so that multiple components can share and access the same state. This helps in managing state more effectively across different components.

**How do you create a simple functional component in React?**

```jsx
import React from 'react';

function MyComponent() {
  return <div>Hello, world!</div>;
}

export default MyComponent;
```

**How do you use the useState hook?**

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

**How do you use the useEffect hook?**

```jsx
import React, { useEffect, useState } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const timer = setInterval(() => {
      setCount(count => count + 1);
    }, 1000);
    return () => clearInterval(timer);
  }, []);

  return <div>Count: {count}</div>;
}

export default Timer;
```

**How do you create a context in React?**

```jsx
import React, { createContext, useContext, useState } from 'react';

const MyContext = createContext();

function MyProvider({ children }) {
  const [value, setValue] = useState('Hello, world!');

  return (
    <MyContext.Provider value={value}>
      {children}
    </MyContext.Provider>
  );
}

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

function App() {
  return (
    <MyProvider>
      <MyComponent />
    </MyProvider>
  );
}

export default App;
```

**How do you implement routing in a React application using React Router?**

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>
        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

## Redux Toolkit interview questions:

**What is a slice in Redux Toolkit?**
   - A slice is a collection of Redux reducer logic and actions for a single feature of your application. It is created using the `createSlice` function, which automatically generates action creators and action types.
 
 **How do you handle state immutability with Redux Toolkit?**
   - Redux Toolkit uses the `immer` library under the hood to handle immutability, allowing you to write "mutative" logic in reducers, which are actually applied immutably.

```
const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment(state) {
      return state + 1;
    },
    decrement(state) {
      return state - 1;
    },
  },
});
```

**What are the advantages of using `createSlice` over traditional Redux reducers?**
   - `createSlice` reduces boilerplate by automatically generating action creators and action types, handles immutability with `immer`, and organizes reducer logic by feature.

**How do you use middleware with Redux Toolkit?**
   - Redux Toolkit’s `configureStore` accepts a `middleware` option where you can add custom middleware. It includes default middleware like `redux-thunk` and `redux-logger`.

```
import { configureStore } from '@reduxjs/toolkit';
import logger from 'redux-logger';

const store = configureStore({
  reducer: rootReducer,
  middleware: (getDefaultMiddleware) => getDefaultMiddleware().concat(logger),
});
```
 
**How do you handle side effects in Redux Toolkit?**
    - Side effects are typically handled using middleware like `redux-thunk` or `redux-saga`. With Redux Toolkit, `createAsyncThunk` is a convenient way to manage asynchronous logic directly.

**What is the `extraReducers` field in `createSlice` used for?**
    - `extraReducers` allows a slice to handle actions defined outside of the slice. It is useful for handling actions generated by `createAsyncThunk` or other slices.

```
const userSlice = createSlice({
  name: 'user',
  initialState: { name: '', status: 'idle' },
  reducers: {},
  extraReducers: (builder) => {
    builder
      .addCase(fetchUser.pending, (state) => {
        state.status = 'loading';
      })
      .addCase(fetchUser.fulfilled, (state, action) => {
        state.status = 'succeeded';
        state.name = action.payload.name;
      })
      .addCase(fetchUser.rejected, (state) => {
        state.status = 'failed';
      });
  },
});
```

**What is the purpose of `RTK Query` in Redux Toolkit?**
    - `RTK Query` is a powerful data fetching and caching tool built into Redux Toolkit. It simplifies managing server-side data and reduces boilerplate for common data fetching patterns.
  
**How do you structure a large Redux application with Redux Toolkit?**
    - Large Redux applications can be structured by feature or domain, with each feature having its own slice. Code splitting and lazy loading can be used for performance optimization.

**What is the role of `getDefaultMiddleware` in Redux Toolkit?**
    - `getDefaultMiddleware` is a utility provided by Redux Toolkit that includes a set of default middleware like `redux-thunk` and `redux-logger`. It allows you to customize the middleware stack.
 
## TypeScript Interview Questions

**What is TypeScript?**
   - TypeScript is a superset of JavaScript that adds static typing and other features to the language, which helps in catching errors early during development and improving code quality.

**What are the benefits of using TypeScript over JavaScript?**
   - **Static Typing**: Helps catch errors at compile time.
   - **Improved IDE Support**: Better autocompletion, refactoring, and navigation.
   - **Optional Type Annotations**: Provides flexibility in defining types.
   - **Advanced Language Features**: Such as interfaces, enums, and generics.
   - **Better Code Documentation**: Improves code readability and maintenance.

**What are types in TypeScript?**
   - Types define the shape of data. Examples include basic types like `number`, `string`, `boolean`, and complex types like arrays, objects, tuples, and custom types.

**What is the `any` type in TypeScript?**
   - The `any` type allows a variable to be of any type. It disables type checking and should be used sparingly as it can lead to runtime errors.

```
let value: any = "hello";
value = 42;
```
 
**How do you declare variables in TypeScript?**
   - Variables are declared using `let`, `const`, or `var`, followed by a type annotation.

```
let name: string = "Alice";
const age: number = 30;
var isStudent: boolean = true;
```

**What are interfaces in TypeScript?**
   - Interfaces define the structure of an object. They are used to enforce type checking on object properties.

```
interface Person {
  name: string;
  age: number;
}

const person: Person = {
  name: "John",
  age: 25,
};
```

**What are type aliases in TypeScript?**
   - Type aliases create new names for types. They can be used for both primitive and complex types.

```
type ID = string | number;

let userId: ID = "abc123";
userId = 123;
```

**What are generics in TypeScript?**
   - Generics allow you to create reusable components that can work with any data type. They provide a way to define functions, classes, or interfaces with a placeholder type.

```
function identity<T>(value: T): T {
  return value;
}

const result = identity<string>("hello");
const numResult = identity<number>(42);
```

**What is the difference between `interface` and `type` in TypeScript?**
   - Both `interface` and `type` can be used to define object shapes, but `interface` is more extendable. `type` is more versatile and can be used for other types like unions and intersections.

**How do you handle optional properties in TypeScript?**
    - Optional properties are defined using a question mark `?` after the property name.

```
interface Car {
  brand: string;
  model: string;
  year?: number;
}

const car1: Car = { brand: "Toyota", model: "Corolla" };
const car2: Car = { brand: "Ford", model: "Focus", year: 2018 };
```

**What are enums in TypeScript?**
    - Enums are a way to define a set of named constants. They can be numeric or string-based.

```
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let move: Direction = Direction.Up;
```

**What is type inference in TypeScript?**
    - TypeScript can automatically infer the type of a variable based on its initial value, reducing the need for explicit type annotations.

```
let inferredString = "hello"; // inferred as string
let inferredNumber = 42; // inferred as number
```

**What are utility types in TypeScript?**
    - Utility types are built-in types that provide type transformations. Examples include `Partial`, `Readonly`, `Pick`, and `Omit`.

```
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

const todo: Partial<Todo> = {
  title: "Learn TypeScript",
};
```
   
**What is the `unknown` type in TypeScript?**
    - The `unknown` type is similar to `any`, but safer. It requires you to perform type checking before using the variable.

```
let value: unknown = "hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```
  
