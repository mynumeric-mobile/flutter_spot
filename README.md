Flutter_MySpot is a plug alowing you to easily implement tutorial in your app

<div align="center">
  <video  controls autoplay src="https://github.com/mynumeric-mobile/flutter_spot/assets/60822263/677de86d-3368-4e3e-af2d-d4ce50375abc" width="400" />
</div>

## Features

Manage scenario with scene to explain élément on your flutter widget adding key to desired widget

<li>Allow reponsive screen,</li>
<li>Audio support (using <a href="https://pub.dev/packages/audioplayers">audioplayer</a>),</li>
<li>Handle play once (using <a href="https://pub.dev/packages/flutter_secure_storage">flutter_secure_storage)</a>,</li>

## Getting started

To install plug-in add to your public.yaml :
```dart
dependencies:
  flutter:
    sdk: flutter

  flutter_myspot:
    git: https://github.com/mynumeric-mobile/flutter_myspot
```

## Usage

examples for package could be found in example folder

- first wrap your page with HoleWidget

this widget hold scenario. Scenario is composed by properties and an array of scenes. Each scene is used sequencialy to highlight a designet widget.

note that your widget must have a key :

```dart
HoleWidget(
          scenario: SpotScenario(
            titleWidget: SpotScenario.textWidgetBuilder(text: "Wellcome to our tutorial", context: context),
            // and a scene for each widget to highlight
            scenes: [
              SpotScene(
                description: SpotScenario.textWidgetBuilder(
                    text: "You can change this number",
                    context: context,
                    style: const TextStyle(color: Colors.white, fontSize: 20)),
                audioAsset: "number.mp3",
              ),
            ],
            
          ),
          child: MyHomePage(title: 'Flutter Demo Home Page', key: GlobalKey()),
        ));
  }
```
- Next designate widget to highlight :
  add in top of your main widget an array 'tutorialKeys' add as many GlobalKey as you want scene
  
```dart
class MyHomePage extends StatefulWidget {
  MyHomePage({super.key, required this.title});
  final List<GlobalKey> tutorialKeys = [GlobalKey()];// add this line
....
```

  and add tutorialKey to desired widget.

```dart
  Text(
    key: widget.tutorialKeys[0],
```
