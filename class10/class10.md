# Class 10

## In memory storage

## Understanding the JavaScript Call Stack{:target="_blank"} [source  ](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4) 

<br>



### 1-What is a 'call'?
At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).


### 2- How many 'calls' can happen at once?

First Out (LIFO) principle to temporarily store and manage function invocation (call).

LIFO: When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

### 3- What does LIFO mean?
First Out (LIFO) principle to temporarily store and manage function invocation (call).

LIFO: When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.
### 4- Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.
example of a call stack:![call stack](https://th.bing.com/th/id/R.82b9c53584798f208694d6ba1c05d34b?rik=ZgFcLdvjJV3bLw&riu=http%3a%2f%2fwww.itcsolutions.eu%2fwp-content%2fuploads%2f2011%2f02%2fCallStack.gif&ehk=Efma0z%2fjF2E5yrDhWc%2fENhcqoO2G77xgWgeVF6M268g%3d&risl=&pid=ImgRaw&r=0)


Temporarily store when the function is called:![Temporarily store](https://cdn-media-1.freecodecamp.org/images/QgR2uIk7tW0YNz0Xm8g0jAPeRFI0e4sCejsv)
### 5- What causes a Stack Overflow?
A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.



## Understanding the JavaScript Call Stack{:target="_blank"} [source  ](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4) 

<br>


### 1- What is a 'reference error'?
when you try to use a variable that is not yet declared you get this type os errors.common happen when using const and let ,they are not  hoisted like var and function
### 2-What is a 'syntax error'?
when you have something that cannot be parsed in terms of syntax,

### 3-What is a 'range error'?
give the array  an invalid length like given it negative length
### 4- What is a 'tyep error'?
This is probably the most frequent error in JS.when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.

### 5- What is a breakpoint?
 be achieved by putting a debugger statement in your code in the line you want to break.You can also add conditional breakpoints by right-clicking a previous set breakpoint, which will make your program stop at that point only if a condition is met.
### 6- What does the word 'debugger' do in your code?
the process of analyzing how your program runs, how it generates data in order to find defects and issues in your code.
<br>
<br>


### To solve error :
- most common way its to simply console.log() the variables you want to check or, by using chrome developer tools, open your page with your JS code (press cmd+o in macOS or Ctrl+o in Windows) and choose your file to debug, click the line you wanna debug and refresh your page again (F5).If the line you selected was run you will be able to see what has happened before that point and you can try and evaluate the next lines to check if everything is outputting what you are expecting.
- breakpoint 

## Things I want to know more about
be familiar with solve error