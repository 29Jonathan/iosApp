<h1>HW1</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        ZStack{
            Rectangle()
                .fill(Color(red: 235/255, green: 205/255, blue: 203/255))
                .frame(minWidth: 0, idealWidth: 100, maxWidth: .infinity, minHeight: 0, idealHeight: 100, maxHeight: .infinity, alignment: .center)
                .ignoresSafeArea(.all)
            VStack{
                Text("110352     黃書逸")
                    .font(.system(size: 35, weight: .bold))
                    .frame(width: 400, height: 20, alignment: .center)
                    .offset(x: 0, y: 100)
                
                Text("How are you today ?\nA beautiful day !")
                    .fontWeight(.heavy)
                    .lineSpacing(10)
                    .font(.system(size: 22))
                    .foregroundColor(.white)
                    .frame(width: 400, height: 200, alignment: .top)
                    .padding(.top, 20)
                    .background(Color.blue)
                    .cornerRadius(60)
                    .opacity(0.7)
                    .offset(x: 0, y:130)
                    .multilineTextAlignment(.center)
                
                Image("Me")
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .frame(width: 400, height: 500, alignment: .trailing)
                    .cornerRadius(80)
            
            }
            Image(systemName: "graduationcap.fill")
                .foregroundColor(.red)
                .font(.system(size: 80))
                .position(x: 295, y: 360)
            Image(systemName: "bubble.right")
                .font(.system(size: 70))
                .foregroundColor(.white)
                .frame(width: 100, height: 150, alignment: .bottom)
            Text("Hello")
                .font(.title)
                .foregroundColor(.white)
                .frame(width: 100, height: 90, alignment: .bottom)
        }
    }
}

    
```

<img width="40%"  src="https://github.com/29Jonathan/iosApp/blob/e530f761f90c971d071c93d1c389c973777366ac/974884B4-C235-4D6D-9E74-CBF757826C83.jpeg">
