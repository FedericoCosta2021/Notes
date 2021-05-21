# Javascript notes

checkpoint:
76 of javascript complete beginner tutorial
106 of javascript moderno para principiantes

---

js complete beginner course
videos 0-18

//to comment
try not using underscore, use camel style for naming it makes it easier to read

developer.mozilla.org
^a nice place to learn

## Variables

creation:

```javascript
    -let variableName= value;
    to make strings put them in ""

    -const variableName= value;
    creates a constant which cant be changed after setting a value to it

    -var variableName= value;
    this is outdated
```

variables can change type so careful
variables also have properties which can be accessed with a . after calling the variableName
aswell as methods which can be called by variableName.method()
theres a bunch of methods for just variables, gotta check them out
you can also call 2 multiple methods in one line by adding another . like so:

> variableName.method().method1().methodetc();

---

## Primitive types in js

prim types are the most basic forms data is stored

**Number**
numeric value, js only uses one variable type to store numeric info no need to differ between float, int, etc. Theres a max size and min size to this obv

**NaN**
not a number. Is a numeric value that reps something that cant be represented numerically, example:

```javascript
0 / 0 = NaN;
1 + NaN = NaN;
```

**Infinity**
**-Infinity**
js has a way to rep infinity and negative version

**0**
**-0**
js also has this

**String**
text wrapped in quotation marks, can be single or double. But dont mix them up cause it causes confusion you can use quotes inside quotes but they cant be the same type of quotation mark
example:

```javascript
let myString='hello "sirs"'; ===> this works and shows: hello "sirs"
let myString='hello 'sirs'': ===> will not work because there is '' inside another '', one set of '' have to change for this to work
```

Strings can be "added together" this is called a concatenation, example:

```javascript
let msg = "hola";
let who = "fede";
msg + fede;
//output: "holafede"
```

-adding a number instead of another string causes the number value to turn into a string, this doesnt work with any other operation
-Strings are indexed starting at 0, to access a String value at a certain index you can do:
variableName[indexValue]
-Strings cannot be changed, they are immutable

**boolean**
true or false variables

js complete beginner course
video 24
**null**
for something to be null it has to be intentionally assigned the null value.

**undefined**
for something to be undefined it has to be initialized, ie. the keyword reserved for it but without an actual value assigned to it

Simple operations in js:

```javascript
+ addition
* subtraction
- multipliaction
/ division
% remainder also called modulo
** exponent example:2**3= 2^3 = 8

space isnt important, you can do 4+ 7; and it will still work
```

---

js complete beginner course
videos 19-20

## Some string methods used in the video

calling a method without the parenthesis will ask js if it exists, so put the () to actually use them

**.trim()**
Method removes white space before and after the string

```javascript
"              hello     ".trim(); //'hello'
```

**.indexof(String)**
this will go through a string searching for the input inside of the parenth, if it finds an exact match it will return the starting index of the substring if not it returns a -1. THIS IS CASE SENSITIVE.

```javascript
"This is very nice".indexOf("very"); //this will return 8
```

**.slice(number,number)**
this will create a substring from the target string starting from the indicated index value, up to the other value. If 1 value is set, it will slice from the indicated there up to the last index of the target. Your original string will not be affected. example:
'FireTruck'.slice(4); //this will result in 'Truck'

.replace('part of string you want replaced','what you want to replace it with')
if the targeted subString repeats itself in the String, the method will only replace the first match, to replace all matches you need to use a regular expression

---

js complete beginner course
videos 22--corrupted video looked up the topic and took some notes down

## Escape characters

escape characters are used to show characters which would otherwise not be viewable in strings, just like in java. You can insert line breaks or tabs inside of a string

```javascript
\'  '
\"  "
\\  /
\n New Line
\t Horizontal Tabulator
\v Vertical Tabulator

not too sure what these do
\r Carriage Return
\b Backspace
\f Form Feed
```

---

js complete beginner course
video 23

## String templates and literals

a string template is a String normally represented within tildes not '' but `` which are used to pass info down a certain way

```javascript
let person = "me";
let food = "cookie";
`Hello ${person} want a ${food}?`;
```

the String variables can be changed and injected once more into the template to show diff things whats inside the curly brackets can actually be anything, an expression even, using normal quotes for this purpose will not work it has to be tilde's. This is called interpolating data inside of a string. Another example, say we're working on a personal blog and you want to show how long ago a post was made:

```javascript
`posted ${elapsedTime} ago by ${user}`;
```

---

js complete beginner course
video 25

## Math object and random numbers

Math object refers to a set of constants like pi etc and methods which perform mathematical operations:

```javascript
    Math.round(4.9) //5

    Math.abs(-656) //absolute value 656

    Math.pow(2,5) //2^5 = 32

    Math.floor(3.9999999)  //3   removes decimals

    Math.random();    returns a random decimal inbetween 0 and 1 but never 1 the values must be tweaked to suite a certain range example if you want random numbers from 0-10 including 10

    Math.floor(Math.random() * 10 ) + 1;
```

---

js complete beginner course
video 26

## typeof

is actually an operator except its one sided meaning that you have to write it correctly otherwise you'll get an error, will return the type of a variable, or data. Written as:

typeof whateverYouWantToCheck; //no parenthesis required

---

js complete beginner course
video 27

## parseInt() and parseFloat()

takes a string and turns it into a float or int. Passing a String with decimals into parseInt will chop off the decimal portion of it, not round it up. You can pass Strings with non number values to parseWhatever but the numeric portion of it must be in the front of the string. As soon as it detects a non number char it'll stop the function

```javascript
parseInt("36646"); //36646
parseInt("56.7879778"); //56
parseInt("343studios"); //343
parseInt("ret443"); //NaN
```

---

js complete beginner course
video 29-31

## boolean comparisons

just like in other langs the boolean variables can be used to create conditionals with their comparisons.
You can compare Strings with other strings however the comparison **is** case sensitive and must be the same char, so no strange accents/special chars.
In greater than/less than comparisons it takes the unicode value of the string. but its uncommon to use it. And theres probably a better way of getting a boolean from a set of strings

```javascript
> greater than

< less than

>= greater than or equal to

<= less than or equal to

==  !=
    Checks for equality of value, but not equality of type. It coerces both values to the same type and then compares them. This can lead to some unexpected results! /for example:
5 == 5            //true
5 == '5'          //true
0 == ''           //true
0 ==  false       //true
null == undefined //true

=== strict equality
!== non strict equality
    Checks for equality AND type:
5 === 5            //true
5 === '5'          //false
0 === ''           //false
0 ===  false       //false
null === undefined //false

so stick with ===

```

---

js complete beginner course
video 32

## Adding js to a page

so like css, you need to import the script file using

```html
<script src="yourSource.js"></script>
```

however depending on the script if the html elemnt is not initialized the js may not be work properly, to resolve this you may need to call the js inside the \<body> after setting up the element.

To display some js information in the browser console you need to use a method.

```javascript
console.log("what you want displayed in console");
//or
console.error("this will appear as an error msg");
```

---

js complete beginner course
video 33-34

## If and else if

Ifs are just like java:

```javascript
if(condition){
    code to execute
    }
    else {
        code
    }
```

```javascript
if(something===somethingElse){
...
}else if(anotherCondition){

}else if(...){
    ......
}else{
    code that will run if no condition is met
} finally {
    ...
}

```

js complete beginner course
video 42

### Use a switch instead

just like in java, js has switches but heres a neet little thing i learned, if you have multiple cases that spit the same outcome then you can "combine the cases" by putting an empty case above another with code like so:

```javascript
switch (variable) {
  case "poop":
  case "tree bark":
  case " coffee":
    console.log("BROWN");
    break;

  case "lips":
    console.log("red");
    break;

  default:
    break;
}
```

### Different syntax for simple if else statement

if the statement is a yes or no, if else, non of that else if bull, then you can use something called the ternary operator **?** in the following way:

```javascript
condition ? codeIfTrue : codeIfFalse;
```

---

js complete beginner course
video 37

## Some more on conditionals

Conditionals will accept primitives, like so:

```javascript
if(5){//this is true
    ...
}
```

so be careful with what you put in there. Also everything in js spits out a true value when placed alone in a condition except the following:
-false
-0
-""
-undefined
-null
-NaN

i guess this is why the comparisons on the previous section showed as true when comparing any of these values to each other and using == instead of ===

---

js complete beginner course
video 38-41

## Logical operators

&& and
|| or
! not

no singles & |

---

js complete beginner course
video 43

## ARRAYS AND COLLECTIONS

Like java, theres arrays in js. There are some things to note about them
-Arrays are mutable
-Arrays can have other arrays in them.
-Arrays can have more than one type of data in them you dont need to specify what type of array it is
-const arrays can change in value only if referenced properly. Check reference types below for more

syntax:

```javascript
let emptyArray = [];
let myArray = [1, 2, "", true];
```

js complete beginner course
video 55

## ARRAY REFERENCE TYPES

In js when you create a primitive type variable then js actually reserves a space in memory for the value itself, so assigning another variable the value of the original one and then changing the original one wont change the val of the new var created. Arrays don't work like this. When an array is created js creates a code or address which points to the array. So in the example above, if instead of primitive types we had arrays instead, then the value of the new array will also be changed.

So when using **const arrays** what you're actually doing is saying that the reference pointer this array is using, is now immutable. However the actual content within the array can be changed, as long as you aren't changing its reference

comparing 2 arrays with a == or === will always yeild false, because js is actually checking if their references are the same, not the data values within them. This is also true for objects, So to check array equality use a good ol for loop

```javascript
const nums = [1, 2, 3];

//this will not work
nums = [1, 2, 3, 4, 5, 6];

//this will
nums.splice(2, 0, 4, 5, 6);
nums[0] = 10;
```

js complete beginner course
chapter 5

## SOME ARRAY METHODS

**push()**
-add to end

**pop()**
-remove from end

**shift()**
-remove from start

**unshift()**
-add to start

**Concat()**
-merge arrays, this wont change the original arrays. The order of the method call matters.

```javascript
let array1 = [1, 2, 3];
let array2 = [4, 5, 6];
let array3 = ["a", "b", "c"];
console.log(array1.concat(array2));
//expected output [1,2,3,4,5,6]

//combine more than 2 arrs
console.log(array1.concat(array2, array3));
//output: [1,2,3,4,5,6,a,b,c]
```

**includes()**
-looks for a matching value in the entire array and returns boolean

**indexOf()**
-just like str.indexOf. Looks for a matching value in the entire array and returns index value or -1 if not present

**findIndex(function(element,index){ return element.key==='something'})**
-works like index of but is used when objects are in play

**join()**
-creates a string from array. The character between array entries can be modified.

```javascript
let array1 = [1, 2, 3];
let array2 = [4, 5, 6];
let array3 = ["a", "b", "c"];

array1.join();
// '1,2,3'

array2.join("-");
// '4-5-6'
```

**reverse()**
-reverses an array, and actually mutates it

**slice()**
-copy portion of an arr

**splice()**
-remove/replace elements. This will return an array containing the deleted entries, if no entries are deleted then empty array

```javascript
let array1 = [1, 2, 3, 4, 5, 6];

// .splipce(startIndex [number of elements to remove from start, values to replace deleted items or add into array,...])

//will add 10 and 20 infront of index 2
array1.splice(2, 0, 10, 20); //[1,2,3,10,20,4,5,6]

array1 = [1, 2, 3, 4, 5, 6];

array1.splice(3, 3, "a", "b", "c"); // [1,2,3,a,b,c]
```

**sort()**
-sorts an array converting all values to utf char codes and sorts them based on that. This will work fine if the values are strings, it'll sort them alphabetically but not so much if anything else is passed

### finding values of objects within arrays

chapter 11 jsmoderno

```javascript
const games = [
  { title: "terraria", rating: 9.5, myRating: 9 },
  { title: "stardew valley", rating: 9, myRating: 9 },
  { title: "valhiem", rating: 10, myRating: 9 },
  { title: "skyrim", rating: 10, myRating: 8 },
  { title: "minecraft", rating: 10, myRating: 10 },
];

const findValueOfkeyofObject = (myArray, valOfkey) => {
  const index = myArray.findIndex((object, index) => {
    return object.title === valOfkey;
  });
  return index;
};

const filterArrayWithObjects = (myArray, value) => {
  return myArray.filter((object, index) => {
    return object.title.includes(value);
  });
};

console.log(findValueOfkeyofObject(games, "skyrim"));
console.log(games[findValueOfkeyofObject(games, "skyrim")]); 
console.log(filterArrayWithObjects(games, "e"));
```

---

js complete beginner course
javascript moderno para principiantes
chapter 6

## OBJECTS

finally, objects from what I saw on the course are sorta like dart's map. Objects have properties, which have keys and a value associated with them. Instead of accessing object values through an index like you would an array, you do so with the keys mentioned. Check the syntax:

```javascript
const myObject = {
    prop1: value,
    prop2: 1,
    prop3: 'nope',
    prop4: false

    myObject.prop1; //shows value of prop 1
};
```

-Keys are turned into strings so using numbers is not ideal, however you can access data using a diff syntax. The second way shown below turns whatever is between [''] into a string and search for a matching key withing the object. This can be used to search for properties with invalid names, ie with spaces, or when you want to search for a variable's value inside your object.

```javascript
let userInput=1;

const myObject = {
    1: value,
    2: 1,
    3: 'nope',
    4: false
}
    myObject.1; //will not work
    myObject[3]; //will work
    myObject['4'];
    myObject[userInput];
```

-you can call an object property with a . if the name of the key is a string value. Otherwise use [] or ['']
-commas identify the end of a property

theres another way of creating objects, that was the literal way, this is the object way, pretty intuitive stuff:

```js
let Persona=new Object();
Persona.nombre='Fulano';
Persona['isHungry']=true;
```

Also remember if you create an bject from another object and then change the value of either one, this will change the value for both because of how js works

## METHODS

methods are functions inside of classes like below. With methods you can add data to your object, and you should use these methods to actually touch your object.

```javascript
let userInput=1;

const myObject = {
    1: value,
    2: 1,
    3: 'nope',
    4: false,

    //methods
    'get3':function()=>myObject[3];
    'addValues':function(){.....
    }
}
   myObject.1; //will not work
    myObject[3]; //will work
    myObject['4'];
    myObject[userInput];
    myObject.get3();
    myObject.addValues();
```

in a method you can use the this keyword to refer to a particular property in the object just ilke in java, althought it isn't really necessary. Its mostly just good practice

## ADDING/UPDATING PROPERTIES

```javascript
//empty object
const fruitAmount = {};

//adding property
fruitAmount["Apples"] = 6;

//diff way
fruitAmount.Bannana = 10;

//to update
fruitAmount.Apples += 12;

fruitAmount.Apples; //18
```

we can use arrays with objects or objects with arrays:

```javascript
 const gameSession{
     player1 : {
         username:'fede',
         color: 'red'
     },
     player2 :{
         username:'fabi',
         color: 'blue'
     },
     board :{
         ['o',null,'x'],
         ['o','x',null ],
         ['x',null, 'o']
     }
}


gameSession.player1.username; // fede
gameSession.board[0][2];// x
```

## OBJECT REFERENCE TYPE

works the same as array ref

## LOOPS

js complete beginner course
CHAPTER 7

the following work the same, the bottom one is my code, basically the way i did it with java. But in his example he's creating a new array from the row everytime a loop occurs and then adds up the vals of the new array. Seems needlesly complicated imo if you only wanted to find the total for something

```javascript
const gameBoard = [
  [4, 32, 8, 4],
  [64, 8, 32, 2],
  [8, 32, 16, 4],
  [2, 8, 4, 2]
];
console.log(gameBoard[2]);
let totalScore = 0;
for (let i = 0; i < gameBoard.length; i++) {
  let row = gameBoard[i];
  for (let j = 0; j < row.length; j++) {
    totalScore += row[j];
  }
}
console.log(totalScore);

let total = 0;
for (let x = 0; x < gameBoard.length; x++) {
  for (let y = 0; y < gameBoard[x].length; y++) 
  total += gameBoard[x][y];
}
console.log(total);

```

**for of**
 will allow us to call each entry in an array in a cleaner looking bit of code, if you need to use the index vals for something its better to use traditional for loop

```javascript
const gameBoard = [
  [4, 32, 8, 4],
  [64, 8, 32, 2],
  [8, 32, 16, 4],
  [2, 8, 4, 2]
];

//will print entire rows
for(let entry of gameBoard){
console.log(entry);
}

//show each entry individually
for (let entry1 of gameBoard) {
  for (let entry2 of entry1) {
    console.log(entry2);
  }
}

```

Objects are not iterable, you cannot use a for loop or any loop to assign values, etc to an object. You can however use a method called **Object.keys(your object)** or **Object.values(your object)** to access either keys or values. These will return arrays with the desired data. You can use this method in a a for loop to do things.

**for in**
use a for in instead of a for of when accessing object data. A for in will automatically loop through all the keys of an object, So calling the value of a property is much neater using this loop instead of other for's. You can also use for in with arrays but its not reeally a good idea since bugs can happen

```javascript
let movieReview = {
  name: "bees",
  review: 10,
  rating: "kids"
};
for (let key in movieReview) {
  console.log(key, movieReview[key]);
}
```

## FUNCTIONS

chapter 5 javascript modernos para principiantes

A function can be created just like in java or dart, but you need to use the keyword function:

```js
function myFunction(){
console.log('this is my function its the best');
}
```

they can be void or return something and also take in arguments and also be initialized as an expression, to later call it you would do so normally:

```js
var thisIsNowAFunction= function(){
  console.log('hello');

  hello();
}
```

passing undefined variable will not throw an error cause js sucks. So careful with that. You can set default values for the args which will be replaced if the parameter is set:

```js
function myFunction(a=1,b=1,c=1){
  return a+b+c;
}
console.log(myFunction());//3
console.log(myFunction(0,0,0));//0
console.log(myFunction(0));//2
console.log(myFunction(0,0));//1
```

es6 introduced arrow functions:

```javascript
const years = [2000,2005,2008,2012];

//element is parameter
//es5
var age5= years.map(function(element){return 2021-element;});

//es6
let age6 = years.map((element)=>2021-element); 
let age6withIndex = years.map((element,index)=>`entry ${index+1} = 2021-${element}`); 

const squared = (num)=>num*num;
console.log(squared(3));


const people=[
  {name:'fede',
  age:23},
  {name:'fabi',
  age:30},
  {name:'espe',
  age:51},
  {name:'dad',
  age:54}
]

const youngerThan = people.filter((person)=>person.age<50);
console.log(youngerThan);
```

## DOM

chapter 7 javascript moderno para principantes

The DOM is short for the document object model. This refers to the basic html structure of a page

## SCOPE AND BLOCKS

chapter 8 javascript moderno para principantes

in esc5 the scope is diff than in other newer versions:

```javascript
{
let a=5;
let b=1;
var c=0;
}
console.log(a+b);  //throws error
console.log(c);   //works fine

let age=10;
var age5=20;
{
  age5=25;
  age=15;
}

console.log(age);
console.log(age5)
```

## MAPS

chapter 9 javascript moderno para principantes

something im not understanding, need to look up their use since some methods used in the course are deprecated and currently not working. Mostly the get() method.

Maps are structures that hold data very similar to an objkect in js. They have keys and their respective values. Dunno how to call a key tho. You cant just do it like you would with an object.

## SPREAD OPERATOR

chapter 9 javascript moderno para principantes

the spread operator is normally used to call each element in something. Here im using it to combine 2 arrays and then using it to add each element of an array.

```javascript
const sum = (a,b,c)=>a+b+c;
const nums1 =[1,2,3];
const nums2 = [4,5,6];
let numsAll= [nums1,nums2];

console.log(numsAll); //an array with 2 arays

numsAll= [...nums1,...nums2];
console.log(numsAll); //combined array

//another application
console.log(sum(1,2,3));
console.log(sum(...nums1));
```

## CLASSES

chapter 10 javascript moderno para principantes

just like in some other langs:

```Javascript
class Person{
  constructor(name, age){
this.name=name;
this.age=age;
this.isHuman=true; //gonna be true everytime something is constructed
  }

  //methods
  getBiography()=>`name : ${this.name}\n age : ${this.age}\n human : ${this.isHuman}`
}
const person1= new Person('fede',23);

console.log(person1.getBiography());
```

### GETTERS AND SETTERS

[useful link](https://javascript.info/property-accessors)

```javascript
class PersonaProper {
    constructor(name,age,color){
        this.name = name;
        this.age = age;
        this.isHuman = true;
    }
    set name (entry){this._name=entry;}
    set age(entry){this._age=entry;}
    set color(entry){this._color=entry;}
    get name(){return this._name;}
    get age(){return this._age;}
    get color(){return this._color;}
    toString() {
        return `name : ${this._name}\n age : ${this._age}\n human : ${this.isHuman}\n color : ${this._color}`;
      }
}

const persona5 = new PersonaProper();
persona5.name = 'maria';
persona5.age = 83;
persona5.color='pink'
console.log(persona5.name);
console.log(persona5.age);
console.log(persona5.color);
console.log(persona5.toString());
```

the set and get keyword should contain this._whatevr when referring to the actual data you want to set/get. The `_` acts as a container for the data you want to store. This is so you dant have to type getName etc for the diff operations and to offer you more control over whats  happening
