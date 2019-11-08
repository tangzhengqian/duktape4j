# duktape4j
```
cmake -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_C_FLAGS=-std=c99 -fstrict-aliasing \
    -DCMAKE_CXX_FLAGS=-std=c++11 -fstrict-aliasing -fexceptions \ 
    ..
```

[![AppVeyor](https://img.shields.io/appveyor/ci/WebFolder/duktape4j.svg?label=Windows)](https://ci.appveyor.com/project/WebFolder/duktape4j) [![circleci](https://img.shields.io/appveyor/ci/WebFolder/duktape4j.svg?label=Ubuntu)](https://circleci.com/gh/webfolderio/duktape4j) [![travis](https://img.shields.io/travis/webfolderio/duktape4j.svg?label=macOS)](https://travis-ci.org/webfolderio/duktape4j)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fwebfolderio%2Fduktape4j.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fwebfolderio%2Fduktape4j?ref=badge_shield)

Java binding for [Duktape](https://github.com/svaarala/duktape), a very compact embedded ECMAScript (JavaScript) engine.

ducktape4j is Java port of [duktape-android](https://github.com/square/duktape-android/).

Supported Java Versions
-----------------------

Oracle & OpenJDK Java 8, 11.

Both the JRE and the JDK are suitable for use with this library.

Stability
---------
This library is suitable for use in production systems.

Supported Platforms
-------------------
* Windows 8 & Windows 10 (64-bit)
* Ubuntu (64-bit)
* macOS High Sierra (10.13)

How it is tested
----------------
ducktape4j is regularly tested on [appveyor](https://ci.appveyor.com/project/WebFolder/duktape4j) (Windows), [circleci](https://circleci.com/gh/webfolderio/duktape4j) (Ubuntu) and [travis](https://travis-ci.org/webfolderio/duktape4j) (macOS).

Integration with Maven
----------------------

To use the official release of duktape4j, please use the following snippet in your `pom.xml` file.

Add the following to your POM's `<dependencies>` tag:

```xml
<dependency>
    <groupId>io.webfolder</groupId>
    <artifactId>duktape4j</artifactId>
    <version>1.0.0</version>
</dependency>
```

Download
--------
[duktape4j-1.0.0.jar](https://search.maven.org/remotecontent?filepath=io/webfolder/duktape4j/1.0.0/duktape4j-1.0.0.jar) - 1522 KB

Usage Examples
--------------

```java
public class HelloWorld {

    public static interface Console {
        default void info(String message) {
            System.out.println(message);
        }
    }

    public static void main(String[] args) {
        try (Duktape duktape = Duktape.create()) {
            duktape.set("console", Console.class, new Console() { });
            duktape.evaluate("console.info('hello, world!')");
        }
    }
}
```

License
-------
Licensed under the [Apache License](https://github.com/webfolderio/duktape4j/blob/master/LICENSE).

Note: The included C code from [Duktape](https://github.com/svaarala/duktape) is licensed under [MIT](https://github.com/svaarala/duktape/blob/master/LICENSE.txt) and [duktape-android](https://github.com/square/duktape-android) licensed under [Apache](https://github.com/square/duktape-android/blob/master/LICENSE).

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fwebfolderio%2Fduktape4j.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fwebfolderio%2Fduktape4j?ref=badge_large)
