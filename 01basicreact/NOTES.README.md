# React Notes

## What is React?
- **React** is a JavaScript library for building user interfaces, primarily for single-page applications.
- Developed and maintained by Facebook.
- Uses a component-based architecture, making UI development modular and reusable.
- Utilizes a virtual DOM for efficient UI updates.

## Key Features
- **Declarative:** Describe what you want to see, and React updates the UI.
- **Component-Based:** Build encapsulated components that manage their own state.
- **Learn Once, Write Anywhere:** Use React for web (ReactDOM) and mobile (React Native).

## Core Concepts
- **JSX:** JavaScript XML, a syntax extension for writing UI code that looks like HTML.
- **Components:** Functions or classes that return JSX.
- **Props:** Inputs to components, passed as attributes.
- **State:** Data managed within a component.
- **Lifecycle Methods:** Functions that run at specific points in a component’s life (class components).

---

# ReactDOM

## What is ReactDOM?
- **ReactDOM** is the package that provides DOM-specific methods for web applications.
- It connects React components to the browser DOM.

## Usage
- Renders React components into the DOM.
- Example:
  ```js
  import React from 'react';
  import ReactDOM from 'react-dom/client';

  ReactDOM.createRoot(document.getElementById('root')).render(<App />);



# React Native Documentation

## What is React Native?

React Native is a framework for building native mobile apps using React. It allows you to write mobile applications for both iOS and Android platforms using JavaScript and React.

## Key Differences from ReactDOM

- **Native Components:**  
  React Native uses native components such as `<View>`, `<Text>`, and `<Image>` instead of web elements like `<div>`, `<span>`, etc.

- **No Browser DOM:**  
  React Native does not provide direct access to the browser DOM.

- **Bridge Communication:**  
  React Native uses a bridge to communicate between JavaScript code and native platform code, enabling access to native APIs and features.

---


## npx create-react-app

`npx create-react-app` is a command used to quickly set up a new React project with a pre-configured development environment.

- **npx**: A package runner tool that comes with Node.js, allowing you to run packages without installing them globally.
- **create-react-app**: An official tool provided by the React team to scaffold a new React application with sensible defaults and best practices.

### Usage

```bash
npx create-react-app my-app
```

This command creates a new folder named `my-app` with all the necessary files and dependencies to start developing a React application.

### Key Features

- Sets up a modern build setup with no configuration.
- Includes development server, build scripts, and testing utilities.
- Supports JSX, ES6, and more out of the box.





# Understanding `package.json` in a React Project

The `package.json` file is a crucial part of any Node.js or React project. It manages project metadata, dependencies, scripts, and configuration.

---

## Key Sections in This `package.json`

### 1. Project Metadata
- **name**: `"01basicreact"`  
  The name of your project.
- **version**: `"0.1.0"`  
  The current version of your project.
- **private**: `true`  
  Prevents accidental publishing to the npm registry.

---

### 2. Dependencies
Lists all the packages your project needs to run:
- **react**: Core React library for building UI.
- **react-dom**: React package for working with the DOM.
- **react-scripts**: Scripts and configuration used by Create React App.
- **@testing-library/jest-dom**: Custom Jest matchers for testing DOM nodes.
- **@testing-library/react**: Utilities for testing React components.
- **@testing-library/user-event**: Simulates user interactions in tests.
- **web-vitals**: Measures performance metrics.

---

### 3. Scripts
Shortcuts to run common tasks:
- **start**: Runs the app in development mode (`npm start`).
- **build**: Builds the app for production (`npm run build`).
- **test**: Runs tests (`npm test`).
- **eject**: Exposes configuration files for customization (`npm run eject`).

---

### 4. ESLint Configuration
- **eslintConfig**: Specifies linting rules by extending recommended React settings.

---

### 5. Browserslist
Defines which browsers the app should support:
- **production**: Targets a broad range of browsers for deployed apps.
- **development**: Focuses on the latest versions for local development.

---

## Summary

- `package.json` manages dependencies, scripts, and configuration.
- It is essential for running, building, and testing your React app.
- Understanding each section helps you maintain and customize your project efficiently.









# Understanding `package-lock.json` in a React Project

The `package-lock.json` file is automatically generated when you run `npm install` in your project. It works alongside `package.json` to ensure consistent and reliable dependency management.

---

## Key Purposes of `package-lock.json`

- **Locks Dependency Versions:**  
  Records the exact versions of every installed package and its dependencies, ensuring that the same versions are installed each time, even if the `package.json` specifies version ranges.

- **Ensures Consistency:**  
  Guarantees that all developers and deployment environments use the same dependency tree, reducing "works on my machine" issues.

- **Improves Install Speed:**  
  Provides a map of the dependency tree, allowing npm to resolve and install packages faster.

- **Security:**  
  Helps security tools scan for vulnerabilities in all installed packages, including nested dependencies.

---

## Main Sections in `package-lock.json`

- **name & version:**  
  The name and version of your project.

- **lockfileVersion:**  
  Indicates the version of the lock file format.

- **dependencies:**  
  An object listing all installed packages, their resolved versions, integrity hashes, and any nested dependencies.

---

## Why Not Edit Manually?

You should never manually edit `package-lock.json`. It is managed by npm and updated automatically when you install or update packages.

---

## Summary

- `package-lock.json` ensures consistent, repeatable installs for your project.
- It locks the full dependency tree, not just top-level packages.
- Always commit this file to version control for team projects.




