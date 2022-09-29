# Class 05

# Putting it all together:

## React Docs - Thinking in React  [source  ](https://reactjs.org/docs/thinking-in-react.html) 
<br>

### 1- What is the single responsibility principle and how does it apply to components?
a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.
Separate your UI into components, where each component matches one piece of your data model.
![image](https://reactjs.org/static/9381f09e609723a8bb6e4ba1a7713b46/90cbd/thinking-in-react-components.png)


### 2-What does it mean to build a ‘static’ version of your application?
takes your data model and renders the UI but has no interactivity. 
will use props are a way of passing data from parent to child and don’t use state at all to build it.State is reserved only for interactivity.



### 3-Once you have a static application, what do you need to add?
 The components will only have render() methods
 will take your data model as a prop

 
### 4-What are the three questions you can ask to determine if something is state?
- Is it passed in from a parent via props? If so, it probably isn’t state.
- Does it remain unchanged over time? If so, it probably isn’t state.
- Can you compute it based on any other state or props in your component? If so, it isn’t state.

### 5-How can you identify where state needs to live?
 * dentify every component that renders something based on that state.
* Find a common owner component .
* Either the common owner or another component higher up in the hierarchy should own the state.
* If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
<br>
<br>
<br>

## Higher-Order Functions : [source  ](https://eloquentjavascript.net/05_higher_order.html#h_xxCc98lOBK)


### 1- What is a “higher-order function”?



### 2- Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?



### 3-Explain how either map or reduce operates, with regards to higher-order functions.

<br>
<br>

## Things I want to know more about