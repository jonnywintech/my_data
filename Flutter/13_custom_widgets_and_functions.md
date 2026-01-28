Custom widgets and function that are usefull in specific cases

#close_opened_window
```dart
Navigator.pop(context);
```
usefull for closing popups


#Swiping helper
```dart
Dismissible(
        onDismissed: (DismissDirection direction) {
          if (direction == DismissDirection.endToStart ||
              direction == DismissDirection.startToEnd) {
            onRemoveExpense(expenses[index]);
          }
        },
        key: ValueKey(expenses[index]),
        child: ExpenseItem(expenses[index]),
      ),
```
Depending of direction we can preform specific actions. In this case it does not matter

#bottom_popup
```dart
 ScaffoldMessenger.of(
      context,
    ).showSnackBar(
      SnackBar(
        content: Text('Expense deleted.'),
        duration: Duration(seconds: 3),
        action: SnackBarAction(
          label: 'Undo',
          onPressed: () {
            setState(() {
              _registeredExpenses.insert(expenseIndex, expense);
            });
          },
        ),
      ),
    );
  }
```
popup messages that are displayed at bottom with undo functionality currently added to this example

#theme
using default flutter theme settings, and then change only what you need (else you would need to configure each named parameter inside `Theme()`)
```dart
ThemeData().copyWith(
// here you change parameters you need
),
```

#screen size and its value
When used LayoutBuilder we can get size of screen and adjust application accordingly.
```dart
    return LayoutBuilder(
      builder: (ctx, constraints) {
        print(constraints.minHeight);
        print(constraints.maxHeight);
        print(constraints.minWidth);
        print(constraints.maxWidth);
        
        return Widget(child: Text('hello'));
    });
    
    //eg.
    // constraints.minHeight < 399 ? Row(...) : Column(..);
```


