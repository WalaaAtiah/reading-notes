# Class 03

## React Docs - lists and keys : 
 [learn more ](https://reactjs.org/docs/lists-and-keys.html) 

### 1- What does .map() return? 
new array
### 2- If I want to loop through an array and display each value in JSX, how do I do that in React?
using  map () and return the value inside curly braces {}

### 3. Each list item needs a unique  key_.

### 4. What is the purpose of a key?

help react to select which element need  to change ,



## The Spread Operator [learn more ](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab) 

### 1. What is the spread operator?
refer to the use of an ellipsis of three dots (…) to expand an alterable object into the list of arguments,quick syntax for adding items into arrays ,to merge two array 
### 2. List 4 things that the spread operator can do?

Copying an array
separate  array in to arguments
Using Math functions
Adding an item to a list
Combining objects
### 3. Give an example of using the spread operator to combine two arrays.
let names = ['walaa','mazen','mohammad']
let addname = ['bayan','afnan','yahia' ];
const allnames = [...names,...addname]
console.log(...allnames);
### 4. Give an example of using the spread operator to add a new item to an array.
let num = [5,8,9]
let  add = [4, ...num]
console.log(add) 

### 5. Give an example of using the spread operator to combine two objects into one.
let cats= {  Name: 'losy',  legs: 4};
let dogs = {  name : 'dogy',  legs: 4 ,kids:5};
let animal = {  ...cats,  ...dogs};
 

### Videos :How to Pass Functions Between Components [learn more ](https://www.youtube.com/watch?v=c05OL7XbwXU) 


### 1- In the video, what is the first step that the developer does to pass functions between components?
Create the function where the stat going to change


### 2- In your own words, what does the increment function do?
update one of the count depend which name is pass in 


### 3. How can you pass a method from a parent component into a child component?
 pass by props 
### 4. How does the child component invoke a method that was passed to it from a parent component?
By calling the method


## Things I want to know more about
more practise in this  
