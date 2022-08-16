# Advanced State with Reducers

## useReducer

     const [state, dispatch] = useReducer(reducer, initialArg, init);

useReducer is an alternative to useState. Accepts a reducer of type (state, action) and returns the current state paired with a dispatch method. UseReducer lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

There are two ways to use the useReducer function - you may choose either one of them depending on the use case. The simplest way is to pass the initial state as a second argument to the function 'useReducer', rather than the more complicated 'initializeState' function.

- pass the initial state as a second argument:

    const [state, dispatch] = useReducer(
    reducer,
    {count: initialCount}
     );

- pass an init function as the third argument:

    function init(initialCount) {
         return {count: initialCount};
    }

    function reducer(state, action) {
        switch (action.type) {
          case 'increment':
          return {count: state.count + 1};
          case 'decrement':
          return {count: state.count - 1};
          case 'reset':
          return init(action.payload);
          default:
          throw new Error();
        }
    }
    function Counter({initialCount}) {
        const [state, dispatch] = useReducer(reducer, initialCount, init);
        return (
              <>
               Count: {state.count}
               <button
                onClick={() => dispatch({type: 'reset', payload: initialCount})}>
                Reset
               </button>
               <button onClick={() => dispatch({type: 'decrement'})}>-</button>
               <button onClick={() => dispatch({type: 'increment'})}>+</button>
             </>
        );
    }

If you return the same value from a Reducer Hook as the current state, React will bail out without rendering the children or firing effects. Use useMemo to optimize expensive calculations while rendering.

The reducer function receives an action, which is executed by a dispatch function. The state is the data we are manipulating, and the action is the current state of the data that we want to manipulate.

The reducer returns an array that holds the current state and a dispatch function to which you can pass an action for each state change - similar to Redux's useReducer pattern.

useReducer Hook is similar to the useState Hook for managing state in Redux. It accepts a reducer function as its first parameter and the initial state as the second. In Redux, the dispatch function sends the action object to the store instead of the reducer.

The reducer function in Redux is a key component of the React programming language.
