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
    //import the material UI library
    import 'package:flutter/material.dart';

    // main class that runs our MyApp() function
    void main() => runApp(MyApp());

    // MyApp() function that returns a MaterialApp() widget
    // don't worry about this part
    class MyApp extends StatefulWidget {
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

### SizedBox
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