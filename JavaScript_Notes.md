## Document Structure
Root is defines as `<html>`. You then can have elements within. You open and close tags for the language parcer example `<h1>`. Is a tag for headers.

~~~js
<html>
    <head>
        <h1>This is some text</h1>
    </head>
    <body>
        <p>This is a paragraph</p>
        <p>This is a second paragraph</p>
    </body>
</html>
~~~

We end with this: after adding break tag and styles to center the text - known as inline style. 
~~~js
<html>
    <head>
        <h1 style="text-align:center;">This is some text</h1>
    </head>
    <body>
        <p style="text-align:center;">This is a paragraph</br>
        This is a second paragraph add some more text</p>
    </body>
</html>
~~~

## JavaScript Syntax
Rules for correctly structures program.

* Case Sensitivity - consol.Log() is not same as console.log()
* Semicolin line ending - code goes here;
* Comments are - //single line comment
* Types - int, str, char, boolean

First we add ID to paragraphs with `id=p1`. Add a button with ` <button type='button' 
        onclick="document.getElementById('p1').innerHTML='Hello World!';">` creates button that sets HTML element of p1 to become hellow world on button click. 

~~~js
<hmtl>
    <head>
        <h1>This is some text</h1>
    </head>
    <body>
        <p id='p1'>This is a paragraph</p>
        <p id='p2'>This is a second paragraph</p>
        <button type='button' 
        onclick="document.getElementById('p1').innerHTML='Hello World!';">
        hello</button>
        <button type='button' 
        onclick="document.getElementById('p2').innerHTML='This is JavaScript.';">
        JavaScript</button>
    </body>
</hmtl>
~~~

## Working with Image Tags
 Works when cat.jpg is in the same file as the idex.html file.

~~~js
<html>
    <head>
        <h3>This is the heading</h3>
    </head>
    <body>
        <div id='text'>
            This is some text.
        </div>
        <button type="button"
        onclick="document.getElementById('photo').src = 'cat.jpg'">
        show me a cat
        </button>
        <img id="photo" src="cat.jpg" style="width:300px;height:300px;">
        <button type="button"
        onclick="document.getElementById('photo').src = 'dog.jpg'">
        show me a dog
        </button>
    </body>
</html>
~~~

# More Advanced Client-Side Scripting

## Variables and Arrays
`<script>` denotes code that does not need to go on the screen.

Use the `var` keyword:

~~~js
<html>
    <head>
       
    </head>
    <body>
        <p id = 'p1'></p>
        <script>
            var b = 4;
            var a = 3;
            var sum = b + a;
            document.getElementById('p1').innerHTML = sum;
        </script>
    </body>
</html>
~~~

Arrays - declared also with `var` but use the square brackets []. Starts at index 0. Refer with [] as well.
~~~js
<html>
    <head>
       
    </head>
    <body>
        <p id = 'p1'></p>
        <script>
            var items = ["first","second","third"]
            document.getElementById('p1').innerHTML = items[2];
        </script>
    </body>
</html>
~~~

## Conditionals and Looping
If statement - declare with `if(boolean) {}`
~~~js
<html>
    <head>
       
    </head>
    <body>
        <p id = 'p1'>value not set </p>
        <script>
            var value = 4;
            if(value < 5)
            {
                document.getElementById('p1').innerHTML = value;
            }
                
            
        </script>

    </body>
</html>
~~~
for looping - declare with `for(counter = 1; counter < 10; counter + 1>){}

While looping - uses
~~~js
<html>
    <head>
       
    </head>
    <body>
        <p id = "p1">value no set</p>
        <script>
            var array = ["one","two","three","four"];
            var output = "";
            for(i = 0; i < array.length; i++){
                output += "This is item " + array[i] + "</br>" ;
            }
            document.getElementById('p1').innerHTML = output;
        </script>

    </body>
</html>
~~~

## Basics of Functions
Starts with key word, then name, then arguments (optional inputs), and then the fuction using to `return` for a output.
~~~js
function addnumbers (n1, n2) {
    return n1 + n2;
}
~~~
## Basics of Frameworks
Create a new file in the same folder as the `index.html` file. Then you can write `src = libfile.js`. A framwork exposes an API to code. You can use libraries too with the `src` code. Some frameworks like AngularJS, React, etc. You usually pick one framework and stick with it.

## Server Side Javascript with NodeJS

Node JS lets you create a server. Allows to you to do a web request process in JS. http request, create server, then listen on a port. Serves as the framework on the server.

## REST and API

### REpresentational State Transfer
* Client Server Based - each side does just one job
* Stateless - no state is stored, every request has all info
* Cachable - responses not changed can be used again to load faster
* Layerable - can go through proxy or load balancer
* Extendable - server to add functinality to client
* Uniform Interface - anticipate how a response is formated

### API

Defines how  a system will responds and what queries are valid to interact with that system.

