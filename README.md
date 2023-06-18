# SwiftUIGuideline

Guidelines for developing applications with SwiftUI

## Table of Contents

- [Naming](#naming)
- [Constraints](#constraints)
- [Using Property Wrappers](#using-property-wrappers)
- [Code Organization](#code-organization)
- [References](#references)

## Naming

- Any View should have a `View` or component suffix. For example: HomeView, FilterButton, TitleLabel, ValueSlider
- Closures for views should have an `on` prefix. For example: onTap, onSelection, onChange, onDrag
- The View Model should have the prefix of the View's name and the suffix `Model`. For example: HomeViewModel, FilterViewModel

## Constraints

- View initialization and body execution should be as lightweight as possible. Do not burden them with heavy computations.
- Do not extend a View beyond 100 lines. If this happens, extract components into separate Views.
- Extract separate Views into computed properties or make methods if they need to take parameters.
- Do not extend the body, computed properties, or make methods of a View beyond 50 lines.
- Extract the contents of `ForEach` into a separate View, computed property, or make method.
- Extract repeated UI in different Views into a separate View to avoid code duplication.
- Extract repeated UI within a single View into computed properties or make methods.
- Always write modifiers on a new line. Recommended:
Recommended:
```swift
MyView()
    .frame(height: 20)
```
Not recommended:
```swift
MyView().frame(height: 20)
```

## Using Property Wrappers

- `@State` - used only inside a View to modify a value. Always make it private.
- `@Binding` - declares that a value is passed from outside but can also be modified within the View.
- `@StateObject` - observes changes in an object and is responsible for data preservation. Used only inside a View. Lifecycle is the same as the View. Always make it private.
- `@ObservedObject` - observes changes in an object but is not responsible for data preservation. Used both inside and outside a View. Lifecycle is managed from outside.
- `@EnvironmentObject` - a shared object for reading/writing within a specific View hierarchy.
- `@Environment` - a shared object for use throughout the application.
- `@Published` - allows you to create observable objects that automatically notify when changes occur. SwiftUI automatically tracks such changes and re-calls the View's body, which uses the observable objects. Used both inside `ObservableObject` and outside.


## Code Organization

Follow this sequence inside View:

```swift
struct MyView: some View {
    enum { }
    struct { }
 
    private enum { }
    private struct { }

    let
    
    @Environment var
    @EnvironmentObject var
    @ObservedObject var 
    @StateObject var 
    @Binding var 
    @State var 
    var
    
    var body: some View { }
    
    private let 

    @Environment private var
    @EnvironmentObject private var
    @ObservedObject private var 
    @StateObject private var 
    @Binding private var 
    @State private var 
    private var 
    
    init() { }
    
    private func () { }
}
```

Add an empty line between sections. For example:
```swift
let state: ViewState<[String]>
let title: String
    
@Binding var filterInfo: [String: Bool]

@State private var isFilterHidden = true
```

Wrapper sequence:

```swift
    @Environment
    @EnvironmentObject
    @ObservedObject 
    @StateObject 
    @Binding 
    @State
```

## References

[Apple Tutorial](https://developer.apple.com/tutorials/swiftui/)

[First acquaintance with components and transition from UIKit](https://github.com/SimpleBoilerplates/SwiftUI-Cheat-Sheet)

[All basic things SwiftUI](https://fuckingswiftui.com)

[100 days of SwiftUI](https://www.hackingwithswift.com/100/swiftui)

[Descriptions of Property Wrappers in SwiftUI](https://disk.yandex.ru/i/5C8sPIZwXVOC7g)

