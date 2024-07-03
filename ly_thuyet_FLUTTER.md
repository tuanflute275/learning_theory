# ly_thuyet_FLUTTER

> stl -> tạo StatelessWidget

## Widget Container 

    import 'package:flutter/material.dart';
    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false, // tắt logo debug
        home: MyApp(),
      ));
    }

    class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: "Flutter App",
          theme: ThemeData(
            primarySwatch: Colors.blue,
          ),
          home: const MyContainer(), // extract widget to name MyContainer , có thể tách ra file riêng rồi import vào nên thế 
        );
      }
    }

    class MyContainer extends StatelessWidget {
      const MyContainer({
        super.key,
    });

    @override
    Widget build(BuildContext context) {
      return Container(
        // 1 số thuốc tính của container: color, alignment, tranform, decoration, padding, margin....
        // padding: const EdgeInsets.all(5), // all -> 4 phía
        // padding: const EdgeInsets.only(bottom: 5), -> only -> 1 hướng nào đó
        //padding: const EdgeInsets.symmetric(horizontal: 10), -> symmetric;horizontal : hai bên trái phải.
        //padding: const EdgeInsets.symmetric(vertical: 10),  -> symmetric;vertical : trên dưới.
        // color: Colors.green,
        //width: 200,
        //height: 200,
        alignment: Alignment.center,
        transform: Matrix4.rotationY(12),
        decoration: const BoxDecoration(
          shape: BoxShape.circle,
          color: Colors.green,
        ),
        child: const Text(
          'hi',
          textAlign: TextAlign.center,
        ),
      );
    }
  }

# Wrap Widget

    import 'package:flutter/material.dart';

    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false,
        home: MyApp(),
      ));
    }

    class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar( // header
            title: const Text("Flutter App"), // titile
          ),
          body: const Center( // body
            child: Wrap( // ngoài ra còn có Row, Column như bootstrap 
              alignment: WrapAlignment.center, // căn giữa
              direction: Axis.vertical, // xếp dọc
              children: <Widget>[
                MyContainer(),
                MyContainer(),
                MyContainer(),
                MyContainer(),
              ],
            ),
          ),
        );
      }
    }

    class MyContainer extends StatelessWidget {
    const MyContainer({
      super.key,
    });

    @override
    Widget build(BuildContext context) {
      return Container(
        width: 200,
        height: 200,
        // color: Colors.green,
        padding: const EdgeInsets.symmetric(vertical: 10),
        alignment: Alignment.center,
        transform: Matrix4.rotationY(12),
        decoration: const BoxDecoration(
          shape: BoxShape.circle,
          color: Colors.green,
        ),
        child: const Text(
          'hi',
          textAlign: TextAlign.center,
        ),
      );
    }
  }

# Expanded Widget
>Expanded(child: MyContainer()), -> có bao nhiêu chiếm hết

# Text Widget

  `child: const Text(
            'app',
            textAlign: TextAlign.center,
            style: TextStyle(
              color: Color.fromARGB(255, 183, 10, 13),
              fontWeight: FontWeight.bold,
              fontStyle: FontStyle.italic,
              fontSize: 30,
              decoration: TextDecoration.lineThrough,
              wordSpacing: 10,     
        ),
    ),`

# Scaffold Widget

    import 'package:flutter/material.dart';
    import 'package:flutter/widgets.dart';

    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false,
        home: MyApp(),
      ));
    }

    class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        backgroundColor: const Color.fromARGB(255, 179, 190, 177),
        appBar: AppBar(
          title: const Text(
            "Flutter App",
            style: TextStyle(
              color: Colors.white,
            ),
          ),
          centerTitle: true,
          backgroundColor: Colors.amber,
        ),
        drawer: Drawer(
          child: ElevatedButton(
            onPressed: () {
              Navigator.pop(context);
            },
            child: const Text('ok'),
          ),
        ),
        body: const Center(
          child: Wrap(
            alignment: WrapAlignment.center,
            // direction: Axis.vertical,
            children: <Widget>[
              MyContainer(),
              Expanded(child: MyContainer()),
              MyContainer(),
              MyContainer(),
            ],
          ),
        ),
        floatingActionButton: FloatingActionButton(
          backgroundColor: Colors.blueGrey,
          onPressed: () {},
          child: const Icon(Icons.add),
        ),
        floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
        bottomNavigationBar: const BottomAppBar(
          shape: CircularNotchedRectangle(),
          child: SizedBox(
            height: 30,
            child: Text(
              "Footer",
              textAlign: TextAlign.end,
              style: TextStyle(
                fontWeight: FontWeight.bold,
                fontSize: 30,
              ),
            ),
          ),
        ),
      );
    }
    }

    class MyContainer extends StatelessWidget {
    const MyContainer({
      super.key,
    });

    @override
    Widget build(BuildContext context) {
      return Container(
        width: 200,
        height: 200,
        // color: Colors.green,
        padding: const EdgeInsets.symmetric(vertical: 10),
        alignment: Alignment.center,
        transform: Matrix4.rotationY(12),
        decoration: const BoxDecoration(
          shape: BoxShape.circle,
          color: Colors.blue,
        ),
        child: const Text(
          'app',
          textAlign: TextAlign.center,
          style: TextStyle(
            color: Color.fromARGB(255, 183, 10, 13),
            fontWeight: FontWeight.bold,
            fontStyle: FontStyle.italic,
            fontSize: 30,
            decoration: TextDecoration.lineThrough,
            wordSpacing: 10,
          ),
        ),
      );
    }
  }

# Button Widgets (TextButton, ElevatedButton, OutlinedButton)

    import 'package:flutter/material.dart';
    import 'package:flutter/widgets.dart';

    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false,
        home: MyApp(),
      ));
    }

    class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
    Widget build(BuildContext context) {
      var myButtonStyle = ButtonStyle(
          backgroundColor:
              MaterialStateProperty.all<Color>(Colors.blue), // background
          foregroundColor: MaterialStateProperty.all<Color>(
              Colors.yellow), // màu cho nội dung bên trong
          overlayColor:
              MaterialStateProperty.all<Color>(Colors.blue), // hover vào đổi màu
          shadowColor:
              MaterialStateProperty.all<Color>(Colors.red), // shadow color
          padding:
              MaterialStateProperty.all<EdgeInsets>(const EdgeInsets.all(50)));
      return Scaffold(
        appBar: AppBar(
          title: const Text(
            "Flutter App",
            style: TextStyle(
              color: Colors.white,
            ),
          ),
          centerTitle: true,
          backgroundColor: Colors.amber,
        ),
        drawer: Drawer(
          child: ElevatedButton(
            onPressed: () {
              Navigator.pop(context);
            },
            child: const Text('ok'),
          ),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              TextButton(
                onPressed: () {},
                style: TextButton.styleFrom(
                    foregroundColor: Colors.red,
                    textStyle: const TextStyle(fontSize: 20),
                    backgroundColor: Colors.amber),
                child: const Text('Text Button', style: TextStyle(fontSize: 20)),
              ),
              ElevatedButton(
                  onPressed: () {},
                  style: myButtonStyle,
                  child: const Icon(
                    Icons.cloud_upload,
                    size: 80,
                  )),
              OutlinedButton(
                onPressed: () {},
                style: OutlinedButton.styleFrom(
                  foregroundColor: Colors.red,
                  textStyle: const TextStyle(fontSize: 20),
                  backgroundColor: Colors.amber,
                  side: const BorderSide(
                    color: Colors.red,
                    width: 2,
                  ),
                ),
                child:
                    const Text('Outline dButton', style: TextStyle(fontSize: 20)),
              ),
            ],
          ),
        ),
        floatingActionButton: FloatingActionButton(
          backgroundColor: const Color.fromARGB(255, 25, 138, 180),
          child: const Icon(
            Icons.add,
            color: Colors.white,
          ),
          onPressed: () {},
        ),
        floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
        bottomNavigationBar: const BottomAppBar(
          shape: CircularNotchedRectangle(),
          child: SizedBox(
            height: 30,
            child: Text(
              "Footer",
              textAlign: TextAlign.end,
              style: TextStyle(
                fontWeight: FontWeight.bold,
                fontSize: 30,
              ),
            ),
          ),
        ),
      );
    }
  }

# Radio Button Widget (Radio and RadioListTile)

    import 'package:flutter/material.dart';

    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false,
        home: MyApp(),
      ));
    }

    class MyApp extends StatefulWidget {
      const MyApp({super.key});
      @override
      State<MyApp> createState() => _MyApp();
    }

    class _MyApp extends State<MyApp> {
      static int gender = 0;
      @override
      Widget build(BuildContext context) {
        var myButtonStyle = ButtonStyle(
            backgroundColor:
                MaterialStateProperty.all<Color>(Colors.blue), // background
            foregroundColor: MaterialStateProperty.all<Color>(
                Colors.yellow), // màu cho nội dung bên trong
            overlayColor:
                MaterialStateProperty.all<Color>(Colors.blue), // hover vào đổi màu
            shadowColor:
                MaterialStateProperty.all<Color>(Colors.red), // shadow color
            padding:
                MaterialStateProperty.all<EdgeInsets>(const EdgeInsets.all(50)));
        return Scaffold(
          appBar: AppBar(
            title: const Text(
              "Flutter App",
              style: TextStyle(
                color: Colors.white,
              ),
            ),
            centerTitle: true,
            backgroundColor: Colors.amber,
          ),
          drawer: Drawer(
            child: ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: const Text('ok'),
            ),
          ),
          body: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                RadioListTile(
                    title: const Text("Male"),
                    subtitle: const Text("Male subtittle"),
                    secondary: const Icon(Icons.male),
                    value: 1,
                    groupValue: gender,
                    onChanged: (value) {
                      handleChangeGender(value);
                    }),
                RadioListTile(
                    title: const Text("Female"),
                    subtitle: const Text("Female subtittle"),
                    secondary: const Icon(Icons.female),
                    value: 0,
                    groupValue: gender,
                    onChanged: (value) {
                      handleChangeGender(value);
                    }),
              ],
            ),
          ),
          floatingActionButton: FloatingActionButton(
            backgroundColor: const Color.fromARGB(255, 25, 138, 180),
            child: const Icon(
              Icons.add,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
          floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
          bottomNavigationBar: const BottomAppBar(
            shape: CircularNotchedRectangle(),
            child: SizedBox(
              height: 30,
              child: Text(
                "Footer",
                textAlign: TextAlign.end,
                style: TextStyle(
                  fontWeight: FontWeight.bold,
                  fontSize: 30,
                ),
              ),
            ),
          ),
        );
      }

      void handleChangeGender(int? value) {
        return setState(() {
          gender = int.parse(value.toString());
          print(gender);
        });
      }
    }


# GridView Widget

    import 'package:flutter/cupertino.dart';
    import 'package:flutter/material.dart';
    import 'package:flutter/widgets.dart';

    void main(List<String> args) {
      runApp(const MaterialApp(
        debugShowCheckedModeBanner: false,
        home: MyApp(),
      ));
    }

    class MyApp extends StatelessWidget {
      const MyApp({super.key});

      @override
      Widget build(BuildContext context) {
        return const MaterialApp(
          title: "Grid view",
          home: MyHomePage(),
        );
      }
    }

    class MyHomePage extends StatelessWidget {
      const MyHomePage({super.key});

      @override
      Widget build(BuildContext context) {
        return Scaffold(
          backgroundColor: Colors.blue,
          body: GridView(
            gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
                crossAxisCount: 2, // chia bố cục ở đây là 2 phần tử trên trục row
                crossAxisSpacing: 10, // khoảng cách các phần tử theo row
                mainAxisSpacing: 10),// khoảng cách các phần tử theo column
                
            children: [
              Container(color: Colors.red),
              Container(color: Colors.purple),
              Container(color: Colors.yellow)
            ],
          ),
        );
      }
    }

# Display SnackBar in Flutter
