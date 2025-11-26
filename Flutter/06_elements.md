Main element is Scaffold which contans whole screen -> app bar
```dart 
 Widget build(BuildContext context) {
    return Scaffold(appBar: AppBar(
	     elevation: 0.0, // this removes elevation (SHADOW)
    ));
  }
```

#App Bar
```dart
class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: appBar(), // this is top bar
      body: Column(   /// this is body and it have column with children
        children: [
          TextField(
            decoration: InputDecoration(
            filled: true, 
            fillColor: Colors.white),
          ),
        ],
      ),
    );
  }
```

#Text widget for displaying text  and its properties that are ususaly used :)
```dart
Text(
  'Hello World',
  style: TextStyle(
	color: Colors.white,
	fontSize: 18,
	fontWeight: FontWeight.bold,
  ),
```

#Container used for wrapping and styling containers inside
```dart
Container(
	margin: EdgeInsets.only(top: 40, left: 20, right: 20),
)
```

`Height i Width`
In case that you cannot use height and width 
use margin to resize element
also it might need `aligment: Aligment.center`

Full Example of the container
```dart
Container(
  alignment: Alignment.center,
  margin: EdgeInsets.all(10),
  decoration: BoxDecoration(
	color: Color(0xffF7F8F8),
	borderRadius: BorderRadius.circular(10),
  ),
  child: SvgPicture.asset('assets/icons/arrow_left.svg'),
),
```

#Gesture Detector on Tap

```dart
  GestureDetector(
	onTap: () {},
	child: Container(...)
	).
```
#### #AppBar full example [[99_full_elements_examples]]

#Row to show border items it must be wrapped into IntrisivHeights
```dart
IntrinsicHeight(
  child: Row( /// element
	mainAxisAlignment: MainAxisAlignment.end,
	children: [
	  VerticalDivider(
		color: Colors.black,
		thickness: 0.1,
		indent: 10,
		endIndent: 10,
	  ),
	  Padding(
		padding: const EdgeInsets.all(12),
		child: SvgPicture.asset('assets/icons/filter.svg'),
	  ),
	],
  ),
),
```

#SizedBox used to add space between containers
```dart
SizedBox(
	height:100,
)
```