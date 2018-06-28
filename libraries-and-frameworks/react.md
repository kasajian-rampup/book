# React

## Notes

### Prerequisite

JavaScript and HTML

### Getting Started

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

Now let's do the same thing with React.  \(the following will expose the React and ReactDOM global variables\):

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

> **Summary**: elements now created with Reac.createElement.

Review the difference in the script code between the two snippets. 

Analyzing what the 'element' object in the debugger, and notice there's a 'props' property, which has the same properties as the second argument to Reac.createElement, but with one more property called 'children' that's the third argument.  However, if more than three arguments are passed in, then 'props.children' becomes an array.  That means this:

```javascript
const element = React.createElement('div',
    {className: 'container'}, 'Hello World');
```

can be written as:

```javascript
const element = React.createElement('div',
    {className: 'container', children: 'Hello World'} );
```

```text
---
JSX version

<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
<script type="text/babel">
const rootElement = document.getElementById('root');
const element = <div className="container">Hello Word</div>
ReactDOM.render(element, rootElement);
</script>

Summary: in the script, the element uses JSX syntax.
const element = <div className="container">Hello Word</div>
is exactly the same as:
const element = React.createElement('div',
    {className: 'container', children: 'Hello World'} );
We also had to include babel, and change our script's <script> tag to
reference babel.

Let's externalize the "Hello World" from the JSX div.  BEFORE:
const element = <div className="container">Hello Word</div>
AFTER:
const content = 'Hello World'
const element = <div className="container">{content}</div>
Inside the interpolated section in braces, we can put any javascript:
const element = <div className="container">{(())=>content)()}</div>

const myClassName = 'container'
You can also do it for className props or any prop
const element = <div className={myClassName}>{content}</div>

Props object:
Something common with JSX is creation of a props object.
const props = {
    className: 'container',
    children: 'Hello World'
}
const element = <div {...props}/>

spread syntax:
func call:
f(...x); = f.apply(null, x); // Passes array into multiple arguments.

array literals:
[...x, 1, 2]  // merge array x into array.

object literal (new to ES2018)
let o = { ...x };

rest syntax:
function f(...a) {} // arguments come in as an array.

also can be destructured:
function f(...[a, b, c]) {}

----
Let's say we have this:
const element = <div {...props}/>
and we want to override the class name rather than use the one in props.
We can try:
const element = <div className="my-class" {...props}/>
but that doesn't work because props comes after the className.
We can change it to:
const element = <div {...props} className="my-class" />
We can override other props like, the children prop:
const element = <div {...props} children="Hi there" />
or we can do:
const element = <div {...props}>Hi there</div>
----
const rootElement = document.getElementById('root');
const element = (
    <div className="container">
        <div>Hello Word</div>
        <div>Hello Word</div>
    </div>
)
ReactDOM.render(element, rootElement);

There's two div's tht are identical.  We don't want to repeat ourselves,
so we can extract:

const helloWorld = <div>Hello Word</div>
const element = (
    <div className="container">
        {helloWorld}
        {helloWorld}
    </div>
)

But what if we want one to say "hello" and the other "good-bye" world?
Let's rename 'helloWorld' to 'message' and make a function.

const message = (props) => <div>{props.msg}</div>
const element = (
    <div className="container">
        {message({msg: 'Hello World'})}
        {message({msg: 'Goodbye World'})}
    </div>
)

Another way, capitalize message:

const Message = (props) => <div>{props.msg}</div>
const element = (
    <div className="container">
	<Message msg='Hello World' />
	<Message msg='Goodbye World' />
    </div>
)

Now let's change the msg prop to children prop.

const Message = (props) => <div>{props.children}</div>
const element = (
    <div className="container">
	<Message children='Hello World' />
	<Message children='Goodbye World' />
    </div>
)

And since 'children' is a well known prop, we can use the more terse JSX syntax:
const Message = (props) => <div>{props.children}</div>
const element = (
    <div className="container">
	<Message>Hello World</Message>
	<Message>Goodbye World</Message>
    </div>
)

```



