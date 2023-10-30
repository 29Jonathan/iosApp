<h1>Bonus</h1>
    
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

<img width="40%"  src="https://github.com/29Jonathan/iosApp/blob/7341b02b07043f224dc607588a7cc467fe9baf76/A316B403-2A68-485A-9325-57CC65A64ADC.jpeg">
