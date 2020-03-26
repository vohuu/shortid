# shortid

[![Build Status](https://travis-ci.org/bolorundurowb/shortid.svg?branch=master)](https://travis-ci.org/bolorundurowb/shortid)  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![NuGet Badge](https://buildstats.info/nuget/shortid)](https://www.nuget.org/packages/shortid) [![Coverage Status](https://coveralls.io/repos/github/bolorundurowb/shortid/badge.svg?branch=master)](https://coveralls.io/github/bolorundurowb/shortid?branch=master)

## About ShortId

A CSharp library to generate completely random short id's. They can be used as primary keys or unique identifiers. This library is different in that you can specify the length of the id's generated. I have tested the application generating 180000 id's without duplicates.

## How to use

To make use of the `shortid`, add it to your project via the Nuget package manager UI or console via this command:

```
Install-Package shortid
```

Add the following using command to the top of your csharp code file:

```csharp
using shortid;
```

This gives your code access the classes and methods of the `shortid` namespace.

To generate a unique id of any length between 7 and 14, you call the `Generate` method without parameters.

```csharp
string id = ShortId.Generate();
// id = KXTR_VzGVUoOY
```

If you want to include numbers in the generated id, then you call the `Generate` method with a boolean indicating your preference.

```csharp
string id = ShortId.Generate(true);
// id = O_bBY-YUkJg
```

If you do not want special characters *i.e _ and -* in your generated id, then call the `Generate` method with two boolean parameters, the first indicating whether or not you want numbers and the second indicating whether or not you want special characeters.

```csharp
string id = ShortId.Generate(true, false);
// id = waBfk3z
```

If you want to specify the length of the generated id, call the `Generate` method with an integer parameter which is the desired length.

```csharp
string id = ShortId.Generate(8);
// id = M-snXzBk
```

If you want to control the type of id generated by specifying whether you want numbers, special characters and the length, call the `Generate` method and pass three parameters, the first a boolean stating whether you want numbers, the second a boolean stating whether you want special characters, the last a number indicating your length preference.

```csharp
string id = ShortId.Generate(true, false, 12);
// id = VvoCDPazES_w
```

**NOTE: v2.0.0 introduced a change that prevents lengths of less than 7**


## Customize ShortId

`ShortId` has several features that help with customizing the ids generated. Characters sets can be introduced and the random number generator can be seeded.

To change the character set in use, run the following:

```csharp
string characters = //whatever you want;
ShortId.SetCharacters(characters);
```

**NOTE: the new character set must not be `null`, an empty string or whitespace. Also, all whitespace characters would be removed, finally the character set cannot be less than 20 characters.**

`ShortId` also allows the seed for the random number generator to be set.

To set the seed, run the following:

```csharp
int seed = 1939048828;
ShortId.SetSeed(seed);
```

Finally, `ShortId` allows for all customizations to be reset using the following:

```csharp
ShortId.Reset();
```
