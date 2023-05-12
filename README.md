# SwiftUI-iPad-Enter-text-and-answer.
You can enter text and the computer judgment and answer. iPad swift playground.

# The first part
Enter the first text
![IMG_1116](https://github.com/S-way520/SwiftUI-iPad-Enter-text-and-answer./assets/95877651/4eaa7b6a-493a-4115-ab72-837c02fdf43f)
Enter the second text
![IMG_1117](https://github.com/S-way520/SwiftUI-iPad-Enter-text-and-answer./assets/95877651/fbf151bd-298d-4f1e-9e00-542310ca7394)
Enter the third text
![IMG_1118](https://github.com/S-way520/SwiftUI-iPad-Enter-text-and-answer./assets/95877651/acbf47d8-9303-4fc7-9893-61e94a3e5da5)

# The second part
First file
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Second file
```swift
import SwiftUI
struct ContentView: View {
    var body: some View {
        MyTextFieldView()
    }
}
struct MyTextFieldView: View {
    @State private var text = ""
    @State private var confirmedText = ""
    @State private var show1Alert = false
    @State private var show2Alert = false
    @State private var show3Alert = false
    var body: some View {
        if show1Alert {
            Text("You said \(text) Well, let's start today's story")
                .padding(60)
        }
        if show2Alert {
            Text("We don't have to go out anymore. Let's continue to tell the story.")
                .padding(60)   
        }
        if show3Alert {
            Text("Do you know 烟雨行舟？")
                .padding(60)
        }
        VStack {
            Spacer()
            Text("What color is the sky today?")
            HStack{
                TextField("Enter here", text: $text)
                    .textFieldStyle(.roundedBorder)
                Button(action: {confirmedText = text}, label: {
                    Image(systemName: "paperplane")
                })
                .onChange(of: confirmedText, perform: { value in
                    if confirmedText.contains("blue") {
                        show1Alert = true
                        show2Alert = false
                        show3Alert = false
                    } 
                    if confirmedText.contains("grey") {
                        show2Alert = true
                        show1Alert = false
                        show3Alert = false
                    }
                    if confirmedText.contains("raining") {
                        show3Alert = true
                        show1Alert = false
                        show2Alert = false
                    }
                })
            }
        }
        .padding()
    }
}
```
