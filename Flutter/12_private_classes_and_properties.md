
Classes and properties that are private and can be only acceses from own class without mutating data are starting with `_` underscore

examples
```dart
class Quiz extends StatefulWidget {
  const Quiz({super.key});

  @override
  State<Quiz> createState() => _QuizState();
}

class _QuizState extends State<Quiz> {
  List<String> selectedAnswers = [];
  var _activeScreen = 'start-screen';
  }
```

in this example  we have state in class that are private and it can only be used inside of Quiz class
also variable is private and can be only used in this state in Quiz class when is instanciad.