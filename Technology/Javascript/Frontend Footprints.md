# Frontend Footprints
#javascript#

## Redux
### Provider
Provider makes the Redux store available to the rest of your app.
```js
const rootElement = document.getElementById('root')
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  rootElement
)
```

### connect()
 
To connect your component to the store.


## Antd
### Grid

Ant design divides 12 grids into 24 on average. In the grid framework, we can define the outer framework base on rows and columns.

* Creating a group of columns horizontally in a row;
* Content should be put in Columns which should be the elements of Rows;
* In the Grid framework, we use `span` to define the width of a column, the value of span is between 1 and 24;
* If the total value of the columns in a row exceeds 24, then the column will render in the next line;

**Spacing among columns**

We can use `gutter` to space the columns, and  (16+8n)px is recommended for the value of the gutter;

**Alignment of the columns**

We can use the `justify` attribute to define the alignment of the columns, such as `'start'`, `‘center’`, `‘end’`,`‘space-between’` and  `‘space-around’`.

What’s more, some columns in the same row have different height, we can define the vertical alignment of them with `align` attribute.

Eg:
```javascript

import { Row, Col } from 'antd';

const DemoBox = props => <p className={`height-${props.value}`}>{props.children}</p>;

ReactDOM.render(
  <div>
    <p>Align Top</p>
    <Row type="flex" justify="center" align="top">
      <Col span={4}>
        <DemoBox value={100}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={50}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={120}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={80}>col-4</DemoBox>
      </Col>
    </Row>

    <p>Align Center</p>
    <Row type="flex" justify="space-around" align="middle">
      <Col span={4}>
        <DemoBox value={100}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={50}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={120}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={80}>col-4</DemoBox>
      </Col>
    </Row>

    <p>Align Bottom</p>
    <Row type="flex" justify="space-between" align="bottom">
      <Col span={4}>
        <DemoBox value={100}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={50}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={120}>col-4</DemoBox>
      </Col>
      <Col span={4}>
        <DemoBox value={80}>col-4</DemoBox>
      </Col>
    </Row>
  </div>,
  mountNode,
);
```


**Responsive Design**

Show different style on different devices to achieve the best users’ experience.

We can use `xs sm md lg xl xxl` to define different grid alignment for devices with different size of displays.

Eg:
```javascript
import { Row, Col } from 'antd';

ReactDOM.render(
  <Row>
    <Col xs={{ span: 5, offset: 1 }} lg={{ span: 6, offset: 2 }}>
      Col
    </Col>
    <Col xs={{ span: 11, offset: 1 }} lg={{ span: 6, offset: 2 }}>
      Col
    </Col>
    <Col xs={{ span: 5, offset: 1 }} lg={{ span: 6, offset: 2 }}>
      Col
    </Col>
  </Row>,
  mountNode,
);
```


## React

### JSX

```javascript
const element = <h1>Hello, world!</h1>;
```

This is a React element — JSX, which is neither a string or HTML.

**JSX is an Expression Too**

After compilation, the JSX expressions become regular JS functions and evaluates to JS objects.

**JSX Prevents Injection Attacks**

Everything is converted to a string before being rendered.

**JSX Represents Objects**

JSX will be compiled down to `React.createElement()` calls.

```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```javascript
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);

```

These two examples are identical.

React element are plain objects and React DOM take care of the DOM to match the React elements.

Applications built with React usually have a single root inside it.

### Updating the Rendered Element

> An element is like a single frame in a movie: it represents the UI at a certain point in time.  

**React Only Updates What’s Necessary**


### Components and Props

> Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.  

`props` in Component can be passed into rendered components by define properties in the tags.

Eg:
```javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);

```

> Extracting components might seem like grunt work at first, but having a palette of reusable components pays off in larger apps.  

**Props are read-only.**
> Extracting components might seem like grunt work at first, but having a palette of reusable components pays off in larger apps.  

`componentDidMount()` and `componentWillUnmount` are lifecycle methods.

### How to Use State Correctly

**Do Not Modify State Directly**
Use `setState()` instead.

**State Updates May Be Asynchronous**

a second form of `setState()` that accepts a function rather than an object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument:

```javascript
this.setState(function(state, props) {
  return {
    counter: state.counter + props.increment
  };
});
```

**State Updates are Merged**

> When you `callsetState()`,  React merges the object you provide into the current state.  

> This is why the state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.  

This is why we need redux or react hooks.

