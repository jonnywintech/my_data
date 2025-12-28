```dart

class StyledText extends StatelessWidget {
  const StyledText(this.text, {super.key}); // argument
	  final String text; // declared argument

  @override
  Widget build(BuildContext context) {
    return Text(
      text,  /// usage
      style: TextStyle(
        color: Colors.white,
        fontSize: 88,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```