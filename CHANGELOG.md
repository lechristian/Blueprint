# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Master]

### Fixed

- Removed layout rounding no longer needed since [#64] ([#95]).

### Added

- [Add support for the iPhone SE 2](https://github.com/square/Blueprint/pull/96) in `ElementPreview`.
- Added `tintColor` and `contentMode` into the initializer for `Image`

### Removed

### Changed

### Deprecated

### Security

### Documentation

### Misc

# Past Releases

## [0.11.0] - 2020-05-10

### Fixed

- [Fixed `ConstrainedSize`](https://github.com/square/Blueprint/pull/87) to ensure that the measurement of its inner element respects the `ConstrainedSize`'s maximum size, which matters for measuring elements which re-flow based on width, such as elements containing text.

- Changed [BlueprintView.sizeThatFits(:)](https://github.com/square/Blueprint/pull/92/files) to treat width and height separately when determining if measurement should be unconstrained in a given axis.

### Added

- [Added support](https://github.com/square/Blueprint/pull/88) for `SwiftUI`-style element building within `BlueprintUI` and `BlueprintUICommonControls`.

  This allows you to replace this code:

  ```swift
  ScrollView(.fittingHeight) (
    wrapping: Box(
      backgroundColor .lightGrey,
      wrapping: Inset(
        uniformInset: 10.0,
        wrapping: ConstrainedSize(
          height: .atLeast(20.0),
          wrapping: Label(
            text: "Hello, world!"
          )
        )
      )
    )
  )
  ```

  With this code:

  ```swift
  Label(text: "Hello, World!")
    .constrainedTo(height: .atLeast(20.0))
    .inset(by: 20.0)
    .box(background: .lightGrey)
    .scrollable(.fittingHeight)
  ```

  Improving readability and conciseness of your elements.


## [0.10.0] - 2020-04-27

### Added

- BlueprintView will align view frames to pixel boundaries after layout ([#64]).

## [0.9.2] - 2020-04-27

### Fixed

- [Don't try to build](https://github.com/square/Blueprint/pull/89) `SwiftUI` previews on 32 bit ARM devices – `SwiftUI` does not exist on these devices.

## [0.9.1] - 2020-04-17

### Fixed

- Weak link `SwiftUI` so if an app is not already linking `SwiftUI`, it will build correctly.

## [0.9.0] - 2020-04-17

### Added

- [Add support](https://github.com/square/Blueprint/pull/76) for previewing Blueprint elements in Xcode / SwiftUI previews.
- [Add accessibilityIdentifier](https://github.com/square/Blueprint/pull/81) support to `AccessibilityElement`.

## [0.8.0] - 2020-04-03

### Fixed

- [Properly measure](https://github.com/square/Blueprint/pull/73) the child of `ScrollView` to allow for unconstrained measurement.
- Fix stack layout during underflow ([#72])

### Added

- ScrollView can automatically adjust its content inset for the keyboard ([#55])

### Changed

- Improved element diffing ([#56])

## [0.7.0] - 2020-03-30

### Added

- Xcode 11 and Swift 5.1 support ([#67]).

### Changed

- Change how stack [layouts are measured][#68] to resolve an issue where text would be truncated.

### Removed

- Raise minimum deployment target from iOS 9.3 to iOS 10 ([#66]).

## [0.6.0] - 2020-02-24

### Added

- Add `keyboardDismissMode` property on ScrollView ([#57]).
- Add `textAlignment` property on TextField ([#53]).

## [0.5.0] - 2020-01-24

### Fixed

- Prevent divide-by-zero when a stack contains zero-size elements ([#52]).

### Added

- Add `fill` alignment to Aligned ([#42]).

### Documentation

- Fix typos in the tutorial ([#46]).
- Add docs to Overlay ([#45]).

## [0.4.0] - 2019-12-04

### Fixed

- Public init on Aligned ([#41]).

### Changed

- Guarantee that subviews are ordered the same as their associated elements ([#32]).

## [0.3.1] - 2019-11-15

### Fixed

- Do not run snapshot tests from CocoaPods ([#40]).
- Make tests with float comparisons more lenient for 32-bit ([#35]).

### Added

- Add Swift Package Manager support ([#37]).

### Documentation

- Add Getting Started section to README ([#38]).

## [0.3.0] - 2019-11-12

### Added

- Add Stack alignment options `justifyToStart`, `justifyToCenter`, and `justifyToEnd` ([#24]).
- Add ConstrainedAspectRatio element ([#23]).
- Add EqualStack element ([#26]).
- Add Rule element ([#22]).
- Add Aligned element ([#21]).
- Add a screen scale property to some elements ([#18]).
- Swift 5 support ([#15]).

### Changed

- Reorder the parameters of ConstrainedSize, Inset, Button, and Tappapble, so that the wrapped element is the last parameter ([#19]).

## [0.2.2] - 2019-03-29

- First stable release.

[master]: https://github.com/square/Blueprint/compare/0.11.0...HEAD
[0.11.0]: https://github.com/square/Blueprint/compare/0.10.0...0.11.0
[0.10.0]: https://github.com/square/Blueprint/compare/0.9.2...0.10.0
[0.9.2]: https://github.com/square/Blueprint/compare/0.9.1...0.9.2
[0.9.1]: https://github.com/square/Blueprint/compare/0.9.0...0.9.1
[0.9.0]: https://github.com/square/Blueprint/compare/0.8.0...0.9.0
[0.8.0]: https://github.com/square/Blueprint/compare/0.7.0...0.8.0
[0.7.0]: https://github.com/square/Blueprint/compare/0.6.0...0.7.0
[0.6.0]: https://github.com/square/Blueprint/compare/0.5.0...0.6.0
[0.5.0]: https://github.com/square/Blueprint/compare/0.4.0...0.5.0
[0.4.0]: https://github.com/square/Blueprint/compare/0.3.1...0.4.0
[0.3.1]: https://github.com/square/Blueprint/compare/0.3.0...0.3.1
[0.3.0]: https://github.com/square/Blueprint/compare/0.2.2...0.3.0
[0.2.2]: https://github.com/square/Blueprint/releases/tag/0.2.2
[#95]: https://github.com/square/Blueprint/pull/95
[#72]: https://github.com/square/Blueprint/pull/72
[#68]: https://github.com/square/Blueprint/pull/68
[#67]: https://github.com/square/Blueprint/pull/67
[#66]: https://github.com/square/Blueprint/pull/66
[#64]: https://github.com/square/Blueprint/pull/64
[#57]: https://github.com/square/Blueprint/pull/57
[#56]: https://github.com/square/Blueprint/pull/56
[#55]: https://github.com/square/Blueprint/pull/55
[#53]: https://github.com/square/Blueprint/pull/53
[#52]: https://github.com/square/Blueprint/pull/52
[#46]: https://github.com/square/Blueprint/pull/46
[#45]: https://github.com/square/Blueprint/pull/45
[#42]: https://github.com/square/Blueprint/pull/42
[#41]: https://github.com/square/Blueprint/pull/41
[#40]: https://github.com/square/Blueprint/pull/40
[#38]: https://github.com/square/Blueprint/pull/38
[#37]: https://github.com/square/Blueprint/pull/37
[#35]: https://github.com/square/Blueprint/pull/35
[#32]: https://github.com/square/Blueprint/pull/32
[#26]: https://github.com/square/Blueprint/pull/26
[#24]: https://github.com/square/Blueprint/pull/24
[#23]: https://github.com/square/Blueprint/pull/23
[#22]: https://github.com/square/Blueprint/pull/22
[#21]: https://github.com/square/Blueprint/pull/21
[#19]: https://github.com/square/Blueprint/pull/19
[#18]: https://github.com/square/Blueprint/pull/18
[#15]: https://github.com/square/Blueprint/pull/15
