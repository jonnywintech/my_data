Main Element for Route is #Navigator
it technily push screen on screen stack
last one is displayed
```dart
  void selectMeal(BuildContext context, Meal meal) {
    Navigator.of(
      context,
    ).push(MaterialPageRoute(builder: (ctx) => MealDetailsScreen(meal: meal)));
  }

```
