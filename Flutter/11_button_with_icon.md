# Button with icon

```dart
OutlinedButton.icon(
      onPressed: () {},
      style: OutlinedButton.styleFrom(
        backgroundColor: Colors.amber,
        foregroundColor: Colors.white,
        padding: EdgeInsets.fromLTRB(30, 20, 30, 20),
      ),

      label: Text('Start Quiz'),
      icon: Icon(
        Icons.arrow_right_alt_outlined,
        size: 25,
      ),
    );
```