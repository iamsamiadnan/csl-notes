A React component re-renders when certain conditions are met, usually because of updates to state, props, or context. Here's a detailed breakdown of the common triggers:

---

### 1. **State Changes**

- When you update a component’s state using `setState` (for class components) or the state updater function returned by `useState` (for functional components), React schedules a re-render of that component.
- **Example**:
    
    ```jsx
    function Counter() {
      const [count, setCount] = React.useState(0);
      return (
        <button onClick={() => setCount(count + 1)}>
          Clicked {count} times
        </button>
      );
    }
    ```
    
    Every time `setCount` is called, the component re-renders.

---

### 2. **Props Changes**

- When a parent component re-renders and passes new props to a child component, the child component will also re-render by default (even if the props haven't changed in value).
- **Example**:
    
    ```jsx
    function Parent() {
      const [value, setValue] = React.useState(0);
      return <Child prop={value} />;
    }
    
    function Child({ prop }) {
      console.log("Child rendered");
      return <div>{prop}</div>;
    }
    ```
    
    Here, if `setValue` is called in the parent, `Child` will re-render because its `prop` may have changed.

---

### 3. **Context Changes**

- If a component consumes context via `useContext` or `Context.Consumer`, it will re-render whenever the context value changes.
- **Example**:
    
    ```jsx
    const ThemeContext = React.createContext();
    
    function App() {
      const [theme, setTheme] = React.useState("dark");
      return (
        <ThemeContext.Provider value={theme}>
          <Child />
        </ThemeContext.Provider>
      );
    }
    
    function Child() {
      const theme = React.useContext(ThemeContext);
      return <div>The current theme is {theme}</div>;
    }
    ```
    
    Changing the `theme` state in `App` triggers a re-render of `Child`.

---

### 4. **Parent Component Re-renders**

- If a parent component re-renders, all its children re-render unless they are optimized using techniques like `React.memo` or `shouldComponentUpdate`.
- **Solution**: Use `React.memo` for functional components or `shouldComponentUpdate` for class components to optimize unnecessary re-renders.

---

### 5. **Force Updates**

- Using `forceUpdate` (in class components) or workarounds in functional components can trigger a re-render even if state or props haven't changed. However, this should be avoided in most cases.
- **Example** (not recommended):
    
    ```jsx
    class MyComponent extends React.Component {
      forceRerender = () => this.forceUpdate();
      render() {
        return <button onClick={this.forceRerender}>Force Update</button>;
      }
    }
    ```
    

---

### 6. **Key Changes**

- If the `key` prop of a component changes, React treats it as a completely new component and will unmount the old one and mount the new one.
- **Example**:
    
    ```jsx
    function App() {
      const [key, setKey] = React.useState(1);
      return <Child key={key} />;
    }
    ```
    

---

### Optimization Techniques

If a component is re-rendering unnecessarily:

1. **React.memo**: Wrap functional components to prevent re-renders unless props actually change.
    
    ```jsx
    const Child = React.memo(function Child({ prop }) {
      console.log("Child rendered");
      return <div>{prop}</div>;
    });
    ```
    
2. **useMemo / useCallback**: Memoize values or functions passed as props.
3. **shouldComponentUpdate / PureComponent**: For class components, prevent unnecessary updates.
4. **Avoid inline functions or objects**: These are recreated on every render, causing child components to re-render.
