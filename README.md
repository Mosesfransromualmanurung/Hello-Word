import 'package:flutter/material.dart';

void main() {
  runApp(new MaterialApp(
    debugShowCheckedModeBanner: false,
    home: new MyApp(),
  ));
}
class MyApp extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Program Luas Jajar Genjang'),
        ),
        body: Penjumlahan(),
      ),
    );
  }
}

class Penjumlahan extends StatefulWidget {
  _PenjumlahanState createState() => _PenjumlahanState();
}

class _PenjumlahanState extends State<Penjumlahan> {
  final txtalas = TextEditingController();
  final txttinggi = TextEditingController();

  String result = '';

  getTextInputData() {
    setState(() {
      var alas = int.parse(txtalas.text);
      var tinggi = int.parse(txttinggi.text);
      var luas = alas * tinggi;
      result = luas.toString();
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          Container(
              width: 280,
              padding: EdgeInsets.all(10.0),
              child: TextField(
                controller: txtalas,
                autocorrect: true,
                decoration: InputDecoration(hintText: 'Alas'),
              )),
          Container(
              width: 280,
              padding: EdgeInsets.all(10.0),
              child: TextField(
                controller: txttinggi,
                autocorrect: true,
                decoration: InputDecoration(hintText: 'Tinggi'),
              )),
          RaisedButton(
            onPressed: getTextInputData,
            color: Color(0xffFF1744),
            textColor: Colors.white,
            padding: EdgeInsets.fromLTRB(10, 10, 10, 10),
            child: Text('Prosess'),
          ),
          Padding(
              padding: EdgeInsets.all(8.0),
              child: Text("Luas Jajar Genjang = $result",
                  style: TextStyle(fontSize: 20)))
        ],
      ),
    ));
  }
}
