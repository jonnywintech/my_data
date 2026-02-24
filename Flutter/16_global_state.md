# Global state used by Flutter Riverpod
install flutter riverpod package to get global state

Stateless widget are extended 
```dart
class MealDetailsScreen extends StatelessWidget {
to >>>>

class MealDetailsScreen extends ConsumerWidget {

and 
@build 
  Widget build(BuildContext context, WidgetRef ref) {
```

Statefull widgets are also extened but passing ref is not needed in build metod 

```dart
class TabsScreen extends StatefullWidget {
to >>>>

class TabsScreen extends ConsumerStatefulWidget {

```

also in lib folder  make provider folder and in int file name followed by `_provider.dart`

dummy data example
```dart
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:meals_app/data/dummy_data.dart';

final mealsProvider = Provider((ref) {
  return dummyMeals;
});

```

functionaly
```dart
import 'package:flutter_riverpod/legacy.dart';
import 'package:meals_app/models/meal.dart';

class FavoriteMealsNotifier extends StateNotifier<List<Meal>> {
  FavoriteMealsNotifier() : super([]);

  void toggleMealFavoriteStatus(Meal meal) {
    final mealIsFavorite = state.contains(meal);
    if (mealIsFavorite) {
      state = state.where((m) => m.id != meal.id).toList();
    } else {
      state = [...state, meal];
    }
  }
}

final favoriteMealsProvider =
    StateNotifierProvider<FavoriteMealsNotifier, List<Meal>>(
      (ref) => FavoriteMealsNotifier(),
);

```

Usage of this 

```dart
  Widget build(BuildContext context, WidgetRef ref) {
    return Scaffold(
      appBar: AppBar(
        title: Text(meal.title),
        actions: [
          IconButton(
            onPressed: () {
            // HERE
              ref
                  .read(favoriteMealsProvider.notifier)
                  .toggleMealFavoriteStatus(meal);
                  
            /// FUNCTION IS CALLED FROM GLOBAL STATE
            },
            icon: Icon(Icons.star),
          ),
        ],
      ),
```