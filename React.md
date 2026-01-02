# React - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Setup & Basic Concepts](#setup--basic-concepts)
4. [JSX (JavaScript XML)](#jsx-javascript-xml)
5. [Props (Properties)](#props-properties)
6. [State & useState Hook](#state--usestate-hook)
7. [Events](#events)
8. [Conditional Rendering](#conditional-rendering)
9. [Lists & Keys](#lists--keys)
10. [useEffect Hook](#useeffect-hook)
11. [Forms & Controlled Components](#forms--controlled-components)
12. [useContext Hook (Context API)](#usecontext-hook-context-api)
13. [useReducer Hook](#usereducer-hook)
14. [useRef Hook](#useref-hook)
15. [useMemo & useCallback Hooks (Performance)](#usememo--usecallback-hooks-performance)
16. [Custom Hooks](#custom-hooks)
17. [React Router](#react-router)
18. [Best Practices](#best-practices)
19. [Common Patterns](#common-patterns)
20. [Resources](#resources)

---

## Introduction

### What is React?

React is a JavaScript library for building user interfaces, developed by Facebook (Meta). React allows developers to create reusable UI components and build complex, interactive web applications. React uses a virtual DOM for efficient updates and follows a component-based architecture.

### Why Learn React?

React is valuable for:

1. **Component-Based**: Build reusable UI components
2. **Virtual DOM**: Efficient rendering and updates
3. **Declarative**: Describe UI state, React handles updates
4. **Large Ecosystem**: Extensive library ecosystem
5. **Industry Standard**: Used by Facebook, Netflix, Airbnb, many others
6. **Developer Experience**: Great tooling, React DevTools
7. **React Native**: Same skills for mobile app development
8. **Job Market**: High demand for React developers

### Key Features

- **Components**: Reusable, composable UI building blocks
- **JSX**: JavaScript syntax extension for writing components
- **Virtual DOM**: Efficient diffing and rendering
- **One-Way Data Flow**: Predictable data flow from parent to child
- **Hooks**: Modern way to use state and lifecycle in function components
- **React Router**: Client-side routing
- **State Management**: Built-in state, or use Redux, Zustand, etc.

---

## Getting Started

### Installation

**Create React App:**
```bash
npx create-react-app my-app
cd my-app
npm start
```

**Vite (faster alternative):**
```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

### Your First Component

**Code:**
```jsx
import React from 'react';

function HelloWorld() {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>Welcome to React!</p>
    </div>
  );
}

export default HelloWorld;
```

---

## Setup & Basic Concepts

### Overview

React is a library for building user interfaces. Understanding the basic concepts of components, JSX, and React's component-based architecture is essential.

### Key Concepts

- **Components**: Reusable UI building blocks
- **Function Components**: Modern way (with hooks)
- **Class Components**: Legacy (still used in some codebases)
- **JSX**: JavaScript XML syntax
- **Virtual DOM**: Efficient updates
- **One-Way Data Flow**: Parent to child

### Components

**What this demonstrates:** Creating React components.

**Code:**
```jsx
// Function Component (Modern, preferred)
function HelloWorld() {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>Welcome to React!</p>
    </div>
  );
}

// Arrow Function Component
const HelloWorld = () => {
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  );
};

// Implicit Return (single element)
const HelloWorld = () => (
  <div>
    <h1>Hello, World!</h1>
  </div>
);

// Class Component (Legacy)
import React, { Component } from 'react';

class HelloWorld extends Component {
  render() {
    return (
      <div>
        <h1>Hello, World!</h1>
      </div>
    );
  }
}
```

**Explanation:**
- Function components: Modern approach (preferred)
- Arrow functions: Shorter syntax
- Class components: Legacy (still used, but function components preferred)
- Return JSX: Components return JSX
- Export: Export component for use

**Key Takeaways:**
- Use function components (modern)
- Components return JSX
- Export components for reuse

---

## JSX (JavaScript XML)

### Overview

JSX is a syntax extension that allows writing HTML-like code in JavaScript. JSX is compiled to React.createElement() calls.

### Key Concepts

- **JSX Syntax**: HTML-like syntax in JavaScript
- **Expressions**: `{expression}` for JavaScript
- **Attributes**: camelCase (onClick, className)
- **Fragments**: `<>...</>` or `<React.Fragment>`
- **Self-Closing Tags**: Must have closing `/`
- **Comments**: `{/* comment */}`

### JSX Basics

**What this demonstrates:** Writing JSX.

**Code:**
```jsx
function JSXDemo() {
  const name = 'Commander';
  const age = 25;
  const isLoggedIn = true;
  
  // Inline styles (object)
  const divStyle = {
    color: 'blue',
    backgroundColor: 'lightgray',
    padding: '10px'
  };
  
  return (
    <div>
      {/* Comments in JSX */}
      
      {/* Expressions in curly braces */}
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
      <p>Result: {10 + 20}</p>
      
      {/* Conditional rendering */}
      <p>{isLoggedIn ? 'Welcome back!' : 'Please log in'}</p>
      {isLoggedIn && <p>You are logged in</p>}
      
      {/* Inline styles */}
      <div style={divStyle}>Styled content</div>
      <div style={{ color: 'red', fontSize: '20px' }}>Inline style</div>
      
      {/* className instead of class */}
      <div className="container">
        <p className="text-primary">Styled with CSS</p>
      </div>
      
      {/* Fragments */}
      <>
        <h2>Title</h2>
        <p>Paragraph</p>
      </>
      
      {/* Attributes are camelCase */}
      <button onClick={() => alert('Clicked!')}>Click Me</button>
    </div>
  );
}
```

**Explanation:**
- JSX: Looks like HTML but is JavaScript
- Expressions: `{expression}` evaluates JavaScript
- Attributes: camelCase (className, onClick, htmlFor)
- Styles: Object with camelCase properties
- Fragments: Wrap multiple elements without extra DOM node
- Comments: `{/* comment */}` syntax

**Key Takeaways:**
- JSX expressions in `{}`
- Use `className` not `class`
- Use camelCase for attributes
- Fragments for multiple elements

---

## Props (Properties)

### Overview

Props are data passed from parent components to child components. Props are read-only and enable component reusability.

### Key Concepts

- **Props**: Data passed to components
- **Read-Only**: Props cannot be modified by child
- **Default Props**: Default values
- **Children**: Special prop for nested content
- **Prop Types**: Type checking (PropTypes or TypeScript)

### Props

**What this demonstrates:** Using props.

**Code:**
```jsx
// Passing props
function App() {
  return (
    <div>
      <Greeting name="Alice" age={25} />
      <Greeting name="Bob" age={30} />
      <UserCard 
        name="Charlie" 
        email="charlie@example.com"
        isAdmin={true}
      />
    </div>
  );
}

// Receiving props
function Greeting(props) {
  return (
    <div>
      <h2>Hello, {props.name}!</h2>
      <p>Age: {props.age}</p>
    </div>
  );
}

// Destructuring props (preferred)
function Greeting({ name, age }) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      <p>Age: {age}</p>
    </div>
  );
}

// Default props
function Greeting({ name = 'Guest', age = 0 }) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      <p>Age: {age}</p>
    </div>
  );
}

// Props with children
function Card({ title, children }) {
  return (
    <div className="card">
      <h3>{title}</h3>
      <div className="card-body">
        {children}
      </div>
    </div>
  );
}

// Usage
<Card title="User Info">
  <p>Card content</p>
</Card>
```

**Explanation:**
- Props: Passed from parent to child
- Destructuring: Extract props (preferred)
- Default values: Default parameter values
- Children: Special prop for nested content
- Read-only: Cannot modify props

**Key Takeaways:**
- Props pass data to components
- Use destructuring for props
- Props are read-only
- `children` for nested content

---

## State & useState Hook

### Overview

State allows components to manage and update data. The `useState` hook is the modern way to add state to function components.

### Key Concepts

- **State**: Component's internal data
- **useState Hook**: Add state to function components
- **State Updates**: Trigger re-renders
- **State is Local**: Each component has its own state
- **Immutable Updates**: Don't mutate state directly

### useState Hook

**What this demonstrates:** Managing state with useState.

**Code:**
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}

// Multiple state variables
function UserForm() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [age, setAge] = useState(0);
  
  return (
    <form>
      <input 
        value={name} 
        onChange={(e) => setName(e.target.value)} 
      />
      <input 
        value={email} 
        onChange={(e) => setEmail(e.target.value)} 
      />
      <input 
        type="number"
        value={age} 
        onChange={(e) => setAge(Number(e.target.value))} 
      />
    </form>
  );
}

// State with object
function UserProfile() {
  const [user, setUser] = useState({
    name: '',
    email: '',
    age: 0
  });
  
  const updateName = (name) => {
    setUser({ ...user, name });  // Spread operator
  };
  
  return (
    <div>
      <input 
        value={user.name}
        onChange={(e) => updateName(e.target.value)}
      />
    </div>
  );
}
```

**Explanation:**
- `useState`: Hook for state
- Returns: `[value, setter]` array
- Initial value: Passed to `useState()`
- Updates: Call setter function
- Immutable: Don't mutate state, create new value
- Spread operator: `{...obj}` for objects/arrays

**Key Takeaways:**
- `useState(initialValue)` returns `[value, setter]`
- Call setter to update state
- Don't mutate state directly
- Use spread operator for objects/arrays

---

## Events

### Overview

React events are synthetic events that wrap native browser events. Event handlers are functions that respond to user interactions.

### Key Concepts

- **Event Handlers**: Functions for events
- **Synthetic Events**: React's event system
- **Event Object**: Passed to handlers
- **Binding**: Arrow functions or bind
- **Event Names**: camelCase (onClick, onChange)

### Events

**What this demonstrates:** Handling events.

**Code:**
```jsx
function EventDemo() {
  const handleClick = () => {
    alert('Button clicked!');
  };
  
  const handleChange = (e) => {
    console.log('Input value:', e.target.value);
  };
  
  const handleSubmit = (e) => {
    e.preventDefault();  // Prevent form submission
    console.log('Form submitted');
  };
  
  return (
    <div>
      {/* Inline handler */}
      <button onClick={() => alert('Clicked!')}>Click Me</button>
      
      {/* Handler function */}
      <button onClick={handleClick}>Click Me</button>
      
      {/* With parameters */}
      <button onClick={() => handleClick('parameter')}>Click Me</button>
      
      {/* Form events */}
      <form onSubmit={handleSubmit}>
        <input onChange={handleChange} />
        <button type="submit">Submit</button>
      </form>
      
      {/* Mouse events */}
      <div 
        onMouseEnter={() => console.log('Entered')}
        onMouseLeave={() => console.log('Left')}
      >
        Hover me
      </div>
    </div>
  );
}
```

**Explanation:**
- Event handlers: Functions for events
- camelCase: `onClick`, `onChange`, `onSubmit`
- Event object: `e` parameter (synthetic event)
- `e.preventDefault()`: Prevent default behavior
- `e.target`: Element that triggered event
- Arrow functions: Common for inline handlers

**Key Takeaways:**
- Event handlers are functions
- Use camelCase for event names
- `e.preventDefault()` prevents default
- Arrow functions for inline handlers

---

## Conditional Rendering

### Overview

Conditional rendering allows showing different content based on conditions. React supports multiple patterns for conditional rendering.

### Key Concepts

- **Ternary Operator**: `condition ? true : false`
- **Logical AND**: `condition && element`
- **if/else**: Outside JSX
- **Early Returns**: Return early from component
- **Multiple Conditions**: Nested ternaries or functions

### Conditional Rendering

**What this demonstrates:** Different conditional rendering patterns.

**Code:**
```jsx
function ConditionalDemo() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const [userRole, setUserRole] = useState('user');
  
  // Ternary operator
  return (
    <div>
      {isLoggedIn ? (
        <p>Welcome back!</p>
      ) : (
        <p>Please log in</p>
      )}
      
      {/* Logical AND */}
      {isLoggedIn && <p>You are logged in</p>}
      
      {/* Multiple conditions */}
      {userRole === 'admin' ? (
        <AdminPanel />
      ) : userRole === 'moderator' ? (
        <ModeratorPanel />
      ) : (
        <UserPanel />
      )}
      
      {/* Early return pattern */}
      {!isLoggedIn && <LoginForm />}
    </div>
  );
}

// Early return in component
function UserProfile({ user }) {
  if (!user) {
    return <div>Please log in</div>;
  }
  
  return (
    <div>
      <h2>Welcome, {user.name}!</h2>
    </div>
  );
}
```

**Explanation:**
- Ternary: `condition ? trueJSX : falseJSX`
- Logical AND: `condition && JSX` (renders if true)
- Early return: Return early from component
- Multiple: Nested ternaries or if/else outside JSX
- Clean: Choose clearest pattern

**Key Takeaways:**
- Use ternary for if/else
- Use `&&` for conditional rendering
- Early returns for guard clauses

---

## Lists & Keys

### Overview

Rendering lists in React requires mapping over arrays and providing unique keys. Keys help React identify which items have changed.

### Key Concepts

- **map()**: Transform array to JSX elements
- **Keys**: Unique identifiers for list items
- **Key Requirements**: Must be unique, stable, not index (if possible)
- **Key Prop**: Passed to elements

### Lists and Keys

**What this demonstrates:** Rendering lists.

**Code:**
```jsx
function ListDemo() {
  const items = ['Apple', 'Banana', 'Cherry'];
  const users = [
    { id: 1, name: 'Alice', age: 25 },
    { id: 2, name: 'Bob', age: 30 },
    { id: 3, name: 'Charlie', age: 35 }
  ];
  
  return (
    <div>
      {/* Simple list */}
      <ul>
        {items.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
      
      {/* List with objects (use ID as key) */}
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - {user.age}
          </li>
        ))}
      </ul>
      
      {/* List with components */}
      {users.map((user) => (
        <UserCard key={user.id} user={user} />
      ))}
    </div>
  );
}
```

**Explanation:**
- `map()`: Transform array to JSX
- Keys: Unique identifier prop
- Key rules: Unique, stable, prefer ID over index
- Index keys: OK if list is static
- ID keys: Better for dynamic lists

**Key Takeaways:**
- Use `map()` for lists
- Always provide `key` prop
- Use stable, unique keys (prefer ID)

---

## useEffect Hook

### Overview

The `useEffect` hook allows performing side effects in function components. It's used for data fetching, subscriptions, and DOM manipulation.

### Key Concepts

- **Side Effects**: Operations outside component (API calls, subscriptions)
- **useEffect Hook**: Handle side effects
- **Dependency Array**: Control when effect runs
- **Cleanup**: Clean up subscriptions/effects
- **Effect Lifecycle**: Runs after render

### useEffect Hook

**What this demonstrates:** Using useEffect for side effects.

**Code:**
```jsx
import { useState, useEffect } from 'react';

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  
  // Effect runs after every render (no dependencies)
  useEffect(() => {
    document.title = 'User Profile';
  });
  
  // Effect runs once (empty dependency array)
  useEffect(() => {
    console.log('Component mounted');
    
    // Cleanup function
    return () => {
      console.log('Component unmounted');
    };
  }, []);
  
  // Effect runs when userId changes
  useEffect(() => {
    fetch(`/api/users/${userId}`)
      .then(res => res.json())
      .then(data => setUser(data));
  }, [userId]);  // Dependency array
  
  // Cleanup example (subscription)
  useEffect(() => {
    const interval = setInterval(() => {
      console.log('Tick');
    }, 1000);
    
    // Cleanup function
    return () => {
      clearInterval(interval);
    };
  }, []);
  
  return <div>{user?.name}</div>;
}
```

**Explanation:**
- `useEffect`: Hook for side effects
- Effect function: Runs after render
- Dependencies: Array controls when effect runs
- Empty array: Run once (on mount)
- Cleanup: Return function for cleanup
- Common use: API calls, subscriptions, DOM manipulation

**Key Takeaways:**
- `useEffect` for side effects
- Dependency array controls when it runs
- Cleanup function for subscriptions
- Empty array = run once

---

## Forms & Controlled Components

### Overview

Controlled components are form elements whose value is controlled by React state. This enables React to control form data.

### Key Concepts

- **Controlled Components**: Value controlled by state
- **onChange**: Update state on input change
- **value Prop**: Bind input to state
- **Form Submission**: Handle onSubmit
- **Multiple Inputs**: Manage multiple state values

### Forms

**What this demonstrates:** Creating controlled forms.

**Code:**
```jsx
function LoginForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Email:', email);
    console.log('Password:', password);
    // Handle login
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />
      <input
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
        placeholder="Password"
      />
      <button type="submit">Login</button>
    </form>
  );
}

// Multiple inputs with object state
function UserForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    age: ''
  });
  
  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };
  
  return (
    <form>
      <input
        name="name"
        value={formData.name}
        onChange={handleChange}
      />
      <input
        name="email"
        value={formData.email}
        onChange={handleChange}
      />
    </form>
  );
}
```

**Explanation:**
- Controlled: `value` and `onChange` props
- State: Form data in state
- `onChange`: Update state on input change
- `onSubmit`: Handle form submission
- Multiple inputs: Use object state or individual states

**Key Takeaways:**
- Use `value` and `onChange` for controlled inputs
- `e.preventDefault()` in onSubmit
- Object state for multiple inputs

---

## useContext Hook (Context API)

### Overview

The Context API provides a way to share data across the component tree without prop drilling. The `useContext` hook accesses context values.

### Key Concepts

- **Context**: Share data across components
- **Provider**: Provides context value
- **Consumer**: Consumes context value
- **useContext Hook**: Access context in function components
- **Avoid Prop Drilling**: Share data without passing props

### Context API

**What this demonstrates:** Using Context API.

**Code:**
```jsx
import { createContext, useContext, useState } from 'react';

// Create context
const ThemeContext = createContext();
const UserContext = createContext();

// Provider component
function App() {
  const [theme, setTheme] = useState('light');
  const [user, setUser] = useState({ name: 'Commander', role: 'admin' });
  
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <UserContext.Provider value={{ user, setUser }}>
        <div className={`app ${theme}`}>
          <Header />
          <MainContent />
        </div>
      </UserContext.Provider>
    </ThemeContext.Provider>
  );
}

// Consumer component
function Header() {
  const { theme, setTheme } = useContext(ThemeContext);
  const { user } = useContext(UserContext);
  
  const toggleTheme = () => {
    setTheme(theme === 'light' ? 'dark' : 'light');
  };
  
  return (
    <header>
      <h1>Welcome, {user.name}!</h1>
      <button onClick={toggleTheme}>
        Switch to {theme === 'light' ? 'dark' : 'light'} mode
      </button>
    </header>
  );
}

// Custom hook for context
function useTheme() {
  const context = useContext(ThemeContext);
  if (!context) {
    throw new Error('useTheme must be used within ThemeProvider');
  }
  return context;
}
```

**Explanation:**
- `createContext()`: Create context
- Provider: Wrap components with Provider
- `useContext()`: Access context value
- Custom hooks: Wrap useContext for better API
- Multiple contexts: Can use multiple contexts

**Key Takeaways:**
- Context API avoids prop drilling
- Use Provider to provide value
- `useContext` to access context
- Custom hooks for better API

---

## useReducer Hook

### Overview

`useReducer` is an alternative to `useState` for managing complex state logic. It's similar to Redux pattern and useful for state machines.

### Key Concepts

- **Reducer**: Function that updates state based on actions
- **Action**: Object describing what happened
- **Dispatch**: Function to dispatch actions
- **Initial State**: Starting state value
- **Complex State**: Better for complex state logic

### useReducer

**What this demonstrates:** Using useReducer.

**Code:**
```jsx
import { useReducer } from 'react';

// Reducer function
function counterReducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    case 'RESET':
      return { count: 0 };
    case 'SET':
      return { count: action.payload };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });
  
  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>+</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>-</button>
      <button onClick={() => dispatch({ type: 'RESET' })}>Reset</button>
      <button onClick={() => dispatch({ type: 'SET', payload: 100 })}>
        Set to 100
      </button>
    </div>
  );
}
```

**Explanation:**
- `useReducer`: Hook for reducer pattern
- Reducer: `(state, action) => newState`
- Dispatch: Function to dispatch actions
- Actions: Objects with `type` and optional `payload`
- Better for: Complex state logic

**Key Takeaways:**
- `useReducer` for complex state
- Reducer function updates state
- Dispatch actions to update
- Better than useState for complex logic

---

## useRef Hook

### Overview

`useRef` provides a way to access DOM elements and store mutable values that don't trigger re-renders. It persists across renders.

### Key Concepts

- **Ref Object**: `.current` property holds value
- **DOM Access**: Access DOM elements
- **Mutable Values**: Values that don't trigger re-renders
- **Persistent**: Persists across renders
- **Previous Values**: Track previous values

### useRef

**What this demonstrates:** Using useRef.

**Code:**
```jsx
import { useRef, useEffect } from 'react';

function InputFocus() {
  const inputRef = useRef(null);
  
  const focusInput = () => {
    inputRef.current.focus();
  };
  
  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}

// Storing mutable values
function Timer() {
  const [count, setCount] = useState(0);
  const intervalRef = useRef(null);
  
  useEffect(() => {
    intervalRef.current = setInterval(() => {
      setCount(prev => prev + 1);
    }, 1000);
    
    return () => clearInterval(intervalRef.current);
  }, []);
  
  return <div>Count: {count}</div>;
}

// Previous value
function usePrevious(value) {
  const ref = useRef();
  useEffect(() => {
    ref.current = value;
  });
  return ref.current;
}
```

**Explanation:**
- `useRef`: Hook for refs
- `.current`: Property holds value
- DOM refs: `ref={refName}` on elements
- Mutable values: Store values without re-render
- Persistent: Survives re-renders

**Key Takeaways:**
- `useRef` for DOM access
- `.current` property
- Doesn't trigger re-renders
- Persistent across renders

---

## useMemo & useCallback Hooks (Performance)

### Overview

`useMemo` and `useCallback` optimize performance by memoizing values and functions. They prevent unnecessary recalculations and re-renders.

### Key Concepts

- **useMemo**: Memoize computed values
- **useCallback**: Memoize functions
- **Dependencies**: Array controls when to recalculate
- **Performance**: Optimize expensive operations
- **Avoid Premature**: Only use when needed

### Performance Hooks

**What this demonstrates:** Optimizing with useMemo and useCallback.

**Code:**
```jsx
import { useMemo, useCallback, useState } from 'react';

function ExpensiveComponent({ items, filter }) {
  // Memoize expensive computation
  const filteredItems = useMemo(() => {
    return items.filter(item => item.category === filter);
  }, [items, filter]);
  
  // Memoize callback function
  const handleClick = useCallback((id) => {
    console.log('Clicked:', id);
  }, []);
  
  return (
    <div>
      {filteredItems.map(item => (
        <div key={item.id} onClick={() => handleClick(item.id)}>
          {item.name}
        </div>
      ))}
    </div>
  );
}
```

**Explanation:**
- `useMemo`: Memoize computed values
- `useCallback`: Memoize functions
- Dependencies: Array controls recalculation
- Performance: Avoid expensive recalculations
- Use when: Expensive operations or stable references needed

**Key Takeaways:**
- `useMemo` for expensive computations
- `useCallback` for stable function references
- Dependencies control recalculation
- Use only when needed

---

## Custom Hooks

### Overview

Custom hooks are JavaScript functions that use React hooks. They enable code reuse and sharing logic between components.

### Key Concepts

- **Custom Hooks**: Functions starting with `use`
- **Reuse Logic**: Share logic between components
- **Compose Hooks**: Use other hooks inside
- **Naming**: Must start with `use`
- **Return Values**: Return whatever needed

### Custom Hooks

**What this demonstrates:** Creating custom hooks.

**Code:**
```jsx
// Custom hook for fetching data
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    const fetchData = async () => {
      try {
        setLoading(true);
        const response = await fetch(url);
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    
    fetchData();
  }, [url]);
  
  return { data, loading, error };
}

// Usage
function UserList() {
  const { data, loading, error } = useFetch('https://api.example.com/users');
  
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  
  return (
    <ul>
      {data.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}

// Custom hook for local storage
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });
  
  const setValue = (value) => {
    try {
      setStoredValue(value);
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error(error);
    }
  };
  
  return [storedValue, setValue];
}
```

**Explanation:**
- Custom hooks: Functions using hooks
- Naming: Start with `use`
- Compose: Use other hooks inside
- Reuse: Share logic between components
- Return: Return whatever needed

**Key Takeaways:**
- Custom hooks start with `use`
- Share logic between components
- Can use other hooks inside
- Return values as needed

---

## React Router

### Overview

React Router enables client-side routing in React applications. It allows navigation without page refreshes and manages URL-based routing.

### Key Concepts

- **Routes**: Define route paths
- **Navigation**: Link and Navigate components
- **Route Parameters**: Dynamic route segments
- **Nested Routes**: Routes within routes
- **Programmatic Navigation**: Navigate in code

### React Router

**What this demonstrates:** Setting up React Router.

**Code:**
```jsx
import { BrowserRouter, Routes, Route, Link, useParams } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
        <Link to="/users">Users</Link>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/users" element={<Users />} />
        <Route path="/users/:id" element={<UserDetail />} />
      </Routes>
    </BrowserRouter>
  );
}

function UserDetail() {
  const { id } = useParams();
  return <div>User ID: {id}</div>;
}
```

**Explanation:**
- `BrowserRouter`: Router wrapper
- `Routes`: Route container
- `Route`: Define route
- `Link`: Navigation link
- `useParams`: Access route parameters

**Key Takeaways:**
- React Router for client-side routing
- Use `Link` for navigation
- `Routes` and `Route` for routing
- `useParams` for route parameters

---

## Best Practices

### Component Design

- **Small Components**: Keep components small and focused
- **Single Responsibility**: One component, one purpose
- **Props**: Pass only needed props
- **Composition**: Compose components
- **Naming**: Clear, descriptive names

### Performance

- **useMemo/useCallback**: When needed, not always
- **Code Splitting**: Lazy load components
- **Virtual Lists**: For long lists
- **Avoid Inline Objects**: In JSX props
- **React.memo**: Memoize components

### State Management

- **Local State**: Use useState for component state
- **Lifted State**: Lift state up when needed
- **Context**: For global state
- **External Libraries**: Redux, Zustand for complex state

---

## Common Patterns

### Container/Presentational

```jsx
// Container (logic)
function UserListContainer() {
  const [users, setUsers] = useState([]);
  
  useEffect(() => {
    fetchUsers().then(setUsers);
  }, []);
  
  return <UserList users={users} />;
}

// Presentational (UI)
function UserList({ users }) {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

### Higher-Order Component (HOC)

```jsx
function withAuth(Component) {
  return function AuthenticatedComponent(props) {
    const { user } = useAuth();
    
    if (!user) {
      return <Login />;
    }
    
    return <Component {...props} user={user} />;
  };
}
```

---

## Resources

### Official Documentation

- **React Documentation**: https://react.dev/
- **React API Reference**: https://react.dev/reference/react
- **React Blog**: https://react.dev/blog

### Learning Resources

- **React Tutorial**: https://react.dev/learn
- **React Docs Beta**: https://react.dev/
- **React Patterns**: https://reactpatterns.com/

### Community

- **Stack Overflow**: Tag: reactjs
- **r/reactjs**: Reddit community
- **Reactiflux Discord**: Community server

### Tools

- **Create React App**: Bootstrap React projects
- **Vite**: Fast build tool
- **React DevTools**: Browser extension
- **React Router**: Routing library
- **Next.js**: React framework
- **Redux**: State management

---

