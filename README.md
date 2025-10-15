dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^2.0.0
  firebase_auth: ^4.0.0
  cloud_firestore: ^5.0.0
  google_sign_in: ^6.0.0
  provider: ^6.0.0

import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'screens/home_screen.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(RabhApp());
}

class RabhApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'ربح',
      theme: ThemeData(primarySwatch: Colors.amber),
      home: HomeScreen(),
    );
  }
}



import 'package:flutter/material.dart';

class HomeScreen extends StatefulWidget {
  @override
  _HomeScreenState createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  int points = 0;

  void _watchAd() {
    setState(() {
      points += 10; // كل مشاهدة إعلان = 10 نقاط
    });
  }

  void _inviteFriend() {
    setState(() {
      points += 20; // دعوة صديق = 20 نقطة
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('تطبيق ربح')),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          children: [
            Text('نقاطك الحالية: $points', style: TextStyle(fontSize: 24)),
            SizedBox(height: 30),
            ElevatedButton(
              onPressed: _watchAd,
              child: Text('👀 مشاهدة إعلان'),
            ),
            ElevatedButton(
              onPressed: _inviteFriend,
              child: Text('📨 دعوة صديق'),
            ),
          ],
        ),
      ),
    );
  }
}
  
