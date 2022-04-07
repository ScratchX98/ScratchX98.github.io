+++
title = "Flutter Introduction"
date = 2022-04-07
draft = false

[taxonomies]
categories = ["English"]
tags = ["programming", "flutter", "cs"]

[extra]
lang = "en"
toc = true
math = false
mermaid = false
+++
## Introductory presentation
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTbztbS-0eJRn4YTO85yUb1-vze4tRocKWSfTgl9-My0NHpi1OHwPxjC2FITGnRlAR70CI6kUcVHY9a/embed?start=false&loop=false&delayms=3000" frameborder="0" width="640" height="398" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

## Running an app
 - Open [dartpad.dev](https://dartpad.dev)
 - Paste the following *boilerplate* code (boilerplate means that the code will be more or less the same whatever application you're making)
```dart
    // ignore_for_file: prefer_const_constructors
    // ignore_for_file: prefer_const_literals_to_create_immutables
    
    // import the material UI library
    import 'package:flutter/material.dart';

    // main class that runs our MyApp() function
    void main() => runApp(MyApp());

    // MyApp() function that returns a MaterialApp() widget
    // don't worry about this part
    class MyApp extends StatefulWidget {
      const MyApp({Key? key}) : super(key: key);
      @override
      _MyAppState createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {

      //this is the area to declare variables and functions in
      //the code here will not be executed when the app is built

      @override
      Widget build(BuildContext context) {

        //the code here WILL be executed when the app is built

        return MaterialApp(
          home: Scaffold( //scaffold is like a frame for our app
            appBar: AppBar(
              //you can change the title if you would like
              title: Text('My First App'),
            ),
            body: Column (
              children: [
                // inside this column of widgets
                // we can add whatever widgets we like
              ],
            )
          ),
        );
      }
    }
```
	
 - Add whatever widgets you like into the `[]` after `children: `
 - Don't forget to put a `,` after every widget and parameter

## List of widgets to try

### Text
```dart
Text('Hello World'),
```
A very simple widget. [More details](https://api.flutter.dev/flutter/widgets/Text-class.html)

### Sized box
```dart
SizedBox(
  height: 20,
  width: 100,
),
```
Useful for creating spaces between other widgets. For example:
```dart
Text('One'),
SizedBox(
  height: 20,
),
Text('Two'),
```
Will create a 20 pixel space between `One` and `Two`. [More details](https://api.flutter.dev/flutter/widgets/SizedBox-class.html)

### Image
```dart
Image.network('https://flutter.github.io/assets-for-api-docs/assets/widgets/owl-2.jpg'),
```
Displays an image from the internet. Make sure that the `URL` of the image ends with an image file like `.png`, `.webp`, or `.jpg`. [More details](https://api.flutter.dev/flutter/widgets/Image-class.html)

### Icon
```dart
Icon(Icons.thumb_up),
```
Displays an icon. A full list of useable material icons can be found [here](https://fonts.google.com/icons). Click on an icon on the website and select the `Flutter` section on the right, it has details on how to use it. [More details](https://api.flutter.dev/flutter/widgets/Icon-class.html)

### Divider
```dart
Divider(),
```
A very simple widget to draw a thin line between two other widgets. [More details](https://api.flutter.dev/flutter/material/Divider-class.html)

### Button
```dart
ElevatedButton(
  child: Text('Click me!'), //this could also be an Icon for example
  onPressed: () {
    //code to be executed when the button is clicked goes here
    print('Button has been clicked');
  },
),
```
A simple button, with an `onPressed` function that executes code when the button is pressed. [More details](https://api.flutter.dev/flutter/material/ElevatedButton-class.html)

### Text field
```dart
TextField(
  onChanged: (value) {
    print ('This value has been inserted: $value');
    //an interesting thing to do would be to assign
    //value to a String input for example
    //however if we want to do that and update our
    //dynamically we would have to use a setState
    setState ((){
      //input = value;
    });
  },
),
```
A text field is where a user inputs text to be read by our application. This input could then be for example assigned to a variable. [More details](https://api.flutter.dev/flutter/material/TextField-class.html)

### Row and Column
```dart
//widgets arranged horizontally
Row(
  children: [
    //widgets go here
  ],
),

//widgets arranged vertically
Column(
  children: [
    //widgets go here
  ],
),
```
Row and Column are used to make lists of widgets, horizontally and vertically respectively. [More details on Row](https://api.flutter.dev/flutter/widgets/Row-class.html), [More details on Column](https://api.flutter.dev/flutter/widgets/Column-class.html).

## Example
Here is an example of what you could make with these widgets, this is a simple app that asks for our name and then greets us:
```dart
// ignore_for_file: prefer_const_constructors
// ignore_for_file: prefer_const_literals_to_create_immutables

//import the material UI library
import 'package:flutter/material.dart';

// main class that runs our MyApp() function
void main() => runApp(MyApp());

// MyApp() function that returns a MaterialApp() widget
// don't worry about this part
class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  //this is the area to declare variables and functions in
  //the code here will not be executed when the app is built

  String? name; //variable that contains name inserted in TextField

  @override
  Widget build(BuildContext context) {
    //the code here WILL be executed when the app is built

    return MaterialApp(
      home: Scaffold(
        //scaffold is like a frame for our app
        appBar: AppBar(
          title: Text('Greeting app'),
        ),
        body: Column(
          children: [
            Text('Hello!'),
            SizedBox(height: 10),
            Text('Insert your name:'),
            TextField(
              onChanged: (value) {
                //setState is used for updating our app dynamically
                setState(() {
                  name = value; //asign value to name
                });
              },
            ),
            SizedBox(height: 20),
            //show the inserted name,
            //adding the $ makes it show variable value
            if(name != null)Text('Hello $name!'), 
          ],
        )
      ),
    );
  }
}
```
