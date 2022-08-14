# Reading: Component Lifecycle / useEffect Hook

The Effect Hook lets you perform side effects in function components:

    import React, { useState, useEffect } from 'react';

    function Example() {
    const [count, setCount] = useState(0);

    // Similar to componentDidMount and componentDidUpdate:
    useEffect(() => {
        // Update the document title using the browser API
        document.title = `You clicked ${count} times`;
    });

    return (
        <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
            Click me
        </button>
        </div>
    );
    }

### There are two common kinds of side effects in React components

- Effects Without Cleanup

    run some additional code after React has updated the DOM.

- Effects with Cleanup

     express side effects that don’t require any cleanup

## Recap

We’ve learned that useEffect lets us express different kinds of side effects after a component renders. Some effects might require cleanup so they return a function:

    useEffect(() => {
        function handleStatusChange(status) {
        setIsOnline(status.isOnline);
        }

        ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
        return () => {
        ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
        };
    });

Other effects might not have a cleanup phase, and don’t return anything.

    useEffect(() => {
    document.title = `You clicked ${count} times`;
    });

The Effect Hook unifies both use cases with a single API.
