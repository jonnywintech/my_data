# Statefull widget
changing state and showing dynamicly content

```dart
import 'dart:math';
import 'package:flutter/material.dart';

final randomizer = Random();

class DiceRoller extends StatefulWidget {
  const DiceRoller({super.key});

  @override
  State<DiceRoller> createState() => _DiceRollerState();
}

class _DiceRollerState extends State<DiceRoller> {
// _DiceRollerState the _ mean it is private and only accesiable trought this class state

// here we define rest of state - logic 
  int imageNumber = 2;

  void rollDice() {
    setState(() {
      imageNumber = randomizer.nextInt(5) + 1;
    });
  }
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Image.asset(
          'assets/images/dice-$imageNumber.png',
          width: 200,
        ),
        SizedBox(height: 30),
        TextButton(
          onPressed: rollDice,
          style: TextButton.styleFrom(
            backgroundColor: Colors.black54,
            foregroundColor: Colors.white,
            padding: EdgeInsets.symmetric(
              horizontal: 25,
              vertical: 15,
            ),
          ),
          child: Text('ROLL DICE'),
        ),
      ],
    );
  }
}

```