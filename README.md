# WeSplit

An iOS app in SwiftUI that demonstrates the use case of basic Form and Picker. A tip calculator that calculates how much each person would have to pay given the number of people as well as the tip percentage. 

<img src="https://github.com/igibliss00/WeSplit/blob/master/README_assets/1.png" width="400">

## Features

### State

SwiftUI manages the storage of any property you declare as a state. When the state value changes, the view invalidates its appearance and recomputes the body. Use the state as the single source of truth for a given view.
A State instance isn’t the value itself; it’s a means of reading and writing the value. To access a state’s underlying value, use its variable name, which returns the wrappedValue property value.
You should **only access a state property from inside the view’s body, or from methods called by it**. For this reason, declare your state properties as private, to prevent clients of your view from accessing them. It is safe to mutate state properties from any thread.

([Source](https://developer.apple.com/documentation/swiftui/state))

We can’t simply use “mutating” to modify the variables because body is a computed property and you cannot have a mutating function inside the computed property.  @State observes the changes to the variable and allows its value to be stored separately by SwiftUI in a place that can be modified.

```
@State private var checkAmount = ""

var body: some View {
    Form {
        Section {
            TextField("Amount", text: $checkAmount)
                .keyboardType(.numberPad)
        }
        
        Section {
            Text("$\(checkAmount)")
        }
    }
}
```

1. Our text field has a two-way binding to the checkAmount property.
2. The checkAmount property is marked with @State, which automatically watches for changes in the value.
3. When an @State property changes SwiftUI will re-invoke the body property (i.e., reload our UI)
4. Therefore the text view will get the updated value of checkAmount.

([Source](https://www.hackingwithswift.com/books/ios-swiftui/reading-text-from-the-user-with-textfield))

