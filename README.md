<!-- 
This README describes the package. If you publish this package to pub.dev,
this README's contents appear on the landing page for your package.

For information about how to write a good package README, see the guide for
[writing package pages](https://dart.dev/guides/libraries/writing-package-pages). 

For general information about developing packages, see the Dart guide for
[creating packages](https://dart.dev/guides/libraries/create-library-packages)
and the Flutter guide for
[developing packages and plugins](https://flutter.dev/developing-packages). 
-->

A simple tool (really simple, about 20 lines of code) to convert a dart object, including `null`, in a `bool` (`true|false`), quite similar to how the twice operator (`!!`) works in Javascript and Typescript.

## Features

You can use it as an operator (`~` or twice `~~`), as an extension (property `.asBool`) or as a simple helper method (`asBool(value)`).

> **IMPORTANT CAVEAT:** The operator `~` doesn't work with `int` values because is used for [bit-wise negate operator](https://api.flutter.dev/flutter/dart-core/int/operator_bitwise_negate.html), for `int` objects use the extension or helper method

What values are convert to `false`

* `null` 
* `0` And `0.0`
* `double.nan` "Not a Number" values
* `""` Empty Strings
* `[]` Empty iterable objects
* `<any>.isEmpty == true` Whatever object with a `isEmpty` property that returns `true` (i.e, a `Map` or any custom class that implement `isEmpty`)

All other values are considered as `true`.

## Getting started

Add the package `asbool` to your project:

```bash
dart pub add asbool
```

Import the package, but if you prefer don't add the extension or the operator you can use different imports:

```dart
import 'package:asbool/asbool.dart'; // All included
```

All options are included: helper method, extension and operator.


```dart
import 'package:asbool/asbool_extension.dart'; // Only helper method and extension
```

Only 2 options are included: helper method and extension.


```dart
import 'package:asbool/asbool_helper.dart'; // Only helper method
```

Only helper method is imported.

## Usage

Use the tool as you wish

```dart
final foo = 'Hi';
final bar = [];
final m = {'a':'b'};

assert(~~foo == foo.asBool); // true == true
assert(asBool(foo) == ~~12); // true == true

assert(asBool(bar) == bar.asBool); // false == false
assert(asBool(0.0) == ~~double.nan); // false == false
assert(~~m == true); // true == true
assert(asBool({}) == false); // false == false
```

## Additional information

If you have any suggestion or problem with the lib, please open an issue and I'll try to help.

