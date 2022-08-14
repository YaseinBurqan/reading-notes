# useState() Hook

## Introducing Hooks

    Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

### No Breaking Changes

    note that Hooks are:

    Completely opt-in. You can try Hooks in a few components without rewriting any existing code.
    
    But you don’t have to learn or use Hooks right now if you don’t want to.

    100% backwards-compatible. Hooks don’t contain any breaking changes.
    
    Available now. Hooks are now available with the release of v16.8.0.

Hooks don’t work inside classes.

## Hooks at a Glance : Hooks API

    Hooks are backwards-compatible. This page provides an overview of Hooks for experienced React users. This is a fast-paced overview.

Hooks are functions that let you “hook into” React state and lifecycle features from function components.

You can create your own Hooks to reuse stateful behavior between different components.

### Rules of Hooks

- Only call Hooks at the top level. Don’t call Hooks inside loops, conditions, or nested functions.

- Only call Hooks from React function components. Don’t call Hooks from regular JavaScript functions. (There is just one other valid place to call Hooks — your own custom Hooks.

## Using the State Hook

What do we pass to useState as an argument?

- The only argument to the useState() Hook is the initial state.

What does useState return?

- It returns a pair of values: the current state and a function that updates it. This is why we write const [count, setCount] = useState().

    Example of normal Hook
      <p>You clicked {this.state.count} times</p>

    Example of useState
      <p>You clicked {count} times</p>


