# React Routing in React Vite

## Setting Up React Router in a Vite Project

### 1. Create a Vite Project
First, set up a new Vite project with React:

```sh
npm create vite@latest my-app --template react
cd my-app
npm install
```

### 2. Install React Router
To use React Router, install the required package:

```sh
npm install react-router-dom
```

### 3. Set Up the Router
Modify `main.jsx` to include the `BrowserRouter`:

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

### 4. Define Routes in `App.jsx`
Create different components for different routes:

```jsx
import { Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import UserProfile from './pages/UserProfile';

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/user/:username" element={<UserProfile />} />
    </Routes>
  );
}

export default App;
```

### 5. Create Component Files
#### `pages/Home.jsx`
```jsx
function Home() {
  return <h1>Home Page</h1>;
}

export default Home;
```

#### `pages/About.jsx`
```jsx
function About() {
  return <h1>About Page</h1>;
}

export default About;
```

#### `pages/UserProfile.jsx`
```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { username } = useParams();

  return <h1>Welcome, {username}!</h1>;
}

export default UserProfile;
```

### 6. Add Navigation
Modify `App.jsx` to include navigation:

```jsx
import { Link } from 'react-router-dom';
import { Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import UserProfile from './pages/UserProfile';

function App() {
  return (
    <>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
        <Link to="/user/Aryan">User Profile</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/user/:username" element={<UserProfile />} />
      </Routes>
    </>
  );
}

export default App;
```

### 7. Run the Application
Start the development server:

```sh
npm run dev
```

Now, navigate to `http://localhost:5173/` to see your React Router in action!
