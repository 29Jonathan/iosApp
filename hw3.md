<h1>HW3</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        ZStack{
            Rectangle()
                .fill(Color.white)
                .frame(minWidth: 0, idealWidth: 100, maxWidth: .infinity, minHeight: 0, idealHeight: 100, maxHeight: .infinity)
                .ignoresSafeArea(.all)
            Shelfview()
            VStack{
                FirstRowView()
                    .offset(x:0, y:-45)
                SecondRowView()
                    .offset(x:0, y:30)
                ThirdRowView()
                    .offset(x:0, y:80)
            }
            Image(systemName: "tag.fill")
                .foregroundColor(.black)
                .font(.system(size: 50))
                .opacity(0.8)
                .offset(x:-50, y:10)
            Text("10$")
                .opacity(0.9)
                .bold()
                .offset(x:-50, y:-25)
                .rotationEffect(Angle(degrees: -40))
        }
    }
}

struct Shelfview: View{
    var body: some View{
        VStack{
            Spacer(minLength: 150)
            Image("Shelf")
                .resizable()
                .frame(height: 200, alignment: .center)
            Image("Shelf")
                .resizable()
                .frame(height: 200, alignment: .center)
            Image("Shelf")
                .resizable()
                .frame(height: 200, alignment: .center)
        }
    }
}

struct FirstRowView: View{
    var body: some View{
        VStack{
            HStack{
                Image("Car1")
                    .resizable()
                    .frame(height: 120, alignment: .center)
                    .offset(x:0, y:30)
                Image("Car2")
                    .resizable()
                    .frame(height: 120, alignment: .center)
                    .offset(x:0, y:20)
                Image("Car3")
                    .resizable()
                    .frame(height: 120, alignment: .center)
                    .offset(x:0, y:35)
            }
            HStack{
                Text("1896")
                    .bold()
                    .foregroundColor(.white)
                    .frame(width: 60, alignment: .center)
                    .background()
                    .cornerRadius(10)
                    .offset(x:-60)
                Text("1997")
                    .bold()
                    .foregroundColor(.white)
                    .frame(width: 60, alignment: .center)
                    .background()
                    .cornerRadius(10)
                Text("2024")
                    .bold()
                    .foregroundColor(.white)
                    .frame(width: 60, alignment: .center)
                    .background()
                    .cornerRadius(10)
                    .offset(x:60)
            }
        }
    }
}    

struct SecondRowView: View{
    var body: some View{
        HStack{
            Image("Pokimon1")
                .resizable()
                .frame(height: 120, alignment: .center)
            Image("Pokimon2")
                .resizable()
                .frame(height: 120, alignment: .center)
                .offset(x:0, y:15)
            Image("Pokimon3")
                .resizable()
                .frame(height: 120, alignment: .center)
        }
    }
}

struct ThirdRowView: View{
    var body: some View{
        HStack{
            Image("Marvel1")
                .resizable()
                .frame(height: 160, alignment: .center)
            Image("Marvel2")
                .resizable()
                .frame(height: 160, alignment: .center)
            Image("Marvel3")
                .resizable()
                .frame(height: 130, alignment: .center)
        }
    }
}

    
```

<img width="40%"  src="https://github.com/29Jonathan/iosApp/blob/d06118c07c35695ca36bfc67e2242cf13a00aebd/58E1F042-FFB3-46C3-8A4B-C5152CA62B59.jpeg">
