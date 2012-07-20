# dartlib
## A collection of (mostly) general libraries to make coding [Dart](http://www.dartlang.org/) more fun.

Starting by porting bits of the [PL javascript library](https://github.com/thinkpixellab/pl) and Google's [Closure javascript library](https://developers.google.com/closure/library/) to enable some interesting scenarios.

## Highlights

### core
 * __async__
     * `SlowMapper`: a convenient way to model slow, async conversions
 * __color__
     * `RgbColor`, `HslColor` with associated conversions back and forth
     * `RgbColor` supports to/from hex
 * __math__
     * `Coordinate`, `Rect`, `Size`, `Vector`, `AffineTransfrom`
 * __properties__
     * A general model for supporting runtime-defined properties supported objects.
     * This functionality is inspired by the Dependency Property model in WPF/Silverlight.

## Blocking Bugs
Bugs blocking me from compiling to Javascript.

### Allow `final static` fields to be non-constants.
  * __Scenario:__ Allowing classes to define a `Property` using `static final Property<bool> isMouseOver Property = new Property<bool>('isMouseOver');`
  * __Work-around__
      * Define `Property` constructor as `const` even though it is not -- it creates a non-const GlobalId.
      * Create instances of `Property` with const constructor.
  * __Issues__
      * Warnings in editor about expecting `const` expressions in `Property` constructor.
      * I cannot compile my project to Javascript.
  * __Related bugs:__
    [3476](http://code.google.com/p/dart/issues/detail?id=3476),
    [3551](http://code.google.com/p/dart/issues/detail?id=3551),
    [3558](http://code.google.com/p/dart/issues/detail?id=3558),
    [3559](http://code.google.com/p/dart/issues/detail?id=3559)

### Allow compile-time constants in switch statements
  * __Scenario:__ I've defined a psedo-enum class `ShapeType` that exposes const fields which I'd like to use in a case statement.
  * __Word-around:__ Ignore the warnings in the editor.
  * __Issues:__ Unknown. I bet this won't compile to javascript, but I'm hitting other issues first.
  * __Related bug:__ [3342](http://code.google.com/p/dart/issues/detail?id=3342)

## Annoying Bugs
Bugs that cause code smells.

### Put the unittest library on [pub](http://www.dartlang.org/docs/pub-package-manager/) or let me use the copy in the SDK without hard-wired paths.
  * __Scenario:__ I'd like to use the unittest library in the SDK, but hardwiring the absolute path to the SDK makes it tough to cleanly share code with others.
  * __Work-around:__ I put an entire copy of the `unittest` code in the `vendor` directory.
  * __Issues__
      * I have to manually sync changes to the SDK code.
      * I have a copy of a lot of files that are already in the SDK.
  * __Related bugs:__
    [2518](http://code.google.com/p/dart/issues/detail?id=2518),
    [3702](http://code.google.com/p/dart/issues/detail?id=3702)


## Authors
 * [Kevin Moore](https://github.com/kevmoo) ([@kevmoo](http://twitter.com/kevmoo))
 * [Andreas Köberle](https://github.com/eskimoblood) ([@eskimobloood](https://twitter.com/eskimobloood))
 * _You? File bugs. Fork and Fix bugs. Let's build this community._

## [The BSD 2-Clause License](http://www.opensource.org/licenses/bsd-license.php)

    Copyright (c) 2012, dartlib project authors
    All rights reserved.

    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are met:

    1. Redistributions of source code must retain the above copyright notice, this
       list of conditions and the following disclaimer.
    2. Redistributions in binary form must reproduce the above copyright notice,
       this list of conditions and the following disclaimer in the documentation
       and/or other materials provided with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
    ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
    WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
    DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
    ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
    (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
    LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
    ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
    SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

    The views and conclusions contained in the software and documentation are those
    of the authors and should not be interpreted as representing official policies,
    either expressed or implied, of the FreeBSD Project.
