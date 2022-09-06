# Redux - Combined Reducers

## Using combineReducers

### Core Concepts

CombineReducers is a utility that helps simplify the most common use case for Redux reducers. It does not "call all reducers" when dispatching an action, but rather wraps them together. Use it at all levels of your reducer structure, not just the root reducer.

### Defining State Shape

combineReducers takes an object full of slice reducer functions, and creates a corresponding state object with the same keys. The correlation between these names is not always apparent, especially when using ES6 features such as default module exports and object literal shorthands.

Example :

        // reducers.js
    export default theDefaultReducer = (state = 0, action) => state

    export const firstNamedReducer = (state = 1, action) => state

    export const secondNamedReducer = (state = 2, action) => state

    // rootReducer.js
    import { combineReducers, createStore } from 'redux'

    import theDefaultReducer, {
    firstNamedReducer,
    secondNamedReducer
    } from './reducers'

    // Use ES6 object literal shorthand syntax to define the object shape
    const rootReducer = combineReducers({
    theDefaultReducer,
    firstNamedReducer,
    secondNamedReducer
    })

    const store = createStore(rootReducer)
    console.log(store.getState())
    // {theDefaultReducer : 0, firstNamedReducer : 1, secondNamedReducer : 2}

Using the ES6 shorthand for defining an object literal, the key names in the resulting state are the same as the variable names from the imports. This may not always be the desired behavior, and is often a cause of confusion for those who aren't as familiar with ES6 syntax.

A better usage might look like:

    import { combineReducers, createStore } from 'redux'

    // Rename the default import to whatever name we want. We can also rename a named import.
    import defaultState, {
    firstNamedReducer,
    secondNamedReducer as secondState
    } from './reducers'

    const rootReducer = combineReducers({
    defaultState, // key name same as the carefully renamed default export
    firstState: firstNamedReducer, // specific key name instead of the variable name
    secondState // key name same as the carefully renamed named export
    })

    const reducerInitializedStore = createStore(rootReducer)
    console.log(reducerInitializedStore.getState())
    // {defaultState : 0, firstState : 1, secondState : 2}

## combineReducers(reducers)

The combineReducers() helper function turns an object whose values are different reducing functions into a single reducing function you can pass to createStore. As your app grows more complex, you'll want to split your reducing function into separate functions, each managing independent parts of the state.

You can control state key names by using different keys for the reducers in the passed object. For example, you may call combineReducers({ todos: myTodosReducer, counter: myCounterReducer) for the state shape to be { todos, counter }.

combineReducers() attempts to enforce some rules that you don't have to follow if you write the root reducer manually. It will check your reducers by passing undefined to them, even if you never intend for them to receive this as state in your code.

You may call combineReducers at any level of the reducer hierarchy, and it doesn't have to happen at the top. You may use it again to split the child reducers that get too complicated into independent grandchildren, and so on. It's a helper function, not a replacement for writing a root reducing function.

[Multiple Reducers Example](https://www.youtube.com/watch?v=gBER4Or86hE)
