# Context API in React with Vite

## Introduction
Context API is a built-in state management solution in React that allows you to pass data through the component tree without having to manually pass props at every level. It is useful for managing global states such as themes, authentication, and user preferences.

## Setting Up a React Project with Vite
To create a new React project using Vite, run the following commands:

```sh
npm create vite@latest my-app --template react
cd my-app
npm install
npm run dev
```

## Creating a Context
To use the Context API, follow these steps:

### 1. Create a Context
Create a new file `ThemeContext.js` in the `src` directory:

```js
import { createContext, useState } from "react";

const ThemeContext = createContext();

export const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme((prevTheme) => (prevTheme === "light" ? "dark" : "light"));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

export default ThemeContext;
```

### 2. Wrap the Application with the Provider
Modify `main.jsx` to include the `ThemeProvider`:

```js
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import { ThemeProvider } from "./ThemeContext";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <ThemeProvider>
      <App />
    </ThemeProvider>
  </React.StrictMode>
);
```

### 3. Consume the Context in a Component
Use the `useContext` hook to access the context values in any component:

```js
import { useContext } from "react";
import ThemeContext from "./ThemeContext";

const ThemeToggle = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div style={{ background: theme === "light" ? "#fff" : "#333", color: theme === "light" ? "#000" : "#fff", padding: "20px" }}>
      <p>Current Theme: {theme}</p>
      <button onClick={toggleTheme}>Toggle Theme</button>
    </div>
  );
};

export default ThemeToggle;
```

### 4. Use the Component in `App.jsx`
Modify `App.jsx` to include the `ThemeToggle` component:

```js
import ThemeToggle from "./ThemeToggle";

function App() {
  return (
    <div>
      <h1>React Context API with Vite</h1>
      <ThemeToggle />
    </div>
  );
}

export default App;
```

## Conclusion
The Context API simplifies state management in React applications by providing a way to share values between components without manually passing props. Using Vite as a development tool enhances performance and streamlines project setup. This example demonstrates how to implement a simple theme toggler using Context API in a React Vite project.
