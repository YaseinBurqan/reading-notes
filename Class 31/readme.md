# Context API

In a typical React application, data is passed top-down (parent to child) via props. This can be cumbersome for certain types of props, such as locale preference or UI theme. Context provides a way to share values between components without having to explicitly pass a prop through every level of the tree.

1.When to Use Context
2.Before You Use Context
3.API

- React.createContext
- Context.Provider
- Class.contextType
- Context.Consumer
- Context.displayName

4.Examples

- Dynamic Context
- Updating Context from a Nested Component
- Consuming Multiple Contexts

5.Caveats
6.Legacy API

### When to Use Context?

Context is a type of data that can be considered "global" for a tree of React components. For example, in the code below we manually thread through a "theme" prop in order to style the Button component. Using context we can avoid passing props through intermediate elements.

Component composition is often a simpler solution than context. Use context sparingly if you only want to avoid passing some props through many levels. Inversion of control can make your code cleaner in many cases by reducing the amount of props you need to pass through your application.

### API

- React.createContext

    const MyContext = React.createContext(defaultValue);

The defaultValue argument is only used when a component does not have a matching Provider above it in the tree. This can be helpful for testing components in isolation without wrapping them. Note: passing undefined as a Provider value does not cause consuming components to use defaultValue.

- Context.Provider

    <MyContext.Provider value={/*some value*/}>

Every Context object comes with a Provider React component that allows consuming components to subscribe to context changes. Providers can be nested to override values deeper within the tree. Changes are determined by comparing the new and old values using the same algorithm as Object.is for objects.

    The way changes are determined can cause some issues when passing objects as value: see Caveats.

- Class.contextType

        class MyClass extends React.
        Component {
        componentDidMount() {
        let value = this.context;
        }
        componentDidUpdate() {
        let value = this.context;
        }
        componentWillUnmount() {
        let value = this.context;
        }
        render() {
        let value = this.context;
        }
        }
        MyClass.contextType = MyContext;

The contextType property on a class can be assigned a Context object created by React. Using this property lets you consume the nearest current value of that Context type using this.context. You can reference this in any of the lifecycle methods including the render function.

- Context.Consumer

      <MyContext.Consumer>
      {value => /*render something based on the context value*/}
      </MyContext.Consumer>

Using this component lets you subscribe to a context within a function component. The function receives the current context value and returns a React node. For more information about the 'function as a child' pattern, see render props.

- Context.displayName

        const MyContext = React.createContext(/*some value*/);
        MyContext.displayName = 'MyDisplayName';

        <MyContext.Provider> // "MyDisplayName.Provider" in DevTools
        <MyContext.Consumer> // "MyDisplayName.Consumer" in DevTools

### Updating Context from a Nested Component

Sometimes it is necessary to update the context from a component that is nested somewhere deeply in the tree. In this case you can pass a function down through the context to allow consumers to update their own context using the same code as you did for the previous version of this article.

### Consuming Multiple Contexts

You might want to consider creating your own render prop component that provides both a context consumer and a render prop. To keep context re-rendering fast, React needs to make each context consumer a separate node in the tree - you could create a separate render prop for each value.

### Caveats

There are some gotchas that could trigger unintentional renders in consumers when a provider's parent re-renders. For example, the code below will re-render all consumers every time the Provider re-ends because a new object is always created for value.

    class App extends React.Component {
    render() {
        return (
        <MyContext.Provider value={{something: 'something'}}>
            <Toolbar />
        </MyContext.Provider>
        );
      }
    }

To get around this, lift the value into the parent’s state:

    class App extends React.Component {
        constructor(props) {
            super(props);
            this.state = {
            value: {something: 'something'},
            };
    }

        render() {
            return (
            <MyContext.Provider value={this.state.value}>
                <Toolbar />
            </MyContext.Provider>
            );
        }
    }
