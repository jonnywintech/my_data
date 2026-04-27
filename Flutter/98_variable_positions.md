Variable positions in code 
```dart
import 'package:flutter/material.dart';

class AuthScreen extends StatefulWidget {
  const AuthScreen({super.key});
#1 //// imutable variables etc passed from parrent
  @override
  State<AuthScreen> createState() => _AuthScreenState();
}
#2 //// top level scope for shared constants variables etc, helper functions, enums

class _AuthScreenState extends State<AuthScreen> {
  var _isLogin = true;
#3 //// mutable state variables, controllers, focus nodes, etc
  @override

#4 //// initState dispose _submit _toggleAuthMode  
  Widget build(BuildContext context) {
#5 //// build method with UI code
    return Scaffold(
      backgroundColor: Theme.of(context).colorScheme.primary,
      body: Center(
```

## Positions in `auth.dart`

Here is what each position means and what you can put there.

---

### 📍 Position #1 (auth.dart:5)

**Scope:** inside `AuthScreen` class (the `StatefulWidget` class)

**Best use:** immutable widget configuration coming from parent

**Typical variables:**
```dart
final String title;
final Color accentColor;
static const values used by this widget type;
```

**Avoid:** mutable UI state here. `StatefulWidget` itself should stay mostly immutable.

---

### 📍 Position #2 (auth.dart:9)

**Scope:** top-level file scope, between classes

**You can place:**
- top-level `const` / `final` variables (shared constants)
- top-level helper functions
- other classes, enums, typedefs, extensions, mixins

**Typical variables:**
```dart
const double formSpacing = 12;
final RegExp emailRegex = ...;
```

**Avoid:** mutable global state unless you really need app-wide shared state.

---

### 📍 Position #3 (auth.dart:12)

**Scope:** inside `_AuthScreenState` class

**Best use:** mutable state and controllers for this screen

**Typical variables:**
```dart
bool _isLogin = true;
final _formKey = GlobalKey<FormState>();
final _emailController = TextEditingController();
String _enteredEmail = '';
late AnimationController _controller;
```

👉 This is where screen state belongs.

---

### 📍 Position #4 (auth.dart:15)

**Scope:** method area inside `_AuthScreenState`, right before `build`

**Best use:** lifecycle and helper methods

**Typical methods:**
- `initState`
- `dispose`
- `_submit`
- `_toggleAuthMode`

**Note:**  
Variables here should usually be **local variables inside methods**, not standalone declarations floating between annotations and methods.
