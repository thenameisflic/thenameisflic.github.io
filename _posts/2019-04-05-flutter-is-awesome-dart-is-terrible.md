---
layout: single
title: "Flutter is Awesome, Dart not so much"
tags:
  - quick take
---

I've been working in production apps for some months now with Flutter, and i have to say: i've been loving all of it, except the part of it that is made of Dart.

# The things that make Flutter awesome

I won't get into the merits of the hybrid app approach like a single codebase for Android / iOS, you already know that. Instead, i'll compare it with React Native, and i have to tell you: for building layout and functionality, it feels a lot like jumping from Java Swing to Electron in the amount of customization and ease of use in each and every aspect of your application.

Unlike React Native, Flutter components just make sense. We have a ListView (FlatList equivalent), but we also have a ListTile to easily display good looking, native-like lists out of the box. We can use slivers to easily implement [incredible scroll behaviours](https://stackoverflow.com/questions/53747149/tabbarview-without-bounded-height).

Navigation is a breeze, too. I have no idea why all React Native navigation options need to be so cumbersome. Drawers, TabBars, passing parameters / getting values from screens is incredibly simple: it's all widgets all the way down in Flutter. Need to display an app bar? Just add the `AppBar` component to your layout. Need Tabs instead? `TabBar` is simple too, and supports swiping out of the box.

We lost a good deal of performance when we stopped using native platforms like Java Swing for Electron, but with Flutter it has been quite the contrary: my hybrid apps have never been so performant, especially in low-end devices. In my very own Moto C (1.1 GHZ Quad Core, 1 GB, Android 7), my apps have never been as snappy as they are with Flutter with absolutely zero optimizations.

# The things that make Dart awkward

I understand [why Flutter's developers decided to go with Dart](https://flutter.dev/docs/resources/faq#why-did-flutter-choose-to-use-dart). However, i take issue with one of their points: that Dart is a productive language for building layouts.

Let's face it: Dart is a JavaScript wannabe. It was supposed to help developers overcome JavaScript limitations (like CoffeeScript), but after ES6+, i feel like we don't really have a need for its improvements anymore.

Flutter code looks very, very awkward. Take a look at this example `build` function:

```dart
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        ListTile(
          leading: CircleAvatar(
            backgroundImage: AssetImage('assets/Avatar.jpg'),
          ),
          title: Text('News'),
          subtitle: Text("Stay tuned"),
        ),
        Divider(),
      ]..addAll(
          this.news.map(
            (item) {
              return ListTile(
                leading: CircleAvatar(
                  backgroundImage: AssetImage('assets/Newspaper.png'),
                  foregroundColor: Colors.purple,
                ),
                title: Text("${item.title}"),
                subtitle: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Text(timeago.format(item.createdAt, locale: 'en')),
                    Container(
                      height: Spacing.space1,
                    ),
                    Text(item.subtitle)
                  ],
                ),
              );
            },
          ),
        ),
    );
  }
```

You'll find plenty of code like this on the internet if you decide to spend any time at all hacking with Flutter. Besides not being very clear (to me, but that's very subjective) I see several problems with this code, lets take a look at a few of them and see what Dart does currently (and what would be my ideal solution).

### Bracket hell

It feels like Lisp all over again. You'll waste a lot (and i mean a LOT) of time trying to stop compilation errors when you add or remove any component.

*The current solution*: Use trailing commas. `dartfmt` by default only breaks a new line in your code (adding a nice identation) if it finds trailing commas. There's an [open issue](https://github.com/dart-lang/dart_style/issues/753) for doing this automatically, but don't count on it being implemented anytime soon.

*Ideal solution*: Add syntactic sugar to enable XML-like code. There's a [community transpiler](https://spark-heroku-dsx.herokuapp.com/index.html) that already does that, but this seems like a [controversial idea](https://github.com/flutter/flutter/issues/11609). Just take a look at the same code written in a JSX-like syntax:

Just take a look at how easy it is to read the same code in JSX:

```jsx
<Column>
    <ListTile leading={<CircleAvatar backgroundImage={AssetImage('assets/Avatar.jpg')}/>} title="News" title="Stay tuned" />
    <Divider>
    {...this.news.map(item => (
        <ListTile leading={<CircleAvatar backgroundImage={AssetImage('assets/Avatar.png')} foregroundColor={Colors.purple} />} title={item.title} subtitle={
            <Column crossAxisAlignment={CrossAxisAlignment.start}>
                <Text>{timeago.format(item.createdAt, locale: 'en')}</Text>
                <Container height={Spacing.space1} />
                <Text>{item.subtitle}</Text>
            </Column>
        } />)
    )}
</Column>
```

### No spread operator

I really miss JavaScript's `...` spread operator when working with any language that doesn't support it. Working with collections is a huge part of building layouts, and the lack of a simple way to mash up two or more arrays together makes this really painful.

*The current solution*: Use `..addAll`, as i did in the code above.

*The ideal solution*: Just add the spread operator! There's an [open issue](https://github.com/dart-lang/language/issues/47) for that already, so it seems like this one might be coming soon.

### No index in map / reduce

I didn't use this feature is the example, but it is reasonable to expect that you could easily recover the index in any collection higher order function such as `map` or `reduce`. This isn't however the case with Dart, as it doesn't provide a second argument to the callback.


*The current solution*: To access the index of the element you're currently iterating over, you need to write code like this:

```dart
for (var i in values.asMap().keys.skip(1)) {
  isUp.add(values[i] > values[i - 1]);
}
```

*The ideal solution*: It looks like Dart won't support this in the best way possible, which would be simply [adding the argument to the original `map` function](https://github.com/dart-lang/sdk/issues/5245). The alternative, extension functions, would be good enough for me, though.

# The conclusion

Dart isn't a well designed language, and writing UIs with it is very awkward. However, this shouldn't stop you from trying out Flutter. If you find that writing code like that just won't work for you, React Native will always embrace you.

Thanks for reading! Feel free to [discuss this article on Github](https://github.com/thenameisflic/thenameisflic.github.io).
