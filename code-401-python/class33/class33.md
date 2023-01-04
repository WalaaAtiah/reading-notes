# Read 33: Next- Forms and Conditional Rendering 

## Custom Hooks:[source](https://reactjs.org/docs/hooks-custom.html)
**Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.**
* **A custom Hook is a JavaScript function whose name starts with ”use” and that may call other Hooks. For example, useFriendStatus below is our first custom Hook:**

### Using a Custom Hook:
**In the beginning, our stated goal was to remove the duplicated logic**

<br>

## Lifting State Up:[source](https://reactjs.org/docs/lifting-state-up.html#:~:text=In%20React%2C%20sharing%20state%20is,it%20into%20the%20Calculator%20instead.)

* **n React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called “lifting state up”. We will remove the local state from the TemperatureInput and move it into the Calculator instead.**

* **Lifting state involves writing more “boilerplate” code than two-way binding approaches, but as a benefit, it takes less work to find and isolate bugs. Since any state “lives” in some component and that component alone can change it, the surface area for bugs is greatly reduced. Additionally, you can implement any custom logic to reject or transform user input.**

* **If something can be derived from either props or state, it probably shouldn’t be in the state. For example, instead of storing both celsiusValue and fahrenheitValue, we store just the last edited temperature and its scale. The value of the other input can always be calculated from them in the render() method. This lets us clear or apply rounding to the other field without losing any precision in the user input.**

<br>

## Thinking in React:[sorce](https://reactjs.org/docs/thinking-in-react.html)

1. **Step 1: Break The UI Into A Component Hierarchy**
   
<img src="https://reactjs.org/static/9381f09e609723a8bb6e4ba1a7713b46/90cbd/thinking-in-react-components.png" alt="drawing" style="width:400px;"/>


**You’ll see here that we have five components in our app. We’ve italicized the data each component represents. The numbers in the image correspond to the numbers below.**

* **FilterableProductTable (orange)**: contains the entirety of the example
* **SearchBar (blue)**: receives all user input
* **ProductTable (green)**: displays and filters the data collection based on user input
* **ProductCategoryRow (turquoise)**: displays a heading for each category
* **ProductRow (red)**: displays a row for each product


2. **Step 2: Build A Static Version in React**

Now that you have your component hierarchy, it’s time to implement your app. The easiest way is to build a version that takes your data model and renders the UI but has no interactivity. It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing. We’ll see why.

To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. props are a way of passing data from parent to child. If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.

3. **Step 3: Identify The Minimal (but complete) Representation Of UI State**
4. **Step 4: Identify Where Your State Should Live**
5. **Step 5: Add Inverse Data Flow**



<br>

## MEMOIZATION IN REACT JS : [source](topcoder.com/thrive/articles/memoization-in-react-js)




### WHAT IS MEMOIZATION?
There are some times when re-rendering of the component results in performance issues. To overcome this, React provides us with a performance feature known as memoization.

Memoization is an optimization technique that allows an increase in the performance of a program by storing the results of some expensive function so that we don’t need to call that function when the same inputs are given.

### HOW TO IMPLEMENT MEMOIZATION IN REACT
React has the features PureComponent and memo hook which allow us to implement memoization in React.
PureComponent allows us to perform optimization. It depends on the shouldComponentUpdate() lifecycle method but it can only be used with the class component.
React also gives us a memo() hook to apply memoization for functional components.
If we need a function component that gives the same result for the same props and we don’t want to re-render it, we can use memoization to skip the re-render of the component by storing and reusing the last rendered result.

### MEMOIZATION USING PURECOMPONENT
PureComponent is similar to Components in React except that PureComponent implements shouldComponentUpdate() with shallow prop and state comparison and Components does not.
In some cases, if our component re-renders the same result with the same given props and state which results in performance issues, then we can use PureComponent to increase performance. PureComponent’s shouldComponentUpdate() only shallowly compares the object.
But we should make sure that props and state are simple. If they contain any complex data structures then PureComponent may produce wrong results. Also, we should make sure that all the children components of PureComponent are also PureComponent since PureComponent’s shouldComponentUpdate() skips prop updates for the full component subtree.
