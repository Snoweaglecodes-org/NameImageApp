# NameImageApp
import 'package:flutter/material.dart';
import 'package:cached_network_image/cached_network_image.dart';

void main() {
  runApp(MaterialApp(
    title: 'Navigation Basics',
    home: MyApp(),
  ));
}
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final appTitle = 'Form Validation Demo';

    return MaterialApp(
      title: appTitle,
      home: Scaffold(
        appBar: AppBar(
          title: Text(appTitle),
        ),
        body: MyCustomForm(),
      ),
    );
  }
}

// Create a Form widget.
class MyCustomForm extends StatefulWidget {
  @override
  MyCustomFormState createState() {
    return MyCustomFormState();
  }
}

// Create a corresponding State class.
// This class holds data related to the form.
class MyCustomFormState extends State<MyCustomForm> {
  // Create a global key that uniquely identifies the Form widget
  // and allows validation of the form.
  //
  // Note: This is a GlobalKey<FormState>,
  // not a GlobalKey<MyCustomFormState>.
  final _formKey = GlobalKey<FormState>();
  final myController = TextEditingController();
  @override
  void initState() {
    super.initState();

    myController.addListener(_checkLatestValue);
  }
  _checkLatestValue() {
    print("Second text field: ${myController.text}");
  }
  @override
  Widget build(BuildContext context) {
    // Build a Form widget using the _formKey created above.
    return Form(
      key: _formKey,
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: <Widget>[
          TextFormField(
            controller: myController,
            validator: (value) {
              if (value.isEmpty) {
                return 'Please enter some text';
              }
              return null;
            },
          ),
          Padding(
            padding: const EdgeInsets.symmetric(vertical: 16.0),
            child: RaisedButton(
              onPressed: () {
                if (_formKey.currentState.validate()) {
                  if (myController.text == 'Abhijay') {
                    Navigator.push(
                        context,
                        MaterialPageRoute(builder: (context) => Abhijay()));
                  } else if (myController.text == 'Vineeth') {
                    Navigator.push(
                        context,
                        MaterialPageRoute(builder: (context) => VineeBava()));
                  } else if (myController.text == 'Divya') {
                    Navigator.push(
                        context,
                        MaterialPageRoute(builder: (context) => DivyaBava()));
                  } else if (myController.text == 'Sujith') {
                    Navigator.push(
                        context,
                        MaterialPageRoute(builder: (context) => Sujith()));
                  } else {
                    return null;
                  }
                }
              },
              child: Text('Submit')
            )
          )
        ]
      )
    );
  }
}

class Abhijay extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final title = 'Abhijay';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: Text(title),
        ),
        body: Center(
          child: CachedNetworkImage(
            placeholder: (context, url) => CircularProgressIndicator(),
            imageUrl:
            'http://pngimg.com/uploads/trollface/trollface_PNG13.png',
          ),
        ),

        floatingActionButton: FloatingActionButton(
        // When the user presses the button, show an alert dialog containing
        // the text that the user has entered into the text field.
        onPressed: () {
          Navigator.pop(context);
        },
        tooltip: 'Return',
        child: Icon(Icons.arrow_back_ios),
        ),
      ),
    );
  }
}
class Sujith extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final title = 'Sujith';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: Text(title),
        ),
        body: Center(
          child: CachedNetworkImage(
            placeholder: (context, url) => CircularProgressIndicator(),
            imageUrl:
            'https://www.askideas.com/media/76/Funny-Meme-Faces-2.jpg',
          ),
        ),
        floatingActionButton: FloatingActionButton(
          // When the user presses the button, show an alert dialog containing
          // the text that the user has entered into the text field.
          onPressed: () {
            Navigator.pop(context);
          },
          tooltip: 'Return',
          child: Icon(Icons.arrow_back_ios),
        ),
      ),
    );
  }
}
class VineeBava extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final title = 'Vinee Bava';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: Text(title),
        ),
        body: Center(
          child: CachedNetworkImage(
            placeholder: (context, url) => CircularProgressIndicator(),
            imageUrl:
            'https://cdn.techgyd.com/50-Funniest-Meme-Faces-Ideas-For-Facebook-37-833x1024.jpg',
          ),
        ),
        floatingActionButton: FloatingActionButton(
          // When the user presses the button, show an alert dialog containing
          // the text that the user has entered into the text field.
          onPressed: () {
            Navigator.pop(context);
          },
          tooltip: 'Return',
          child: Icon(Icons.arrow_back_ios),
        ),
      ),
    );
  }
}
class DivyaBava extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final title = 'Divya Bava';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: Text(title),
        ),
        body: Center(
          child: CachedNetworkImage(
            placeholder: (context, url) => CircularProgressIndicator(),
            imageUrl:
            'https://www.askideas.com/media/76/Spiderman-Funny-Meme-Faces.jpg',
          ),
        ),
        floatingActionButton: FloatingActionButton(
          // When the user presses the button, show an alert dialog containing
          // the text that the user has entered into the text field.
          onPressed: () {
            Navigator.pop(context);
          },
          tooltip: 'Return',
          child: Icon(Icons.arrow_back_ios),
        ),
      ),
    );
  }
}
