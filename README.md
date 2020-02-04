
## Agenda

### syntax review
```js
let int_example = 10

let m1, m2, m3 = "you can assign multiple variables the same value at the same time"

let array_example = [ 'a', 'b', 'c' ]

function func_example( s ){
  //either a function does something outright, or returns a value
  //aim for simplicity and single purpose functions
  //this function for example will just take the 's' variable and make it 
  //all uppercase, then return that string
  return toUpperCase( s )
}

//if statement example
if ( !false ){
  console.log( 'this if statement was true' )
} else {
  console.log( 'this won\'t happen because we literally made the if statement true' )
}

//loop examples
while ( int_example > 1 ){
  console.log( 'this will be spammy if we don\'t do something' )
  int_example --
}

for ( var i=0; i < 10; i++ ){
  console.log( 'this will loop 10 times as "i" increments' )
}

let j = 0
do {
  console.log( 'doing this until j == 10 lol' )
  j++
} while ( j < 10 )

//google w/e you think of

```

### objects
```js
let obj_example = {
  this_is_a_key: 1,
  this_is_also_a_key: 2,
  obj_keys_can_be_anything: "string lol",
  they_can_even_be_functions: object_function_input_string => console.log( `You entered this string ${ object_function_input_string }` ), //that is an arrow function, more on that later
  one_more_key_for_fun: true
}

```
+ object oriented programming
```js
function Person( data ) {
  // "this" refers to that particular instance of the object, so when you pass the name 
  // parameter here, you can change it for each person object you create, if you'd like
  
  this.name = data.name
  this.greeting = function( ) {
    alert( 'Hi! I\'m ' + this.name + '.' )
  };
}

//here we passed a different name to two instances of a person object
//and so bob and sarah are born
let bob = new Person( { name: 'Bob' } )
let sarah = new Person( { name: 'Sarah' } )

//notice how I passed an object into the Person as data instead of just a string name
//this makes it a lot cleaner if I ever want to add more variables later

```
### classes
```js
//these are just boujee ass objects
//notice how classes are always capitalized, not necessary, just considered good form
class Animal {  
  constructor( data ) {  
    //instead of just defining the object properties right in the object, a class uses a
    //constructor to build the initial object with the given data
    this.name = data.name  
  }  
  eat( ) {  
    console.log( 'eat' )
  }  
}

class Bird extends Animal {  
  constructor( data ) {
    //when extending, call the super( ) function to instantiate the parent class
    super( data.name )
    this.numWings = data.numWings
    //the Bird class doesn't need to have its own eat( ) function, because it extends
    //the Animal class. This is called inheritance.
  }  
}

const bird = new Bird( { name: 'Joe', numWings: 2 } )
console.log( bird.name )
bird.eat( )
```
### polymorphism
+ this is the idea that instead of having one really complex object, you have a large library of other ones that extend eachother and inherit things. Again with the single purpose functions. An example of this would be a car class, which is extended by car brands, etc...           **this is ALWAYS an interview question, no matter how long you have been doing this.**

### overriding
+ overriding is the idea that if you are inheriting functions from multiple parent classes, you may want to change one of them for some reason. So you can override it by just redefining it

### namespace and using unique variable names
+ namespaces are the names of the classes, objects, variables, functions, everything. It is the idea that you want your stuff to be unique so that you don't have another library with the same things, and then it gets ugly.

### using built in classes
+ you might recognize some of the default js classes - String, Object, Function, Array - all just js objects with properties

### using other libraries, react, vue, jquery, Angular, etc
+ all of the libraries you hear about like React or VueJS or JQuery, are all just a file somebody compiled a whole bunch of functions and such into an object, which then took on a life of its own.

### scoping
+ this is the planning. It is what you do with a project manager, where you lay out the whole application or project before you start, so you can divide and conquer and each person on your team works on a library or class or section. The end goal of scoping a project is to have a timeline, even if you don't ever stick to it. While all of this might be pretty basic stuff, scoping is where most developers fall short. They lose sight of the big picture and just sink into coding one thing.

### repositories
+ git, svn, jenkins - all things used to manage releases of code or projects, but also allow you to roll back changes you make in case something happens. That might be oversimplifying it, but yolo

### workflows - agile, waterfall, what a sprint is etc
+ different teams work in different ways. I have yet to go to a coding interview where they don't ask about these different methodologies for working on a team

### network layout, server, client, network protocols etc
+ HTTP, TCP, UDP, HTTPS, SSH, TLS, FTP, blah blah blah

### encodings 
+ base64 - urlencoding - htmlentities - if you want to put some funky characters in a function but it breaks, what do you do? - - - you escape it or encode it

### json - the syntax of object oriented programming
+ json, while you will hear endlessly about this, is just a javascript object at the end of the day. Hence **J**ava**S**cript **O**bject **N**otation
+ it is important to remember that with json, you will always use the double quotes instead of the single quotes, and you put quotes around everything.
+ you will notice the quotes around the keys where as I was not doing that before. Numbers can still not be quoted. This example is some ugly stuff I just googled lol
```json
{
    "widget": {
        "debug": "on",
        "window": {
            "title": "Sample Konfabulator Widget",
            "name": "main_window",
            "width": 500,
            "height": 500
        },
        "image": {
            "src": "Images/Sun.png",
            "name": "sun1",
            "hOffset": 250,
            "vOffset": 250,
            "alignment": "center"
        },
        "text": {
            "data": "Click Here",
            "size": 36,
            "style": "bold",
            "name": "text1",
            "hOffset": 250,
            "vOffset": 100,
            "alignment": "center",
            "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"
        }
    }
}
```

### ajax, fetch, and using the network
+ PUT, HEAD, POST, GET, OPTIONS, TRACE, DEBUG, probably more, cant remember
+ ajax stands for **A**synchronous **J**avaScript **A**nd **X**ML.
+ js has a built in function to handle this called **fetch( )**
+ jQuery is also a lot of peoples go-to for ajax
```js
fetch( 'http://example.com/movies.json?param1=a&param2=b' )
  .then( ( response ) => {
    return response.json( )
  } )
  .then( ( myJson ) => {
    console.log( myJson )
  } )

//notice here the difference between a POST and GET request. A GET request the
//parameters are passed through the URL, where as in a POST request the parameters get
//passed as an object in the body of the request. We could have included an object with
//similar attributes in the GET request above, but there was no need.

const data = { username: 'example' }

fetch( 'https://example.com/profile', {
  method: 'POST', // or 'PUT'
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(data),
})
.then((response) => response.json())
.then((data) => {
  console.log('Success:', data);
})
.catch((error) => {
  console.error('Error:', error);
})

//because the data gets transfered in the body of the request rather than in the URL, 
//POST requests are much better for handling sensitive information.

```

### SQL and using a database
+ SQL is just a language used to fetch data from a database in a quick and efficient way.
```sql
//given a table in a database that looks like this
  +---------+-----------+------------+
  | id      | username  | password   |
  +---------+-----------+------------+
  | 1001    | admin     | 1234       |
  | 2039    | tyler     | yolo420    |
  | 2098    | paint     | bucket     |
  +---------+-----------+------------+
  3 rows in set (0.05 sec)
//if you had thousands of users, and you wanted to grab the row with your name,
//it would look like this:
  SELECT username, password FROM credentials_table WHERE username='Tyler';

//SQL is a very simple and straightforward language. If you can read, you can do SQL.
//What separates the professionals from everybody else is the efficiency. A huge complex
//database with hundreds of columns is way slower than pulling the data you need with a
//large query that combs through multiple small tables. Also SQL efficiency can be exponentially
//improved by setting the fields to the correct data type, such as INT, or CHAR, or blob
//but I am usually lazy and don't work on large databases, so I just use VARCHAR or TEXT
```

### once through the complicated stuff, time to touch on other languages
+ server side languages
+ client side languages
+ java - platform independent - language of android - jar files are their libraries
+ javascript - for web interface or nodejs back end or electron apps - can create modules for a more OOP approach
+ python - for scripting but fast, easy, and platform independent. can also be used for web development - django
+ C++ - for talking to the machine - DLLs are their libraries
+ C# - see java, but for windows only typically
+ Go - can do anything I think
+ Assembly - the language of the machines
+ ruby - sort of a mix of python and other stuff - can be for web dev on rails
+ bash - linux terminal scripting
+ powershell - windows terminal scripting
+ batch - windows cmd.exe scripting

### actual advanced stuff
+ threading
+ digging into low level coding
+ working with binaries
+ debugging
+ kernels
+ other poo I dont know about lol

# Useful Links
+ some handy javascript shorthand for things [shorthand javascript](https://www.sitepoint.com/shorthand-javascript-techniques/)
+ a neat utility for encoding or decoding or w/e you could possibly need [cyber chef](https://gchq.github.io/CyberChef/)
