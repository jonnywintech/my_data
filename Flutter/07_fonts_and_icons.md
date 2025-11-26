In main tree of app create folder fonts
then paste fonts that are going to be used inside of this app

then register fonts in `pubspec.yml`
uncomment following and change accordingly
```yml
 # fonts:
  #   - family: Schyler
  #     fonts:
  #       - asset: fonts/Schyler-Regular.ttf
  #       - asset: fonts/Schyler-Italic.ttf
  #         style: italic
  
  # change to this
    fonts:
    - family: Poppins
      fonts:
        - asset: fonts/Poppins-Bold.ttf
        - weight: 700
        - asset: fonts/Poppins-Medium.ttf
        - weight: 500
        - asset: fonts/Poppins-SemiBold.ttf
        - weight: 600
        - asset: fonts/Poppins-Regular.ttf
        - weight: 400
```

### run 
```bash
flutter pub get
```

In main file main.dart change theme font

```dart
 theme: ThemeData(
        fontFamily: 'Poppins',
        );
```

# Icons 

inside pubspec.yml find `assets` and uncomment and add folder

```yml
  assets:
    - assets/icons/
```

then run flutter pub get