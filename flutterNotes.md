# DART+FLUTTER NOTES

[for a web based IDE](https://dartpad.dartlang.org/0ca5b334ec413c084575f575e0240501)

**to create new virtual androids**
android studio-> tools tab ->avd manager -> select android
the ones with higher api's are more stable versions. In the next step select change graphics to hardware cause I have graphics card.

to use them on vs its pretty simple. When you have a flutter program open, on the bottom of vs you'll see a device option, select it there or if not bring up the vs command palette and select "flutter select device"

checkpoint:
77 FLUTTER IOS ANDROID FERNANDO HERRERA

---

0-7 FLUTTER IOS ANDROID FERNANDO HERRERA

## what is it?

--"Flutter is Google’s UI toolkit for building beautiful, natively compiled applications for mobile, web, and desktop from a single codebase."
Flutter is a framework, or develpment kit which uses a language called dart facilitationg the creation of powerful apps for ios and android.

\*what is dart?
--dart is a c-style programming language also created by google to develop desktop applications and mobile apps.

DART syntax is like java syntax
it needs a main class which tells the machine where to execute the program
you need ; at the end of things
commenting is same as java so // and /_..._/

---

8-12 FLUTTER IOS ANDROID FERNANDO HERRERA

## TYPES OF DATA

DART supports dynamic variables via the keyword var. So specify variable types to avoid unexpected behaviors

-int, unassigned ints will be null, not 0

-String, its a class cause its a chain of chars, can be in double quotes or single, backslashes wont get printed, so they can be used to show certain characters. You can get a char at a certain index via myString[index number] starting at 0 and going to myString.length-1

-char

-boolean written as bool

-double

-List is a collection of objects that have something in common but unless specified, it will accept objects of diff types into it so to specify what type element is in the list you do:
this type of list will grow dynamically

```dart
void main(){
List<int> numbers = [0,1]; //the part in <> defines what type of element should be in the list
numbers.add(3); //this will be ok, will be added to index 2
numbers.add('not a number');  //this should break code
print(numbers);
}

//create a list with a predetermined limit
void main(){
List limited = List(9);
//this list will only have 9 index spaces
}
```

-Map is almost like java's 2d arrays. You have a key and a value of some sort. When you want to call the value at a certain index you instead call it by the key. They key can be any type of data, same goes for the value associated with the key. Remember to set the data type allowed in each entry to avoid unexpected results syntax is:

```dart
Map<key,data> mapName={key1:data1,keyN:dataN};

//create a map, display it, add something to it, display it again, dislpay specific entry
void main(){
//here im defining what element types should be in the places
    Map<int,String> personas={
        1:'gerry',
        2:'larry',
        3:'jerry',
        4:'gary'
    };                                      //entries in the map are seperated by ,
print(personas);                            //display map
personas.addAll({5:'mary'});                //.addAll method adds data to a map
print(personas);
print(personas[1]);                         //will print gerry
print(personas[5]);                         //will print mary
}
```

## VARIABLE INJECTION

these examples would print the same string twice: something is

```dart
void main() {
    var whatElse='is';
    print('something' + whatElse);
    print('something $whatElse');
}
```

the $ between the '' signals the injection of a variable

---

13 FLUTTER IOS ANDROID FERNANDO HERRERA

## FUNCTIONS IN DART

like in java, functions can have different types, this refers to what these functions return
to create a function simply do outside the main

```dart
myFunc(){
}
```

dart will automatically assign the function as a dynamic one, so this function can potentially return any type of data to prevent this from happening you can set the type of object the function should be returning, when you do this, you also need a return statement or if your code is just one line you can use a diff type of syntax

```dart
String myFunc(){
    return 'hello';
}
```

or

```dart
String myFunc() => 'hello'

//to pass on an argument you can do:
void main(){
    example= myFunc(entryForText, entryForName);
    print(example);
}

String myFunc(text,name) => '$text $name'
```

this will work, however you need to make sure your arguments and the example are of the specific type otherwise you can have unexpected results. If instead of entryForText and entryForName you had an int and a bool then it would still accept it. So to fix you could set the type of parameters in myFunc into what you want and also change the type of data example is

```dart
void main(){
    String example= myFunc('entryForText', 'entryForName');    //now the arguments have to be in strings because of the change
    print(example);           //and now since example will be string dart wont have to dynamically set anything
}

String myFunc(String text,String name) => '$text $name'    //set data types to the entries
```

Dart also allows us to assign names to the arguments, so you dont have to worry about the actual order you're stating them, this is acheived by adding {} inside the constructor, while also having to use specific syntax when you want to pass an argument. Not using it will result in an error

```dart
    void main(){
    String example= myFunc('hahaha' , 'hohoho');     //error
    print(example);
}

String myFunc({String text,String name}) => '$text $name'



void main(){
    String example= myFunc(text:'hahaha' , name:'hohoho');     //correct
    print(example);
}

String myFunc({String text,String name}) => '$text $name'
```

14 FLUTTER IOS ANDROID FERNANDO HERRERA

## CLASSES IN DART

very similar to java. Classes are of course molds for something, placed outside the main function. A good programmer will capitalize the first letter of every word in a class's name.
here's an example:

```dart
        void main(){
            var mouse= new Animal();

        }

        class Animal{
            bool warmBlooded;
            bool makeMilk;
        }
```

the above example is ok but the new keyword is not needed, IT IS good programming practice to use it when assigning it to a new variable. var is a dynamic keyword. Now remember constructors right? well it plays the same in dart, right now we are using a default constructor because we arent including any arguments in the class instanciation, remember this means that yes we are infact creating a new Animal called mouse but the values will be null. Setting those values inside the class itself will make it so any new animals will have the same attribute values as our mouse, which is misleading if we want to create say a reptile. to fix this i did:

```dart
void main() {
    var mouse = new Mammal();
    print(mouse);
    print('is warmblooded? ' + mouse.warmBlooded.toString());
    print('makes milk? ' + mouse.makeMilk.toString());
}

class Animal {
    bool warmBlooded;
    bool makeMilk;
}

class Mammal extends Animal {
    Mammal() {
        this.warmBlooded = true;
        this.makeMilk = true;
    }
}
```

works basically like java, extends creates a child class that inherits the attributes of Animal and then i created a default constructer which assigns values to the attributes. To improve this you could over write the Mammal toString to display whats in the print() lines

Looking at the Example from the video, the man is creating a Hero class with a power and name attribute. He then creates a new Hero class using the variable Wolverine. He added a constructer so that it accepts arguments, modified the toString method so that it returns the values of power and name, and showed us how to label the 2 diff arguments so that order doesnt matter when calling the class constructer:

```dart
        void main() {
var wolverine = new Hero(
    name: 'Logan',
    power: 'Undying');                  //notice how order doesnt matter because using labels.
print(wolverine);
}

class Hero {
String power;
String name;

Hero({String power, String name}) {     // {} in function's () mean that the function attribs are labeled
    this.power = power;
    this.name = name;
}
String toString() => '${this.name}-${this.power}';
}
```

15 FLUTTER IOS ANDROID FERNANDO HERRERA

## CLASS DECLARATION SYNTAX

Dart has a short form of declaring classes because of how smart the language actually is. Looking at the example above, you can reduce the amount of code in the constructor. Dart will automatically associate the parameters in the constructor with the class attribs. You can even have attribute labels and dart will know what you're talking about. Fucking nuts!
Since we're in the class we can actually update the toString aswell, removing the {} and this method, cause dart knows you're talking about a variable when using $

```dart
class Hero {
String power;
String name;

//old way
// Hero({String power, String name}) {
//    this.power = power;
//   this.name = name;
//}

//new way, that functions exactly like old one
Hero({this.power, this.name});

String toString() => '$name-$power';
}
```

16 FLUTTER IOS ANDROID FERNANDO HERRERA

## CONSTRUCTERS WITH NAMES (AND SOME JSON)

Say you have a Json file, aka a configuration file that you need to read to create your object but you also want to have the original constructer just incase. Well you can actually create a new constructer with the following syntax:
ClassName.altName(argument)

```dart
import 'dart:convert';                                                  //importing package to convert json data to Map

void main() {

    //final wolverine = new Heroe('Logan', 'Regeneración');                 //old
    final rawJson = '{ "nombre": "Logan", "poder":"Regeneración" }';      //creating of dummy Json, the file must be in this fashion
    Map parsedJson = json.decode( rawJson );                              //decode method spits a Map
    //print( parsedJson );

    final wolverine = new Heroe.fromJson( parsedJson );
    print(wolverine.nombre);
    print(wolverine.poder);

}
class Heroe {
    String nombre;
    String poder;

Heroe( this.nombre, this.poder );          //old constructer

Heroe.fromJson( Map parsedJson ) {              //creating new constructer
    nombre = parsedJson['nombre'];              //using map syntax to assign the values of associated keys to class attribs
    poder  = parsedJson['poder'];
    }
}
```

17 FLUTTER IOS ANDROID FERNANDO HERRERA

## GETTERS & SETTERS (PRIVATE ATTRIBUTES)

Unlike java, there are actual keywords for get and set. Its actually alot prettier. And the syntax for setting an attribute to private is:
\_attribName;

```dart
void main() {
final cuadrado = new Cuadrado();
cuadrado.lado = 10;
print( cuadrado );
print( 'área: ${ cuadrado.area }' );

}
class Cuadrado {
double _lado;               //private attribute


set lado( double valor ) {
if ( valor <= 0 ) {
throw('El lado no puede ser menor o igual a 0');
}
_lado = valor;
}


double get area => _lado * _lado;


toString() => 'Lado: $_lado';

}
```

18-19 FLUTTER IOS ANDROID FERNANDO HERRERA

## ABSTRACT CLASSES AND EXTENDS

```dart
void main() {
//final perro = new Animal();     //wont work, so thats why he did all the other stuff
final perro = new Perro();
perro.emitirSonido();

final gato = new Gato();
gato.emitirSonido();
}

abstract class Animal {
int patas;
void emitirSonido();
}

class Perro implements Animal {     //implements means that the Perro class must have the same attribs as the Animal class
int patas;                      //they need to be added by hand, in this case you would need to add int patas and the emitirsonido method
int colas;
void emitirSonido() => print('GUAUUUUU!!');
}

class Gato implements Animal {          //another example of what he was talking about
int patas;
void emitirSonido() => print('MIAUUUU!!');
}
```

A good use for abstract classes is to create a parent abstract class for child classes, if the parent class wont be used to create any objects of its own then abstract is the way to go as it prevents a future programmer from accidentally using that class. Like java the extends keyword means that the child clases will inherit all attributes the parent class has while adding some more of its own:

```dart
void main() {
    final man= new Personaje(); //wont work

    final superman = new Heroe();
    superman.nombre = 'Clark Kent';

    final luthor = new Villano();
    luthor.nombre = 'Lex Luthor';
}

abstract class Personaje {
    String poder;
    String nombre;
}

class Heroe extends Personaje {
    int valentia;
}

class Villano extends Personaje {
    int maldad;
}
```

20 FLUTTER IOS ANDROID FERNANDO HERRERA

## MIXINS

[in depth mixin tutorial](https://medium.com/flutter-community/dart-what-are-mixins-3a72344011f3)

good read and example, the video is based off that example. To summarize mixins allow child classes to inherit various behaviors which are shared in other classes in a pretty straightforward way. Now child classes can only have one super class. So traditionally speaking creating the diagram from the example would require a bit of a work around. But dart solves all those issues. To pass on these characteristics use with keyword after the extends like below.

taken from the website:
Mixins are very helpful when we want to share a behavior across multiple classes that don’t share the same class hierarchy, or when it doesn’t make sense to implement such a behavior in a superclass.

here the class diagram is followed through beautifully

```dart
abstract class Animal {}        //superclass

abstract class Mamifero extends Animal {}

abstract class Ave extends Animal {}

abstract class Pez extends Animal {}

abstract class Volador {       //creating a simple method to represent various characteristics a flying animal would have, repeats for the other 2 "behaviors"
void volar() => print('Estoy volando!!');
}

abstract class Caminante {
void caminar() => print('Estoy caminando!!');
}

abstract class Nadador {
void nadar() => print('Estoy nadando!!');
}

class Delfin extends Mamifero with Nadador {}           //here he goes

class Murcielago extends Mamifero with Caminante, Volador {}  //if more than one behavior is to be inherited then seperate them with a ,

class Gato extends Mamifero with Caminante {}

class Paloma extends Ave with Caminante, Volador {}

class Pato extends Ave with Caminante, Volador, Nadador {}

class Tiburon extends Pez with Nadador {}

class PezVolador extends Pez with Nadador, Volador {}

void main() {
final pato = new Pato();
pato.volar();      // here he shows that yes those classes now have those behaviors, doing pato. will show volar(),caminante() and nadador()

final pezVolador = new PezVolador();
pezVolador.nadar();
}
```

21-22 FLUTTER IOS ANDROID FERNANDO HERRERA

## ASYNCHRONUS PROCCESSES

futures

A future is type of object that is used to run asynchronous tasks while simultanously running our program. Its runs on a different thread from our original app, heres an example of a http function which returns a future after a delay

```dart
void main() {
print('Estamos a punto de pedir datos');
httpGet('https://api.nasa.com/aliens').then( (data) {
    print( data );
    });
print('Ultima línea');
}



Future<String> httpGet(String url) {
return Future.delayed( new Duration( seconds: 4 ), () {
    return 'Hola Mundo';
});
}
```

To create a future its:

```dart
Future <type of data you're expecting> fName(argument){
....
return type of data you're expecting
}
```

## AWAIT AND ASYNC

These keywords are used when you want a process to wait for another to resume execution without moving around the function in your code. Looking at the code from above, running it as it is would print in the console:
"Estamos a punte de pedir datos"
"Ultima linea"
"Hola mundo"

say we want our program to wait for the future to execute before resuming with the rest of the code. Well to do so, you need to make the function you want halted a async function and also use the await keyword inside of said function like so. If you dont want the program to wait for something add unwait instead of await. Constructors cant have async keyword

```dart
void main() async{                                                //function that is calling other function must hace async keyword
print('Estamos a punto de pedir datos');
await httpGet('https://api.nasa.com/aliens').then( (data) {   //funciton call must have await or unawait
    print( data );
    });
print('Ultima línea');
}



Future<String> httpGet(String url) {
return Future.delayed( new Duration( seconds: 4 ), () {
    return 'Hola Mundo';
});
}
```

---

37-38 FLUTTER IOS ANDROID FERNANDO HERRERA

## FLUTTER FUNDAMENTALS

whats a widget? its a class that can take arguments. Think of them as prebuilt building blocks used to create apps almost like web design. Widgets are abstract classes and come in 2 types, stateless and stateful, this is used to send updates when one of the widget's properties changes. of course the stateless widgets dont allow this update to get sent, they infact wont allow properties to change.Some examples:
-stateful
this class displays names of contacts

```dart
    class contactScreen{
    ...
    String name = '$nameExample'
    }
```

this means that for every instance of this class, the name property can be diff

-stateless
this class has final properties or is not expecting to change values

```dart
    class contactScreen{
    .....
    final name='jerry';
    }
```

stateful widgets are also redrawable, while stateless are, the way to do so is a bit trickier.

whats displayed in a flutter app is inside of widgets inside of other widgets etc.. This forms a tree of widgets with a main one. Get used to this concept
for now i saw :
-scaffold its the background space between elements almost like css's background/padding properties
-the tab bar, its the bar at the bottom of the screen and provides basic controls within the app.
-The app bar, which sits at the top of the screen and is normally used to specify the "title" of the app screen your in, so if i were in the setting part of an app, at the top it would obv say settings

---

39 FLUTTER IOS ANDROID FERNANDO HERRERA

## FLUTTER DIRECTORIES/FILES EXPLAINED

**.idea**
Not found in windows user's projects. This contains info on your editor, you can ignore this

**.gitignore**
this tells git what to ignore when updating saves. You can ignore this

**android**
**ios**
**build**
this holds the application in android, osx, and simulator versions. Ignored in gitignore because the directories are created through your flutter sdk. You can ignore this

**lib**
here is where we create our code

**test**
contains information on our test runs, ignore this

**.metadata**
**.packages**
**.iml**
**.lock**
Auto generated, contiains info about the program you made. DOnt touch

**.yaml**
Contains dependencies your program needs to be run on platforms, you can edit this if needed

**.md**
its the readme that will show up on github for example

---

41-46 FLUTTER IOS ANDROID FERNANDO HERRERA

## GETTING INTO FLUTTER

in this chapter we create the default flutter counter app from scratch, analyzing every line of code.

first bit of code which displays a horrible msg on screen.

```dart
import 'package:flutter/material.dart';
void main(){
runApp(MyApp());
}

class MyApp extends StatelessWidget{
String message='I did it';

@override
build(BuildContext context) {
    return MaterialApp(home:
        Center(child:
            Text(message+' yes')));
    }
}
```

this will run just fine however its best good practice to leave your main.dart alone and only import classes/etc to it. To do this inside the lib folder create:

> lib
>
> > src
> > otherClass.dart
> > main.dart

now, you must import the class into the main.dart file, you can write it out or simply place the cursor on the name of the class inside the main.dart and hit ctrl+. this will bring up a little window, with various options. Its also good practice to seperate OUR imports from system imports. The main should look like this:

```dart
//system imports
import 'package:flutter/material.dart';

//our imports
import 'src/App.dart';

void main(){
runApp(MyApp());
}

```

And src/App.dart looks like:

```dart
//system imports
import 'package:flutter/material.dart';

class MyApp extends StatelessWidget{
String message='I did it';

@override
build(BuildContext context) {
    return MaterialApp(home:
        Center(child:
            Text(message+' yes')));
    }
}
```

flutter allows alot of flexibility regarding its file system so projects can look very diff but function exactly the same.

47-48 FLUTTER IOS ANDROID FERNANDO HERRERA

## WIDGET SCAFFOLD

[Flutter dev entry](https://api.flutter.dev/flutter/material/Scaffold-class.html)

The scaffold is a widget that sets up a pretty app interface for you. The widget has some built in properties that like many of flutters tools, are accessed via their keys inside the build method. To implement it into your app its recommended to create another directory containing the "pages" of your app. so:

> lib
>
> > src
> > otherClass.dart
> > pages
> >
> > > home_page.dart
> > > main.dart

inside our home_page.dart file we follow the same rules seen before however now we must make some adjustments to the build method so it returns a scaffold with the desired arguments also set. Remember the build method will be forever changing.

```dart
import 'packages:flutter/material.dart';

class Hompage extends StatelessWidget{
    @override
    Widget build(){
        return Scaffold(

        );
    }

}
```

## COLUMN AND BODY

Widgets that accept childs can only have one type of child, so if you wanted to have multiple Text(...) childs in the scaffold you need to use the **Body widget** inside the scaffold this will create a container that places anything in it below our appbar. Now inside the body we can choose from a few diff widgets that allow lists. One of these is the **column widget** which organizes its elements vertically

```dart
import 'package:flutter/material.dart';

class HomePage extends StatelessWidget {
  final TextStyle styleExample = new TextStyle(fontSize: 12.0);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('the title'),
        centerTitle: true, //this is needed for android
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: null,
        tooltip: 'this will appear if the user long presses me',
      ),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          Text(
            'this is my first text,  under me should be a counter',
            style: styleExample,
          ),
          Text(
            'dummy counter',
            style: styleExample,
          )
        ],
      ),
    );
  }
}
```

So i managed to make the app sortof work, however since our widget is stateless, I cant create an int without it being final. Tha means its value cant be changed. using a global int outside the class could solve this but it wont update the counter value in the app screen. Sooo to resolve this, we need to port the entire project over to a stateful widget. You can do so by setting cursor on the hompage class and hitting ctrl+. but to actually learn you should write it out.

-remeber to always import the material package when messing with widgets
-Stateful widgets will require an override to their build() method aswell as their create() method.
-create() will require a method which returns a State`<T>` this means that we must also create a new class extending State class which will be used to rebuild our widgets.
-inbetween the <> we must add the target class.
-this class should be private as it will only be used within the file

```dart
import 'package:flutter/material.dart';

class HomePageV2 extends StatefulWidget{

@override
State createState()=>_HomePageV2State();
}



class _HomePageV2State extends State<HomePageV2>{

@override
Widget build(BuildContext context) {
  return ....;}
}
```

-now in the return statement for the build() we just copy+paste the code from home_page.dart, i added a drawer which is a container accessed via the upper left of the screen, and the floating button on the scaffold itself, doesn't do anything tho

```dart
import 'package:flutter/material.dart';

class HomePageV2 extends StatefulWidget {
  @override
  State createState() => _HomePageV2State();
}

class _HomePageV2State extends State<HomePageV2> {
  TextStyle _styleExample = new TextStyle(color: Colors.green);
  int _clickCounter = 0;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('the title'),
        centerTitle: true, //this is needed for android
      ),
      //this is how to add more things in a scaffold, using a child that can hold various childs. Here im using a column whch displays widgets vertically, im centering it and using one of its properties to add a list of widgets to it
      body: Center(
          child: Column(
        mainAxisAlignment: MainAxisAlignment
            .center, //centers contents inside of column with entire screen
        children: <Widget>[
          Text(
            'this is my first text,  under me should be a counter',
            style: _styleExample,
          ),
          Text(
            '$_clickCounter',
            style: _styleExample,
          ),
        ],
      )),
      bottomNavigationBar:
          ButtonBar(alignment: MainAxisAlignment.center, children: [
        FloatingActionButton(
            backgroundColor: Colors.orange,
            onPressed: () {
              _clickCounter++;
              print('$_clickCounter');
              setState(() {});
            },
            child: Icon(Icons.arrow_upward)),
        FloatingActionButton(
            onPressed: () {
              _clickCounter--;
              print('$_clickCounter');
              setState(() {});
            },
            child: Icon(Icons.arrow_downward))
      ]),
      drawer: Drawer(
        child: Column(
          children: <Widget>[Text('test')],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: null,
        mini: true,
        backgroundColor: Colors.pink,
      ),
      floatingActionButtonLocation: FloatingActionButtonLocation.miniEndTop,
    );
  }
}

```

-finally we need to go back to our build() inside the app.dart file to modify what is being returned. From HomePage, to HomePageV2

```dart
//import 'package:showing_scaffold_widget_and_correctfile_structure/src/pages/home_page.dart';
import 'package:showing_scaffold_widget_and_correctfile_structure/src/pages/home_page_v2.dart';

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: Center(child: HomePageV2()));
  }
}
```

53 FLUTTER IOS ANDROID FERNANDO HERRERA

instead of using a button bar, I couldve created a method returning a widget inside the floating action button property in our scaffold. The method, while making the code easier to read would contiain a row and any buttons we'd like to add. ALWAYS inspect what type of class is needed when messing with properties. the floating action button prop in scaffold takes a widget type, which is why we can do this sort of thing. Our method returns a widget, a row containing other buttons.

these are some widgets used in the vid to space the elements out

**SizedBox**
is almost like a div, you can use it to space elements, check its properties to assign it values

**Expanded**
will place the child a max distance away from rest of elements. child property is required
**CHECK VIDEO 55 FOR A COMPLETE OVERVIEW OF EVERYTHING DONE IN THE SECTION**

## 2nd APPLICATION

CHAPTER 6 FLUTTER IOS ANDROID FERNANDO HERRERA

The ListView widget will render a list of widgets in a scrollable container. This widget has some diff builders that do diff things. The norm ListView will do what we stated before. However if you have many elements to be displayed, its better to use the Listview.builder instead as this will dynamically load the elements as you scroll down instead of loading them all at once. Normally this widget is used with the ListTile widget to create entries for the container.

When converting a json to usable data, we must add said file to the app by adding a folder holding all these external files. The folder itself goes outside other folders. Next we edit the yaml file to make the flutter get console command actually include our new files. Make sure you respect the tabs and spacing in the file otherwise you'll get an error.
Now we must create a class to extract this luckily flutter comes with some tools to actually extract data from jsons, its found inside, we use the show keyword to only import the rootBundle classes, not the entire package

```dart
import 'packag:flutter/services.dart' show rootBundle;
```

ok now where do we put this class, well inside:

> lib
>
> > src
> >
> > > providers
> > >
> > > > menu_providers.dart

and in menu_providers.dart we have:

```dart
import 'package:flutter/services.dart' show rootBundle;

class _MenuProviders {
  List<dynamic> opciones = [];

  _MenuProviders() {
    cargarData();
  }

  cargarData() {
    rootBundle.loadString('data/menu_opts.json').then((data) {
      print(data);
    });
  }
}
final menuProviders=new _MenuProviders();
```

rootBundle method will throw a future, here we're saying once you've finished extracting this prints it out in console. However...
The whole idea of doing this is to build our app using a json file, which may or may not be configurable by users later on. And calling the method we just built on first run will result in our config options not being loaded correctly, this is because the future thr method creates takes too long so the rest of our app runs. This is not fixed by using an **asyn/await**

But thankfully flutter has a package that renders widgets using futures called **FutureBuilder** This thing requires a its builder element to be filled. Luckily this thing takes what our rootBundle method spits

### vid 68, get icon from string

flutter doesn't have a built in method of doing this. The json file in the vid is basically a map`<string,string>`. So we need to make a new map somewhere which holds `<String,IconData>` as entries. In this example, String in our map has the same values of the json file, this is so when reading the json file we can pass the string values to be found in our map, and bring forth the icondata. There isnt a way to convert it one to one, as in through a method. Its good practice to create another folder holding any utility functions you may need. Later simply import the package and pass the string as parameter:

```dart
import 'package:flutter/material.dart';

final _iconMap=<String,IconData>{
  'add_alert'     :Icons.add_alert,
  'accessibility' :Icons.accessibility,
  'folder_open'   :Icons.folder_open,
};

Icon iconFromString(String string)=>Icon(_iconMap[string],color: Colors.green,);
```

### vid 69, navigating to diff pages

Use flutter's Navigator object to navigate through your pages. The Navigator method we'll be using takes context and route as parameters. The context must be gotten from the homepage, you pass this to wherever you're calling the navigator to pass it as a parameter. The route is gotten by followig this code:

```dart
final route= MaterialPageRoute(
builder:(context)=>YourOtherPage());
Navigator.push(context,route);
)
```

this will take you to another page in your app and automatically create a back arrow to your previous page. To return from any interactable widget add **Navigator.pop(context)** to its onpressed: atribute.

A better way of doing he same thing is by using the **Navigator.pushNamed** this will allow us to travel from page to page by calling a key associated to each page. So this means using a map. Now to configure this you need to head over to your main.dart or wherever you're returning MaterialApp() and do the following:

```dart
import 'package:flutter/material.dart';
 

import 'package:chapter_6_app/src/pages/alert_page.dart';
import 'package:chapter_6_app/src/pages/homPage.dart';
import 'package:chapter_6_app/src/pages/avatar_page.dart';
//import 'pages/home_temp.dart';

 class Chap6App extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      initialRoute: 'home',
      routes: <String,WidgetBuilder>{
        'home'    : (context)=>HomePage(),
        'alert'   : (context)=>AvatarPage(),
        'avatar'  : (context)=>AlertPage(),
      },
      );
  }
}
```

passing the buildcontext to be applied to each widget

```dart
List<Widget> _listaItemsV2(List<dynamic> data,BuildContext context) {
    final List<Widget> finalWidget = [];

    data.forEach((element) {
    final temp= ListTile(
        leading: iconFromString(element['icon']),
        title: Text(element['texto']),
        trailing: Icon(Icons.arrow_forward_ios_rounded),
        onTap: ()=>Navigator.pushNamed(context, element['ruta']),
      );
      finalWidget.add(temp);
    });
    return finalWidget;
  }
}
```

### vid 71 creating default routes

Code is cleaner if you take the route map and put it in a folder:
>src
>>routes
>>>routes.dart

there should be a function called getAppRoutes or something similar which returns this map:

```dart
import 'package:flutter/material.dart';

import 'package:chapter_6_app/src/pages/homPage.dart';
import 'package:chapter_6_app/src/pages/alert_page.dart';
import 'package:chapter_6_app/src/pages/avatar_page.dart';


getAppRoutes()=>
<String,WidgetBuilder>{
        'home'    : (context)=>HomePage(),
        'alert'   : (context)=>AvatarPage(),
        'avatar'  : (context)=>AlertPage(),
      };
```

now just call it in the routes: of the previous class. Also to generate defualt routes which aren't in our routes.dart map do the following:

```dart
import 'package:flutter/material.dart';

import 'package:chapter_6_app/src/routes/routes.dart';
import 'package:chapter_6_app/src/pages/alert_page.dart';

class Chap6App extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      initialRoute: 'home',
      routes: getAppRoutes(),
      onGenerateRoute: (RouteSettings settings) {//creates default route for routes not registered in our map
        return MaterialPageRoute(
          builder: (context) => AlertPage(),
        );
      },
    );
  }
}
```

this will throw any unregistered route to alertPage()

### vid 72-73 Cards, Images, fade in

To display images use widget, the image property lets us set where we're getting the image use NetworkImage('url') for images from web or AssetImage('route/to/image.png') for local files, assets have their own folder which should be brought in through the .yaml file. to import entire folder do asset/

```dart
Widget getImage(){
  return Image(
    image: AssetImage(image:'route/to/image')
  )
}
```

the fade in is literally just that, a fade in of an image with a placeholder image or gif.

### useful vs shortcuts for flutter

**matapp**
Creates a default matapp class with everything already in and ready to go

**importm**
import 'package:flutter/material.dart';
