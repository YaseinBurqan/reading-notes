# Component Based UI

The smallest `React` example looks like this:

    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(<h1>Hello, world!</h1>);

It displays a heading saying “Hello, world!” on the page.

## what is React ?

React is a JavaScript library based on `Javascript` language.

#

## what is JSX ?

example:

    const element = <h1>Hello, world!</h1>;

JSX tags syntax is neither a string nor HTML, it is a syntax extension to JavaScript.

#

### Embedding Expressions in JSX

- You can put any valid JavaScript expression inside the curly braces in JSX.

example:

    const name = 'Josh Perez';
    const element = <h1>Hello, {name}</h1>;

In the example, we declare a variable called name and then use it inside JSX by wrapping it in curly braces.

#

### JSX is an Expression Too

- After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:.

example:

    function getGreeting(user) {
        if (user) {
                return <h1>Hello, {formatName(user)}!</h1>;
                  }
        return <h1>Hello, Stranger.</h1>;
    }

#

### Specifying Attributes with JSX

You can use quotes to specify string literals as attributes:

    const element = <a href="https://www.reactjs.org"> link </a>;

You can also use curly braces to embed a JavaScript expression in an attribute:

    const element = <img src={user.avatarUrl}></img>;

Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute. You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute.

Warning :

    Since JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

#

### Specifying Children with JSX

If a tag is empty, you may close it immediately with />, like XML:

    const element = <img src={user.avatarUrl} />;

JSX tags can contain children:

    const element = (
        <div>
        <h1>Hello!</h1>
        <h2>Good to see you here.</h2>
        </div>
    );

#

### JSX Prevents Injection Attacks

By default, React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent XSS (cross-site-scripting) attacks.

#

### JSX Represents Objects

Babel compiles JSX down to React.createElement() calls.

React.createElement() performs a few checks to help you write bug-free code but essentially it creates an object.

React elements : You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.

#

## Rendering Elements

### what is Rendering Elements

An element describes what you want to see on the screen.

#

### Rendering an Element into the DOM

    <div id="root"></div>

We call this a “root” DOM node because everything inside it will be managed by React DOM.

To render a React element, first pass the DOM element to ReactDOM.createRoot(), then pass the React element to root.render():

    const root = ReactDOM.createRoot(document.getElementById('root'));
    const element = <h1>Hello, world</h1>;
    root.render(element);

### Updating the Rendered Element

React elements are immutable. Once you create an element, you can’t change its children or attributes.

    the only way to update the UI is to create a new element, and pass it to root.render().

#

### React Only Updates What’s Necessary

React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

    Even though we create an element describing the whole UI tree on every tick, only the text node whose contents have changed gets updated by React DOM.
