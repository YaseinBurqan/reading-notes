# Redux - Additional Topics

The Redux Toolkit package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

- "Configuring a Redux store is too complicated"
- "I have to add a lot of packages to get Redux to do anything useful"
- "Redux requires too much boilerplate code"

"Redux Toolkit" can help you make your Redux code better. It includes a powerful data fetching and caching capability that we've dubbed "RTK Query". It's included in the package as a separate set of entry points. These tools should be beneficial to all Redux users.

## Using Create React App What's Included

Redux Toolkit includes these APIs:

configureStore(): wraps createStore to provide simplified configuration options and good defaults. It can automatically combine your slice reducers, adds whatever Redux middleware you supply, includes redux-thunk by default, and enables use of the Redux DevTools Extension.
createReducer(): that lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements. In addition, it automatically uses the immer library to let you write simpler immutable updates with normal mutative code, like state.todos[3].completed = true.
createAction(): generates an action creator function for the given action type string. The function itself has toString() defined, so that it can be used in place of the type constant.
createSlice(): accepts an object of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.
createAsyncThunk: accepts an action type string and a function that returns a promise, and generates a thunk that dispatches pending/fulfilled/rejected action types based on that promise
createEntityAdapter: generates a set of reusable reducers and selectors to manage normalized data in the store
The createSelector utility from the Reselect library, re-exported for ease of use.

### RTK Query

RTK Query is built on top of the Redux Toolkit core for its implementation, using Redux internally for its architecture. It is intended to simplify common cases for loading data in a web application. It works flawlessly with the Redux DevTools browser extension to traverse and replay a timeline of your request & cache behavior.

### What's included

RTK Query includes these APIs:

createApi(): The core of RTK Query's functionality. It allows you to define a set of endpoints describe how to retrieve data from a series of endpoints, including configuration of how to fetch and transform that data. In most cases, you should use this once per app, with "one API slice per base URL" as a rule of thumb.
fetchBaseQuery(): A small wrapper around fetch that aims to simplify requests. Intended as the recommended baseQuery to be used in createApi for the majority of users.
<ApiProvider />: Can be used as a Provider if you do not already have a Redux store.
setupListeners(): A utility used to enable refetchOnMount and refetchOnReconnect behaviors.
See the RTK Query Overview page for more details on what RTK Query is, what problems it solves, and how to use it.

## MobX

State is the heart of each application and there is no quicker way to create buggy, unmanageable applications than by producing an inconsistent state. Many state management solutions try to restrict the ways in which you can modify state. But this introduces new problems; data needs to be normalized, referential integrity can no longer be guaranteed and it becomes impossible to use powerful concepts like classes.

These are the state, or data, of your application, and actions, which are the things that alter the state. The main difference is that actions don't produce a value, instead they run automatically to perform some kind of task.

The TodoStore has to become observable so that MobX can track all the changes that are being made. The completedTodosCount property could be derived automatically from the todo list. By using the observable and computed annotations we can introduce observable properties on an object.

### Making React reactive

React components are (despite their name) not reactive out of the box. The observer HoC wrapper from the mobx-react-lite package fixes that by basically wrapping the React component in autorun. This is conceptually not different from what we did with the report before.

### Working with references

With MobX there is no need to normalize data first and to write selectors to make sure our components will be updated. In the previous listings you might have noticed that there is an assignee property on the todos. These changes will be picked up automatically by the TodoView.

### Asynchronous actions

Just press the the button (multiple times) to emulate asynchronously loading new todo items:. The code behind that is really straightforward. We start with updating the store property pendingRequests to have the UI reflect the current loading status. Once loading is finished, we update the todos of the store and decrease the pending Requests counter again.

Since everything in our small Todo application is derived from the state, it really doesn't matter when state is changed. Just press the button (multiple times) to emulate as synchronous loading.

## HookState

Code samples in each section are self-contained, complete and interactive.
There is a Todo-list-like complete demo application built with Hookstate. It gives an example of how to organise your project.
Type inference of the API functions supports any complexity of data structures of your states.

It aims to keep the core library as small as possible but still feature-rich to address most of problems in state management. You can also write your own plugins: it is easy and gives a lot of power.

## [Tutorial](https://redux-toolkit.js.org/tutorials/overview)
