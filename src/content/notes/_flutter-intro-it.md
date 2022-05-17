+++
title = "Introduzione a Flutter"
date = 2022-05-18
draft = false

[taxonomies]
categories = ["Italiano"]
tags = ["programming", "flutter", "cs"]

[extra]
lang = "it"
toc = true
math = false
mermaid = false
+++
## Presentazione introduttiva
<div style="
  position: relative;
  overflow: hidden;
  width: 100%;
  padding-top: 61.25%;"
>
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRoblU32tJhqyaJFMk5Llw2usV8mr-Qju3ekU1VTB15J0yrGm5ERAtj4qPDxNLWtdMy1adP2lNmIzh2/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height = "100%" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" position="absolute" style="  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
  height: 100%;"></iframe>
</div>

## Eseguendo un app
 - Aprire [dartpad.dev](https://dartpad.dev)
 - Scrivere il seguente codice *boilerplate* (boilerplate significa che il codice sarà più o meno uguale, qualsiasi applicazione voi stiate creandoh)
```dart
    // ignore_for_file: prefer_const_constructors
    // ignore_for_file: prefer_const_literals_to_create_immutables
    
    // importare il material UI library
    import 'package:flutter/material.dart';

    // la class principale che esegue la nostra funzione MyApp()
    void main() => runApp(MyApp());

    // il widget personalizzato MyApp() che contiene MaterialApp()
    // non preocupatevi di questa parte
    class MyApp extends StatefulWidget {
      const MyApp({Key? key}) : super(key: key);
      @override
      State<MyApp> createState() => _MyAppState();
    }

    class _MyAppState extends State<MyApp> {

      //Quest'area serve a dichiarare variabili e funzioni
      //il codice che troverete qui non verrà esuguito nel build

      @override
      Widget build(BuildContext context) {

        //Il codice che trovate qui VERRÀ eseguito nel build .

        return MaterialApp(
          home: Scaffold( //lo scaffold è come una cornice per la pagina
            appBar: AppBar(
              //potete cambiare il titolo se volete
              title: Text('My First App'),
            ),
            body: Column (
              children: [
                // dentro a questa colonna si possono
                // aggiungere qualsiasi widget
              ],
            )
          ),
        );
      }
    }
```
	
 - Aggiungete qualsiasi widget che vorrete dopo le `[]` e dopo `children: `
 - Non dimenticatevi di mettere una `,` dopo ogni widget e dopo ogni parametro del widget

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
Utile per creare degli spazi tra i widget. Per esempio:
```dart
Text('One'),
SizedBox(
  height: 20,
),
Text('Two'),
```
Creerà uno spazio di 20 pixel tra `One` e `Two`. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/SizedBox-class.html)

### Image
```dart
Image.network('https://flutter.github.io/assets-for-api-docs/assets/widgets/owl-2.jpg'),
```
Mostrerà un'immagina dall'Internet. Assicuratevi che il 'URL' dell'immagine finisce con un file immagine come `.png`, `.webp`, o `.jpg`. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/Image-class.html)

> Nota: dentro a dartpad si possono prendere immagini solo da siti con CORS (cos'è per questo corso è irrelevante), ma essenzialmente significa che non si possono usare immagini a caso dall'internet (mentre in un app normale su android o ios per esempio funziona). Siti come [unsplash](https://unsplash.org) e [imgur](https://imgur.com) funzionano.

### Icon
```dart
Icon(Icons.thumb_up),
```
Mostrerà un'icona. Un'intera lista di icone di material usabili può essere trovato [qui](https://fonts.google.com/icons). Sotto la sezione android ha il nome che può essere incollata dentro all'app. [dettagli aggiuntivi](https://api.flutter.dev/flutter/widgets/Icon-class.html)

### Divider
```dart
Divider(),
```
Un widget molto semplice per disegnare una linea sottile tra due widget. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/Divider-class.html)

### Button
```dart
ElevatedButton(
  child: Text('Click me!'), //potrebbe anche essere un'icona per esempio
  onPressed: () {
    //Codice da eseguire quando viene premuto il tasto qui
    print('Button has been clicked');
  },
),
```
Un pulsante semplice, con una funzione `onPressed` che viene eseguita quando il pulsante è premuto. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/ElevatedButton-class.html)

### Text field
```dart
TextField(
  onChanged: (value) {
    print ('This value has been inserted: $value');
    //assegniamo una variabile stringa all'input
    //ma dobbiamo usare setState per aggiornare in
    //tempo reale l'app
    setState ((){
      input = value;
    });
  },
),
```
Un text field è dove un input dell'utente è letto dalla nostra applicazione. Questo input potrebbe poi essere per esempio assagnato ad una variabile. [dettagli aggiuntivi](https://api.flutter.dev/flutter/material/TextField-class.html)

### Row e Column
```dart
//widget disposti orizzontalmente
Row(
  children: [
    //widget qui
  ],
),

//widget disposti verticalmente
Column(
  children: [
    //widget qui
  ],
),
```
Row e Column sono usati per creare liste di widgets, rispettivamente orizontalmente e verticalmente. [dettagli aggiuntivi sul Row](https://api.flutter.dev/flutter/widgets/Row-class.html), [dettagli aggiuntivi su Column](https://api.flutter.dev/flutter/widgets/Column-class.html).

## Esempio
Questo è un esempio di cosa potete fare con questi widget, questa è un'app semplice che chiede un nome e lo saluta:
```dart
// ignore_for_file: prefer_const_constructors
// ignore_for_file: prefer_const_literals_to_create_immutables

//importare il material UI library
import 'package:flutter/material.dart';

// la class principale che esegue la nostra funzione MyApp()
void main() => runApp(MyApp());

// il widget personalizzato MyApp() che contiene MaterialApp() widget
// non preocupatevi di questa parte
class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  //Questa è un'area per dichiarare variabili e funzioni
  //il codice non verrà eseguito al build

  String? name; //variabile che contiene l'input del TextField

  @override
  Widget build(BuildContext context) {
    //il codice verrà eseguito al build

    return MaterialApp(
      home: Scaffold(
        //scaffold è come una cornice per l'app
        appBar: AppBar(
          title: Text('App per saluti'),
        ),
        body: Column(
          children: [
            Text('Benvenuti!'),
            SizedBox(height: 10),
            Text('Nome:'),
            TextField(
              onChanged: (value) {
                //setState è usato per aggiornare l'app dinamicamente
                setState(() {
                  name = value; //assegna il valore dell'input a nome
                });
              },
            ),
            SizedBox(height: 20),
            //mostra il nome inserito,
            //aggiungendo $ fa si che ti mostra il valore
            //della variabile
            if(name != null)Text('Ciao $name!'), 
          ],
        )
      ),
    );
  }
}
```

## Meteo
Ecco l'app per il meteo che creeremo assieme oggi: [App](https://gist.github.com/ScratchX98/7f1ce873f59017a42d1ae5b2491bac67)
