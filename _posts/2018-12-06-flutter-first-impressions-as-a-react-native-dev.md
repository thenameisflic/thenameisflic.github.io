---
layout: single
title: "Flutter - My first impressions as a React Native developer"
---

## Flutter has been stable for a while now, so its time to get our hands *dart*y.

## Pre-impressions
Before beginning, i need to mention i only have a very loose idea about what Flutter is, what it can do and why you should use it. Here's why it took me so long to do a test drive:

1. Flutter is from Google

    We all know Google has a habit of killing lots of services. I've just checked [Killed by Google](https://killedbygoogle.com/), and boy, did you know there are already 6 services scheduled to die over the next year?
    You might argue its different for its devtools, but does anyone remember AngularJS? What about Polymer? Very hyped for a few months (AngularJS even hyped for years!), but slowly replaced and eventually died down to simpler, more stable libraries such as React and Vue.

    That said, i'm willing to give Flutter the benefit of doubt since 1) Google has been using it to write apps for its new [Fuchsia](https://en.wikipedia.org/wiki/Google_Fuchsia) project and 2) [Alibaba and Tencent](https://flutter.io/showcase) are using it. This means even if Google decides to dorp it, some other companies could keep it moving forward.

2. React Native is great

    It really is. Even though Android often feels like a second-class citizen there, the community is so big it has already solved most of the problems you can find. Also, one of the biggest claims that Flutter has is that it is fast, but i wouldn't call React Native exactly slow. Sure, it sometimes takes a long time to reload, but that's happens mostly when you aren't careful when designing your component hierarchy.

3. Flutter uses Dart

    I'm really baffled about the decision to not use JavaScript. I mean, JavaScript has a lot of flaws, but me and everyone else is just so used to it that writing a framework in anything else feels like we're going to have to work twice as hard to get into Flutter. That said, Dart doesn't look that hard, and i'm sure [there are some good reasons to use it](https://hackernoon.com/why-flutter-uses-dart-dd635a054ebf).


## Installation
To get started with Flutter, you need do download the Flutter SDK. This is a little different from React Native, since all you need there is to install the react-native npm package. No problem so far.

The first command you must run is `flutter doctor`, and boy do i love this command. There's nothing worse than following along a tutorial line by line only to figure out your machine is doing something different than the tutorial should do, so congrats to Flutter here: that's just great Developer Experience. 

Here's my first `flutter doctor` output:

```
Doctor summary (to see all details, run flutter doctor -v):
[!] Flutter (Channel stable, v1.0.0, on Linux, locale C.UTF-8)
    ✗ Downloaded executables cannot execute on host.
      See https://github.com/flutter/flutter/issues/6207 for more information
      On Debian/Ubuntu/Mint: sudo apt-get install lib32stdc++6
      On Fedora: dnf install libstdc++.i686
      On Arch: pacman -S lib32-libstdc++5

[✗] Android toolchain - develop for Android devices
    ✗ Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.io/setup/#android-setup for detailed instructions).
      If Android SDK has been installed to a custom location, set $ANDROID_HOME to that location.
      You may also want to add it to your PATH environment variable.

[!] Android Studio (not installed)
[!] Connected device
    ! No devices available

! Doctor found issues in 4 categories.
```

The first issue was solved by installing `lib32stdc++6` and following this [Github reply](https://github.com/flutter/flutter/issues/6207#issuecomment-373100050). I really don't like it when to solve a problem you need to run a random command on a random Github issue, but it's not like we in the JavaScript community aren't used to it, so [YMMV](https://dictionary.cambridge.org/us/dictionary/english/ymmv).

> ### Windows Subsystem for Linux (WSL) and Flutter
> The official guide suggests you should install Android Studio or Flutter for VSCode. I did all of the above setup on the Linux bash, but hot reload doesn't seem to work if i don't use one of these supported editors. So, if you're thinking of installing Flutter with WSL, be aware that you won't get the magic "save file and app reloads" just by typing `flutter run` in the terminal.

After installing the VSCode Flutter extension, i just typed `Flutter: New Project` and it created and opened a new Flutter project for me. With `Flutter: Run`, the project worked wonderfully on the first try, so more points to the Flutter developers here!

## Getting our hands dirty with Dart

The official guide suggests this is what a typical Flutter app looks like:

```
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Welcome to Flutter',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

My two cents about this:

1. The language looks great! It has object-oriented programming, arrow functions, annotations and named arguments.
2. That `build` method doesn't look quite good. It harkens me back to the old days of Java desktop apps: sure, it doesn't look as bad, but compare it to the JSX equivalent of that:

```
    <MaterialApp title="Welcome to Flutter">
        <Scaffold
            appBar={<AppBar title="Welcome to Flutter" />}
            body={<Center child={<Text>Hello World</Text>} />}
        />
    </MaterialApp>
```

## Package management with pubspec.yaml

No issues here, pubspec.yaml works well and seems to be very well designed. As an aside, i really liked that, as soon as i update the file, the VSCode Flutter extension automatically runs the commands needed so that i can start using the extension right away. Well done!

## Building widgets

In Flutter there are two kinds of widgets, Stateless (immutable) and Stateful (maintain state that might change during the lifetime of the widget). That's a simple enough concept, and i like that it is enforced at the framework level.

## Lists and conditionals

You use the language features (such as `map`) to build lists of items and to create conditionals, React-style. You can also use the `ListView` with lots of goodies bundled in for you. 

## Theming and Styling

Styling in Flutter uses widgets. For example, to create some padding, you use the `Padding` class. That's... unconventional, to say the least.

Here's an example of a simple circle avatar image:

```
new Container(
    width: 40.0,
    height: 40.0,
    margin: EdgeInsets.only(right: 16.0),
    decoration: new BoxDecoration(
        shape: BoxShape.circle,
        image: new DecorationImage(
            fit: BoxFit.fill,
            image: new NetworkImage(
                "https://i.imgur.com/BoN9kdC.png"))))
```

Sure, you can (and should!) create a wrapper for that, but this snippet just doesn't feel right. `border-radius` has been around for a long time, and something like it would work wonders here.

## Wrapping up (for now)

There are a lot of other things i have to research about Flutter, but these are the ones the official guide walks us through (and will do for now). Flutter is a great piece of technology with a great focus on Developer Experience, but it has some details that might still need some improvement to get right.

I hope these insights have been helpful to you! Thanks for reading!
