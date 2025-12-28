gradient canot be directly applied to scaffold but it can to container or other objects that have decoration > BoxDecoration object

```dart
Container(
  decoration: BoxDecoration(
	gradient: LinearGradient(
	  begin: Alignment.topLeft,
	  end: Alignment.bottomCenter,
	  colors: [
		Colors.green.shade100,
		Colors.green.shade700,
	  ],
	),
  ),

  child: const Center(
	child: Text('Deponija'),
  ),
),
```

