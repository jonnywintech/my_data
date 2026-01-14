Getter  are specific keyword that are placed before function name.
In return you get variable name as simple variable without need to call it. 
Guess is it call itself in background so later on you can use data.

Here is example
```dart
class RestultsScreen extends StatelessWidget {
  const RestultsScreen({
    super.key,
    required this.resetScreen,
    required this.selectedAnswers,
    required this.activeScreen,
  });
  // get keyword
  void Function() get summaryData{
   for (var i = 0; i < selectedAnswers.length; i++) {
      summary.add({
        'question_index': i,
        'question': questions[i].text,
        'correct_answer': questions[i].answers[0],
        'user_answer': selectedAnswers[i],
      });
    }
    return summary;
  }
  
  // later on it can be used like this>>
  summaryData[0].question
  // insted of 
  final dataSum = summaryData();
  dataSum[0].question
}
```