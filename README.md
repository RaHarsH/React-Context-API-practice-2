## React Context API Practice 2 - Learning Different Approaches to Creating Context

In this practice, I explored a different approach to creating and using context in React by utilizing `createContext` and `useContext`. Here's a breakdown of how I learned to implement and structure this approach:

### 1. **Creating the Context**
I started by using the `createContext` method from React, which helps define a new context object. The object passed to `createContext` serves as the default value for the context. I learned that it's crucial to initialize the context with proper values, even if they are placeholders. In this case, I set the initial state with a default `themeMode` of `"light"` and two empty methods for switching between dark and light themes.

```js
export const ThemeContext = createContext({
    themeMode: "light",
    darkTheme: () => {},
    lightTheme: () => {},
});
```

This approach provided a structure for managing theme-related states (such as light and dark modes) throughout the component tree.

### 2. **Exporting the Provider**
React's `Context.Provider` component allows consumers to access and modify context values. By exporting the `Provider` directly, I learned to keep my code modular and clean, which helps to maintain flexibility in defining how and where the context values are provided to child components.

```js
export const ThemeProvider = ThemeContext.Provider;
```

### 3. **Using `useContext` to Access Context Values**
Instead of manually accessing the context via `useContext(ThemeContext)` in every component, I learned to encapsulate this logic in a custom hook. This makes consuming the context simpler, reusable, and less verbose across the application.

```js
export default function useTheme() {
    return useContext(ThemeContext);
}
```

By doing this, I created a more intuitive way to access the theme context within any component by simply calling the `useTheme()` hook.

### 4. **Key Takeaways**
- **Encapsulation and Simplicity**: Encapsulating `useContext` in a custom hook like `useTheme` reduced repetition and made the codebase cleaner.
- **Modularity**: Separating the provider (`ThemeProvider`) and consumer (`useTheme()`) logic made it easier to manage the context across different parts of the application.
- **Initialization**: I learned the importance of initializing the context with appropriate default values to avoid potential `undefined` behavior when context consumers access it without a provider.

### 5. **Applications of This Approach**
This structure allowed me to easily manage global state related to theming. The approach can be extended to other global states like user authentication, language preferences, and more.

In conclusion, this method of defining and consuming context helped me build a more modular and maintainable React application with better code readability and consistency.

## remember to change config in tailwind

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  darkMode: "class",
  theme: {
    extend: {},
  },
  plugins: [],
}

