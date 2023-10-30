<h1>Bouns</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    @State var date =  Date()
    var body: some View {
        NavigationView{
            Form(content: {
                Section(header: Text("日期")){
                    DatePicker(
                        selection: $date,
                        displayedComponents: [.date],
                        label: { Text("\(date.formatted(date: .long, time: .omitted))") }
                    )
                }
            })
            .navigationBarTitle("Date Setting")
        }
    }
}

    
```

<img width="40%"  src="https://github.com/29Jonathan/iosApp/blob/d06118c07c35695ca36bfc67e2242cf13a00aebd/58E1F042-FFB3-46C3-8A4B-C5152CA62B59.jpeg">
