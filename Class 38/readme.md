# Redux - Asynchronous Actions

In this section, we'll see how to use the React-Redux library to let our React components interact with a Redux store. We'll update our todo app to fetch the todos from an API, and add new todos by saving them to the API.

We'll be using a fake in-memory REST API for our data (configured using the Mirage.js mock API tool). The project also includes a small HTTP API client object that exposes client.get() and client.post() methods, similar to popular HTTP libraries like axios. It's defined in src/api/client.js.

## Redux Middleware and Side Effects

Redux middleware were designed to enable writing logic that has side effects. They can do anything when it sees a dispatched action: log something, delay the action, make an async call, and more. Also, since middleware form a pipeline around the real store.dispatch function, this also means we could pass something that isn't an action object to dispatch.

### Using Middleware to Enable Async Logic

    import { client } from '../api/client'

    const delayedActionMiddleware = storeAPI => next => action => {
    if (action.type === 'todos/todoAdded') {
        setTimeout(() => {
        // Delay this action by one second
        next(action)
        }, 1000)
        return
    }

    return next(action)
    }

    const fetchTodosMiddleware = storeAPI => next => action => {
    if (action.type === 'todos/fetchTodos') {
        // Make an API call to fetch todos from the server
        client.get('todos').then(todos => {
        // Dispatch an action with the todos we received
        storeAPI.dispatch({ type: 'todos/todosLoaded', payload: todos })
        })
    }

    return next(action)
    }

It would be nice if we had a way to write any. async logic ahead of time, separate from the middleware itself. We could have our middleware check to see if the "action" is actually a function instead, and if it's a function, call the function right away.

Here's what that middleware might look like:

    const asyncFunctionMiddleware = storeAPI => next => action => {
    // If the "action" is actually a function instead...
    if (typeof action === 'function') {
        // then call the function and pass `dispatch` and `getState` as arguments
        return action(storeAPI.dispatch, storeAPI.getState)
    }

    // Otherwise, it's a normal action - send it onwards
    return next(action)
    }

And then we could use that middleware like this:

    const middlewareEnhancer = applyMiddleware(asyncFunctionMiddleware)
    const store = createStore(rootReducer, middlewareEnhancer)

    // Write a function that has `dispatch` and `getState` as arguments
    const fetchSomeData = (dispatch, getState) => {
    // Make an async HTTP request
    client.get('todos').then(todos => {
        // Dispatch an action with the todos we received
        dispatch({ type: 'todos/todosLoaded', payload: todos })
        // Check the updated store state after dispatching
        const allTodos = getState().todos
        console.log('Number of todos after loading: ', allTodos.length)
    })
    }

    // Pass the _function_ we wrote to `dispatch`
    store.dispatch(fetchSomeData)
    // logs: 'Number of todos after loading: ###'

## Redux Async Data Flow

We saw a diagram that represents the normal synchronous Redux data flow. When we add async logic to a Redux app, we add an extra step where middleware can run logic like AJAX requests, then dispatch actions. That makes the data flow look like this:

![](https://d33wubrfki0l68.cloudfront.net/08d01ed85246d3ece01963408572f3f6dfb49d41/4bc12/assets/images/reduxasyncdataflowdiagram-d97ff38a0f4da0f327163170ccc13e80.gif)

## Using the Redux Thunk Middleware

This is the framework that allows you to write code that does some delayed work for you without knowing what store you're using ahead of time.

## Fetching Todos from a Server

We need a way to load a list of todos from the server when the app starts up. We'll write a function that makes an AJAX call to our /fakeApi/todos endpoint. This function will request an array of todo objects, and then dispatch an action containing that array as the payload.

    import { client } from '../../api/client'

    const initialState = []

    export default function todosReducer(state = initialState, action) {
    // omit reducer logic
    }

    // Thunk function
    export async function fetchTodos(dispatch, getState) {
    const response = await client.get('/fakeApi/todos')
    dispatch({ type: 'todos/todosLoaded', payload: response.todos })
    }

### Saving Todo Items

We also need to update the server whenever we try to create a new todo item. Instead of dispatching the 'todos/todoAdded' action right away, we should make an API call to the server with the initial data. Since we're writing the thunk as a separate function, the code that makes the API call doesn't know what type of todo text it is supposed to be.

# What we learned?

In the last few weeks we've been working on improving our todo app so that we can fetch a list of todo items and save new ones. In the process, we saw how Redux middleware are used to let us make async calls and interact with the store by dispatching actions after the calls have completed.

import React from 'react'

import Header from './features/header/Header'
import TodoList from './features/todos/TodoList'
import Footer from './features/footer/Footer'

    function App() {
    return (
        <div className="App">
        <nav>
            <section>
            <h1>Redux Fundamentals Example</h1>
            </section>
        </nav>
        <main>
            <section className="medium-container">
            <h2>Todos</h2>
            <div className="todoapp">
                <Header />
                <TodoList />
                <Footer />
            </div>
            </section>
        </main>
        </div>
    )
    }

    export default App

### SUMMARY

Redux middleware were designed to enable writing logic that has side effects

- "Side effects" are code that changes state/behavior outside a function, like AJAX calls, modifying function arguments, or generating random values

Middleware add an extra step to the standard Redux data flow

- Middleware can intercept other values passed to dispatch
- Middleware have access to dispatch and getState, so they can dispatch more actions as part of async logic

The Redux "Thunk" middleware lets us pass functions to dispatch

- "Thunk" functions let us write async logic ahead of time, without knowing what Redux store is being used
- A Redux thunk function receives dispatch and getState as arguments, and can dispatch actions like "this data was received from an API response"

### [code assets](https://github.com/reduxjs/redux-thunk)
