+++
title = "Flutter Introduction"
date = 2022-04-07
draft = false

[taxonomies]
categories = ["Italiano"]
tags = ["programming", "flutter", "cs"]

[extra]
lang = "en"
toc = true
math = false
mermaid = false
+++
## Introductory presentation
<div style="
  position: relative;
  overflow: hidden;
  width: 100%;
  padding-top: 61.25%;"
>
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTbztbS-0eJRn4YTO85yUb1-vze4tRocKWSfTgl9-My0NHpi1OHwPxjC2FITGnRlAR70CI6kUcVHY9a/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height = "100%" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" position="absolute" style="  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
  height: 100%;"></iframe>
</div>

## Running an app
 - Aprire [dartpad.dev](https://dartpad.dev)
 - scrivere il seguente codice *boilerplate* (boilerplate significa che il codice sarà più o meno uguale, qualsiasi applicazione voi stiate creandoh)
```dart
    // ignore_for_file: prefer_const_constructors
    // ignore_for_file: prefer_const_literals_to_create_immutables
    
    // importare il material UI library
    import 'package:flutter/material.dart';

    // la class principale che esegue la nostra funzione MyApp()
    void main() => runApp(MyApp());

    // il widget personalizzato MyApp() che contiene MaterialApp() widget
    // non preocupatevi di questa parte
    class MyApp extends StatefulWidget {
      const MyApp({Key? key}) : super(key: key);
      @override
      _MyAppState createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {

      //Quest'area serve a dichiarare variabili e funzioni
      //il codice che troverete qui non verrà esuguito nel build

      @override
      Widget build(BuildContext context) {

        //Il codice che trovate qui VERRà eseguito nel build .

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
	
 - Aggiungete qualsiasi widget che vorrete dopo le `[]` e dopo `children: `
 - Non dimenticatevi di mettere una `,` dopo ogni widget parameter

## List of widgets to try

### Text
```dart
Text('Hello World'),
```
Un widget molto semplice. [Dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/Text-class.html)

### Sized box
```dart
SizedBox(
  height: 20,
  width: 100,
),
```
utile per creare degli spazi tra i widget. Per esempio:
```dart
Text('One'),
SizedBox(
  height: 20,
),
Text('Two'),
```
creerà uno spazio di 20 pixel tra `One` e `Two`. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/SizedBox-class.html)

### Image
```dart
Image.network('https://flutter.github.io/assets-for-api-docs/assets/widgets/owl-2.jpg'),
```
Mostrerà un'immagina dall'Internet. Assicurati che il 'URL' dell'immagine finisce con un file immagine come `.png`, `.webp`, o `.jpg`. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/Image-class.html)

### Icon
```dart
Icon(Icons.thumb_up),
```
Mostrerà un'icona. Un'intera lista di icone di material usabili può essere trovato [qui](https://fonts.google.com/icons). Pigia su un'icona sul sito e seleziona la sezione `Flutter` sulla destra, ha dei dettagli su come usarlo. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/Icon-class.html)

### Divider
```dart
Divider(),
```
Un widget molt semplice per disegnare una linea sottilr tra due widgets. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/Divider-class.html)

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
Un pulsante semplice, con una funzione `onPressed` che esegue il codice quando il pulsante è premuto. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/ElevatedButton-class.html)

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
un text field è dove l'inputs text dell'utente è letto dalla nostra applicazione. questo input potrebbe poi essere per esempio assagnato a una variabile. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/TextField-class.html)

### Row e Column
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
Row e Column sono usati per creare liste di widgets, rispettivamente orizontalmente e verticalmente. [dettagli aggiuntivi sul Row](https://api.flutter.dev/flutter/widgets/Row-class.html), [More details on Column](https://api.flutter.dev/flutter/widgets/Column-class.html).

## Esempio
Questo è un esempio di cosa potresti fare con questi widgets, questa è un'app semplice che chiede iò nostro nome e ci saluta:
```dart
// ignore_for_file: prefer_const_constructors
// ignore_for_file: prefer_const_literals_to_create_immutables

//importare il material UI library
import 'package:flutter/material.dart';

// class principale che esegue la nostra funziona MyApp()
void main() => runApp(MyApp());

// La funziona MyApp()che ritorna a MaterialApp() widget
// Non preocuparti di questa parte
class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  //Quest'è un'area per dichiarare variabili e funzioni
  //il codice non verrà eseguito quando l'app è build

  String? name; //variable that contains name inserted in TextField

  @override
  Widget build(BuildContext context) {
    //il codice verrà eseguito quando l'app è build

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
            //mostra il nome inserito,
            //aggiungendo $ fa si che ti mostra il valore della variabile
            if(name != null)Text('Hello $name!'), 
          ],
        )
      ),
    );
  }
}
```
