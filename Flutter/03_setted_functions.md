add to array 
```dart
arr.add('hello');
```

length of array
```dart
arr.length;
```

print on terminal
```dart
print(arr);
```

```dart
@overide
```
`@overide` is special keyword that let you overide default class function / values thar are defined by inheretance

for example set hashcode of object to be equal to name so it could compare it 

```dart
@overide
bool operator = (covariant Cat other) => other.name == name

@overide
int get hashCode = name.hashCode;
```