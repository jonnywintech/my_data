To display correct data for each loop item.
```dart
for (final todo in _orderedTodos)
	CheckableTodoItem(
		key: ValueKey (todo.id),
		todo. text,
		todo.priority,
) , // CheckableTodoItem
```
key: ValueKey(todo.id) // unique key that is passed as value ensures that flutter get correct valuest in memory or Widget state.

Alternative is ObjectKey but it must be unique and connected to the data
```dart
for (final todo in _orderedTodos)
	CheckableTodoItem(
		key: ObjectKey (todo),
		todo. text,
		todo.priority,
) , // CheckableTodoItem
```