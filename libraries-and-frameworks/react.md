# React

## Evolving to React

This entire section is about taking you step-by-step from normal HTML / JavaScript way of doing things \(without any frameworks\) to slowly evolving to using React, so that you have an opportunity to understand the purpose of each each step.

### Prerequisite

**Technology to be somewhat familiar with:**

* JavaScript 5.x, including the _spread_ and _rest_ operators.
* HTML
* Chrome

**Tools:**  No special tools needed.  Use your favorite text editor.   Examples use a single html file from "_download this HTML file_" of the reactjs.org getting-started page.

### Getting Started

This entire section is about taking you step-by-step from normal HTML / JavaScript way of doing things \(without any frameworks\) to slowly evolving to using React, so that you have an opportunity to understand the purpose of each each step.

Let's say we have an html file:

```markup
<div id='root'></div>
<script type="text/javascript">
    const rootElement = document.getElementById('root');
    const element = document.createElement('div');
    element.textContent = 'Hello World';
    element.className = 'container';
    rootElement.appendChild(element);
</script>
```

> **Summary**: append a new child div to the root with some text content.

Now let's do the same thing with React.  \(the following will expose the `React` and `ReactDOM` global variables\):

```markup
<div id='root'></div>
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<script type="text/javascript">
    const rootElement = document.getElementById('root');
    const element = React.createElement('div',
        {className: 'container'}, 'Hello World');
    ReactDOM.render(element, rootElement);
</script>
```

> **Summary**: elements now created with `React.createElement`.

Review the difference in the script code between the two snippets. 

Analyzing what the `element` object in the debugger, and notice there's a 'props' property, which has the same properties as the second argument to `Reac.createElement`, but with one more property called `children` that's the third argument.  However, if more than three arguments are passed in, then `props.children` becomes an array.  That means this:

```javascript
const element = React.createElement('div',
    {className: 'container'}, 'Hello World');
```

can be written as:

```javascript
const element = React.createElement('div',
    {className: 'container', children: 'Hello World'} );
```

### Here's the JSX version

```jsx
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
<script type="text/babel">
    const rootElement = document.getElementById('root');
    const element = <div className="container">Hello Word</div>
    ReactDOM.render(element, rootElement);
</script>
```

> **Summary:** in the script, the element uses JSX syntax.

```jsx
const element = <div className="container">Hello Word</div>
```

is exactly the same as:

```jsx
const element = React.createElement('div',
    {className: 'container', children: 'Hello World'} );
```

We also had to include Babel, and change our script's tag to reference babel.  This allows you to use JSX as well as newer JavaScript syntax which may not be available in your browser by default.

Let's externalize the "Hello World" from the JSX `Div`.

BEFORE:

```jsx
const element = <div className="container">Hello Word</div>
```

AFTER:

```javascript
const content = 'Hello World'
const element = <div className="container">{content}</div>
```

Inside the interpolated section in braces, we can put any JavaScript:

```jsx
const element = <div className="container">{(())=>content)()}</div>
```

You can also do it for `className` props or any prop:

```jsx
const myClassName = 'container'
const element = <div className={myClassName}>{content}</div>
```

### Props

Speaking of props, a little about the Props object.   Something common with JSX is creation of a props object. 

```jsx
const props = {
    className: 'container',
    children: 'Hello World'
}
const element = <div {...props}/>
```

The `...` in `const element = <div {...props}/>` is a way inserting the `props` object into the `div`.  This allows us to use the props object as-is, or augment it by adding our own properties.  If we wanted to override the class name rather than use the one in props, we could try:

```jsx
const element = <div className="my-class" {...props}/>
```

That's close, but it won't work if `props` already has `className` defined.  Since `props` comes after our definition of `className`, it overrides it.  Changing it so that we specify `className` _after_ merging in props, fixes it:

```jsx
const element = <div {...props} className="my-class" />
```

We can also override other props, like the children:

```jsx
const element = <div {...props} children="Hi there" />
```

which, if you recall, is the same as:

```jsx
const element = <div {...props}>Hi there</div>
```

### Refactor to a Component

Now let's say we have the following code, with two `div`s that are identical:

```jsx
const rootElement = document.getElementById('root');
const element = (
    <div className="container">
        <div>Hello Word</div>
        <div>Hello Word</div>
    </div>
)
ReactDOM.render(element, rootElement);
```

We don't want to repeat ourselves,so we can extract:

```jsx
const helloWorld = <div>Hello Word</div>
const element = (
    <div className="container">
        {helloWorld}
        {helloWorld}
    </div>
)
```

But what if we want one to say "hello" and the other "good-bye" world?  Let's rename the variable `helloWorld` to `message` and turn it into a function.

```jsx
const message = (props) => <div>{props.msg}</div>
const element = (
    <div className="container">
        {message({msg: 'Hello World'})}
        {message({msg: 'Goodbye World'})}
    </div>
)
```

The syntax `{message({msg: 'Hello World'})}` is not very HTMLish.  It would be better if the syntax looked like this: `<Message msg='Hello World' />`

All you have to do capitalize message, and it will work.  Below code is the same result as the above.

```jsx
const Message = (props) => <div>{props.msg}</div>
const element = (
    <div className="container">
	<Message msg='Hello World' />
	<Message msg='Goodbye World' />
    </div>
)
```

Now let's rename the `msg` prop to `children` prop:

```jsx
const Message = (props) => <div>{props.children}</div>
const element = (
    <div className="container">
	<Message children='Hello World' />
	<Message children='Goodbye World' />
    </div>
)
```

Since JSX treats a prop named `children` in a special way, `<Message children='Hello World' />` can be expressed as: `<Message>Hello World</Message>`, it makes it look more like HTML.

We just created a simple React Component called `Message`:

```jsx
const Message = (props) => <div>{props.children}</div>
const element = (
    <div className="container">
	<Message>Hello World</Message>
	<Message>Goodbye World</Message>
    </div>
)
ReactDOM.render(element, document.getElementById('root'));
```

### Class Components

This React component is a "function component" because it's defined using a function.  Another type of component is "class component", which is defined using a class.  Let's look at the difference.

Here's a simple function component:

```jsx
function HelloComponent() {
    return (<div>Hello</div>);
}
```

Here's the same thing as a class component:

```jsx
class HelloComponent extends React.Component {
    render() {
        return (<div>Hello</div>);
    }
}
```

Both of these snippets do the same thing.  The difference is that a class components can also keep internal state, whereas a function component cannot.

Let's create a component with a button that will flash the days of the week every time you click it.  Starting with a simple class component with a button where we can specify the label as an attribute:

```jsx
class FlashButton extends React.Component {
  render() {
    return (<button>{this.props.label}</button>);
  }
}

const element = ( <FlashButton label='Flash Weekdays'/> )
ReactDOM.render(element, document.getElementById('root'));
```

So far the component just has a button whose label we can specify.  Take note that `props` is no longer being passed as a parameter, as we had for function components.   `props` is now accessed as as a property of the component, access by `this.` syntax.

Each time the button is clicked, we want to show the next day of the week, which means we must maintain state.  To to this, we can store our state in the `state` property of the component.  Let's first initialize the state to a default value.  We do this in the constructor of the component:

```jsx
class FlashButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date().getTime()};
  }
```

The `state` property is an object that contains the state defined by the component.  You want to put into this object any state that affects how the component is displayed.  You can store internal state as regular properties of the component.   In this case, we want to store the current date so that we can increment to the next date every time the user clicks the button.

Let's display the day of the week as the label of the button.  This means we don't need to pass in the label as a prop.   We'll define a utility method to get the name of the day of the week from the `date` property of the `state` object:

```jsx
class FlashButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date().getTime()};
  }
  getDayOfWeek() {
    return new Date(this.state.date).toLocaleString("en-US", { weekday: "long" });
  }
  render() {
    return (<button>{this.getDayOfWeek()}</button>);
  }
}
```

#### Click event

Let's define a click event on the button that will increment the date by one day.  In React, when an event is a method on the component, we'll need to use the JavaScript `bind()` method to bind the component to the method.   Let's look at that syntax first, and then we'll see an alternate syntax that can avoid the explicit use of `bind()`

```jsx
  constructor(props) {
    super(props)
    this.state = { date: new Date().getTime()};
    this.handleClick = this.handleClick.bind(this)
  }

  handleClick() {
     // date increment code goes here
  }
  render() {
    return (
      <button onClick={this.handleClick}>
        {this.getDayOfWeek()}
      </button>
      );
  }
```

First note the `onClick` event on the button html referring to `this.handleClick`.   Inside of the `handleClick()` method, you wouldn't be able to access `this.state` if you didn't have the call to `bind()` in the constructor.  However, we can rewrite the method as an arrow-function which automatically binds it to the component, eliminating the necessity to call `bind()` in the constructor:

```jsx
  constructor(props) {
    super(props)
    this.state = { date: new Date().getTime()};
  }
  handleClick = () => {    
     // date increment code goes here
  }
```

#### Setting state

Let's do one more simplification by taking advantage of the newer JavaScript syntax for initializing properties, which eliminates the need for the constructor:

BEFORE:

```jsx
  constructor(props) {
    super(props)
    this.state = { date: new Date().getTime()};
  }
```

AFTER:

```jsx
  state = { date: new Date().getTime()};
```

Now let's add the date-increment code to `handleClick`.  Changing the state requires a call to the `setState()` method.  Although we were able to set the `state` property directly when we initialized it, we cannot do this once the component starts rendering.   Instead we call the `setState()` method, passing in a new `state` object.  It's best to think of the `state` object as immutable.  Once it's set, don't change it -- instead, create a new one and pass it to `setState()`.   Example:

```jsx
  handleClick = () => {    
    const d = new Date(this.state.date);
    d.setDate(d.getDate() + 1)    
    this.setState({
      date: d.getTime()
    });
  }
```

But there's one problem.   Because we are both reading and writing the `state` property, there's a potential for a race-condition which can be avoided by using an alternate version of `setState()` .  To use this other version, we pass it a function which is invoked with the previous state value.  You only need to do this if your update depends on the current state.  So let's do that:

```jsx
  handleClick = () => {    
    this.setState(prevState => {
      const d = new Date(prevState.date);
      d.setDate(d.getDate() + 1)    
      return {
        date: d.getTime()
      }
    });
  }
```

#### Final FlashButton component

We now have a component which can be run -- each time you click the button, the text of the button changes to the next day of the week:

```jsx
class FlashButton extends React.Component {
  state = { date: new Date().getTime()};

  getDayOfWeek() {
    return new Date(this.state.date).toLocaleString("en-US", { weekday: "long" });
  }
  handleClick = () => {    
    this.setState(prevState => {
      const d = new Date(prevState.date);
      d.setDate(d.getDate() + 1)    
      return {
        date: d.getTime()
      }
    });
  }
  render() {
    return (
      <button onClick={this.handleClick}>
        {this.getDayOfWeek()}
      </button>
      );
  }
}

const element = ( <FlashButton label="Flash"/> )
ReactDOM.render(element, document.getElementById('root'));
```

### Multiple components

Up to this point, we've rendering a single component via react.  In a normal application, you will have multiple components that interact with each other.   Let's create a Flash component based on the FlashButton component, but which displays the flash text in a separate `Div`, as opposed to on the button label.   Let's bring back our first component, Message to do that:

```jsx
const Message = (props) => <div>{props.children}</div>
```

Now we have two components, `FlashButton` and `Message`.  Since we can only pass in a single component to `ReactDOM.render`,  let's create a new `Flash` component that will be composed of the these two components:

```jsx
class Flash extends React.Component {
  render() {
    return (
      <div>
        <FlashButton/>
        <Message>text</Message>
      </div>
    );
  }
}

const element = ( <Flash label="Flash"/> )
ReactDOM.render(element, document.getElementById('root'));
```

What we want is when the user clicks on the button, the flash text to appear in the `Message` component.   So how can the `Message` component access the state in the `FlashButton` component?  We can't.  We have to move the state to the new `Flash` component so that child component can access it from a common place if they need to.   So let's move the state to the `Flash` component and introduce a `flashNext` method.

```jsx
class Flash extends React.Component {
  state = { date: new Date().getTime()};

  flashNext = () => {
    this.setState(prevState => {
      const d = new Date(prevState.date);
      d.setDate(d.getDate() + 1)    
      return {
        date: d.getTime()
      }
    });
  };
```

Now we can bind the `flashNext()` method to the `onClick` event of `FlashButton`  by passing the method as a prop to the `FlashButton` component:

```jsx
<FlashButton flashNext={this.flashNext}/>
```

```jsx
class FlashButton extends React.Component {
  render() {
    return (
      <button onClick={this.props.flashNext}>Flash</button>
    );
  }
}
```

Then we can show the flash text using the `Message` component.

```jsx
<Message>{this.getDayOfWeek()}</Message>
```

The final Flash Component that can be used is as follows:

```jsx
class FlashButton extends React.Component {
  render() {
    return (
      <button onClick={this.props.flashNext}>Flash</button>
    );
  }
}

const Message = (props) => <div>{props.children}</div>

class Flash extends React.Component {
  state = { date: new Date().getTime()};

  getDayOfWeek() {
    return new Date(this.state.date).toLocaleString("en-US", { weekday: "long" });
  }

  flashNext = () => {
    this.setState(prevState => {
      const d = new Date(prevState.date);
      d.setDate(d.getDate() + 1)    
      return {
        date: d.getTime()
      }
    });
  };

  render() {
    return (
      <div>
        <FlashButton flashNext={this.flashNext}/>
        <Message>{this.getDayOfWeek()}</Message>
      </div>
    );
  }
}

const element = ( <Flash label="Flash"/> )
ReactDOM.render(element, document.getElementById('root'));
```

Technically the FlashButton component doesn't need be a class component since it doesn't have state.  It could be a function component and can be rewritten as follows:

```jsx
function FlashButton(props) {
  return (
    <button onClick={props.flashNext}>Flash</button>
  );
}
```

Or using a simpler syntax:

```jsx
const FlashButton = props => <button onClick={props.flashNext}>Flash</button>
```

