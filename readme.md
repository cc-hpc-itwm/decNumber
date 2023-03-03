# Decimal Floating Point decNumber C Library

The decNumber Library was written by IBM Fellow Mike Cowlishaw, and is included here with his permission.  This repository is primarily some patches, explanations, and a simple build script for the decNumber library.

- The official [decNumber Website](http://speleotrove.com/decimal/) has additional information, documentation, library code, and examples.
- The [decNumber documentation](decNumber-icu-368/decnumber.pdf) is included with the code.
- Understanding the [problems with binary floating-point](http://speleotrove.com/decimal/decifaq1.html#inexact) should be required reading for all software developers.
- The [Patriot Missile Failure](http://www-users.math.umn.edu/~arnold/disasters/patriot.html) is a real world example of why all of this matters and is pretty important.
- The WikiPedia page for [Floating-point arithmetic](https://en.wikipedia.org/wiki/Floating-point_arithmetic) has more in-depth information.

The decNumber library provides data types and functions that can be used in software to correctly calculate values using *Decimal Floating-Point* (specifically *not* binary floating-point, i.e. the `double` and `float` types exposed in most programming languages).

Decimal Floating Point (DFP) must be used when calculations need to be performed on values that have digits to the right of the radix-point, where such values are expected to be base-10 (money and accounting, engineering, statistics, etc.); for example where it would be expected that an expression like `0.1 x 10` would equal `1.0` without rounding errors.  This is the same problem you find when trying to represent 1/3 using decimal, for example.

Floating-point numbers in computing are represented in the following form:
```
significand x base^exponent
```

The `double` and `float` data types supported directly by most modern CPUs, and exposed in languages like C, C++, Java, etc., are *BINARY* Floating Point (BFP) and have a binary base (base-2).  Therefore, these data types cannot be used to accurately represent values that require a decimal base (base-10).  The difference is subtle, but critical:

Decimal: `significand x 10^exponent`
Binary:  `significand x  2^exponent`

For an in-depth understanding, a good starting point is the WikiPedia page on [Floating-point arithmetic](https://en.wikipedia.org/wiki/Floating-point_arithmetic).  A software developer should have a basic understanding of how computers store and computer numbers, and at the very least know when binary vs decimal floating-point is appropriate and acceptable to use.

`rant-on`
Some languages (COBOL, for example) and CPUs (IBM makes a bunch of them) directly support decimal floating-point, and have kept software working correctly for decades (everyone should be very thankful that most large financial companies use a Mainframe running some "ancient" software written in COBOL!)  But speed won over accuracy and common sense (which tends to be the case with computer and CPU architecture these days), and binary floating-point units became the norm in most CPUs.  Without common hardware support for decimal floating-point, the unfortunate side effect is that the knowledge about binary vs decimal floating-point fades away and most software developers are never exposed to the situation.
`rant-off`
