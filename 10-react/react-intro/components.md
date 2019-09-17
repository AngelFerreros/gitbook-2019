# React Components

We saw a bit of how react works, and how babel works with react.

Now we will see one of the main concepts of React, the Component.

In the last example we saw that we can use react to render things just like we did in express and rails- where the HTML template is a kind of code mad-lib- You fill in the data where it needs to go in the page.

React does this at the base level, but we can also sub-divide each part of a page into `Component`s.

These are the sepearate logical pieces of any page.

![https://github.com/wdi-sg/react-intro/raw/master/images/templates-page.png](https://github.com/wdi-sg/react-intro/raw/master/images/templates-page.png)

![https://github.com/wdi-sg/react-intro/blob/master/images/components-page.png](https://github.com/wdi-sg/react-intro/blob/master/images/components-page.png?raw=true)

![https://github.com/wdi-sg/react-intro/blob/master/images/wireframe.png](https://github.com/wdi-sg/react-intro/blob/master/images/wireframe.png?raw=true)

![https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png](https://github.com/wdi-sg/react-intro/blob/master/images/wireframe_deconstructed.png?raw=true)


### Properties of Components
- separation of concerns
- nested / pass data down from parent
- F focused
- I independant
- R resuable
- S small
- T testable


### Babel standalone
Before we move to writing code, let's talk about the default tool we'll use until we learn the React build tools.

```
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
<script type="text/babel">
 ReactDOM.render(
    <p>hello world!</p>,
    document.getElementById('root')
 );
</script>
```

`babel-standalone` relies on a script tag type text/babel. It ingests everything inside that script tag, transpiles it and evals it.


If we pasted the jsx code above into the chrome dev tools console, without letting babel run first, we would get a syntax error.

## Writing a component
```
class List extends React.Component {
    render() {
        return (
          <ul>
            <li>Hello world</li>
          </ul>
        );
    }
}

ReactDOM.render(
    <List />,
    document.getElementById('root')
);
```

- `List` is a js "class" that inherits from React
- a component has certain methods like `render` that allow you to control it


### Component Properties
In react, a component takes data in and renders itself based on that data.

The data is passed from above in the parent component.

Let's start rendering a real list from data coming from outside the list itself.


```
class List extends React.Component {

    render() {
        let itemsElements = this.props.items.map(item => {
                              return <li>{item}</li>
                            });
        return (
          <ul>
            {itemsElements}
          </ul>
        );
    }
}

const listOfItems = [
  "apples",
  "bananas",
  "pineapple"
];

ReactDOM.render(
    <List items={listOfItems} />,
    document.getElementById('root')
);
```


#### Props
Props are the react way of passing data into your component.

When you specify your component you specify it's `props` just like an HTML attribute.
```
<List items={listOfItems} />
```

You can then access them from within the component using `this.props`


### Nesting Components
We mentioned that it's the nested structure of components using components that really makes react special.

Let's put our `<li>` tag data in it's own component.
```
class ListItem extends React.Component {

    render() {
        return (
          <li>{this.props.item}</li>
        );
    }
}

class List extends React.Component {

    render() {
        let itemsElements = this.props.items.map( (item, index) => {
                              return <ListItem item={item}></ListItem>;
                            });
        return (
          <ul>
            {itemsElements}
          </ul>
        );
    }
}

const listOfItems = [
  "apples",
  "bananas",
  "pineapple"
];

ReactDOM.render(
    <List items={listOfItems} />,
    document.getElementById('root')
);
```


### Exercise
Run this code:

```
class Banana extends React.Component {
    render() {
        return (
          <div>
            <p>Hello world</p>
          </div>
        );
    }
}

ReactDOM.render(
    <Banana />,
    document.getElementById('root')
);
```

Add one prop:
```
<Banana apple="hello"/>
```

Display the prop next to `Hello world`.

Change the prop:
```
let thing = Math.random();

ReactDOM.render(
    <Banana apple={thing}/>,
    document.getElementById('root')
);
```

Change the name of the prop. What else do you need to change in your code?
```
<Banana chicken={thing}/>,
```

Add a second prop:
```
<Banana chicken={thing} kiwi={23423423}/>,
```

How do you access this inside the component?

##### Getting started:

Don't forget to include the 3 libraries you need:
```
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

Create a separate jsx file to put your code in and create a script tag to go with it.
```
<script src="script.jsx" type="text/babel"></script>
```

Chrome will require that you get your file from the network (localhost) - so you will have to run `http-server` in your current directory in order to get the file to be loaded and executed from the script tag.


#### Further
Run the above code: create a component that gets rendered multiple times by passing in props.

#### Further
Have the list item class render 2 components: `ItemId` which will use the map `index` (from the above example) as the id, and `Item` which will render the text of the item. Pass data into these two components as props.

#### Further
```
var fruits = [
  {
    name:"apple",
    weight:23,
    colors : [
      "red","green","yellow"
    ]
  },
  {
    name:"mango",
    weight:13,
    colors : [
      "green","yellow"
    ]
  },
  {
    name:"avocado",
    weight:3,
    colors : [
      "green","brown"
    ]
  }
];
```
Create react code that renders this array of objects.

Use at least 2 separate components.
