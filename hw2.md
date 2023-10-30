<h1>HW2</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    @State var cpu:Int = 0
    var cpuImage = ["Rock", "Scissors", "Paper"]
    @State var gameOut = ""
    @State var point = 100
    @State var money = 20
    @State var runTime = 1.5
    @State var timerRunning = false
    @State var timer = Timer.publish(every: 0.1, on: .main, in: .common).autoconnect()
    
    
    var body: some View {
        ZStack{
            Rectangle()
                .fill(Color(red: 235/255, green: 205/255, blue: 203/255))
                .frame(minWidth: 0, idealWidth: 100, maxWidth: .infinity, minHeight: 0, idealHeight: 100, maxHeight: .infinity, alignment: .center)
                .ignoresSafeArea(.all)
            VStack{
                Image(cpuImage[cpu])
                    .resizable()
                    .scaledToFit()
                    .frame(width: 250, height: 250, alignment: .center)
                    .offset(x: 0, y: 20)
                Text("your $: \(point)")
                    .font(.system(size: 50, weight: .bold))
                    .foregroundStyle(Color.brown)
                    .opacity(0.7)
                    .offset(x: 0, y: 50)
                Text("\(gameOut)")
                    .foregroundStyle(Color.red)
                    .offset(x: 0, y: 70)
                HStack{
                    Button(action: {
                        timerRunning = true
                        cpuRandom()
                        checkWin(my: 0, cpu: cpu)
                    }, label: {
                        Image("Rock")
                            .resizable()
                            .scaledToFit()
                    })
                    
                    Button(action: {
                        timerRunning = true
                        cpuRandom()
                        checkWin(my: 1, cpu: cpu)
                    }, label: {
                        Image("Scissors")
                            .resizable()
                            .scaledToFit()
                        
                    })
                    
                    Button(action: {
                        timerRunning = true
                        cpuRandom()
                        checkWin(my: 2, cpu: cpu)
                    }, label: {
                        Image("Paper")
                            .resizable()
                            .scaledToFit()
                    })
                }
                .offset(x: 0, y: 60)
                
                HStack{
                    Button(action: {
                        if money == 20{
                            money = 50
                        }
                        else if money == 50{
                            money = 20
                        }
                    }, label: {
                        Image("Bet")
                            .resizable()
                            .scaledToFit()
                            .offset(x: 0, y: 50)
                    })
                    
                    Text("Bet: \(money)")
                        .foregroundStyle(Color.black)
                        .font(.system(size: 30, weight: .bold))
                        .opacity(0.7)
                        .offset(x: 0, y: 50)
                }
            }
            .onReceive(timer) { _ in
                if runTime>0 && timerRunning{
                    if cpu<2 {
                        cpu += 1
                    }else{
                        cpu = 0
                    }
                    runTime -= 0.1
                }else{
                    timerRunning = false
                    runTime = 1.5
                    
                }
            }
        }
    }
    func cpuRandom(){
        cpu = Int.random(in:0...2)
    }
    func checkWin(my:Int, cpu:Int){
        //0:rock 1:scissors 2: paper
        if (my==0 && cpu==1)||(my==1 && cpu==2)||(my==2 && cpu==0) {
            gameOut = "Win"
            point += money
        }else if (my==0 && cpu==0)||(my==1&&cpu==1)||(my==2 && cpu==2) {
            gameOut = "Draw"
        }else{
            gameOut = "Lose"
                point -= money
        }
        
    }
}

    
```

<"https://yzu365-my.sharepoint.com/:v:/g/personal/s1103525_mail_yzu_edu_tw/EYwUo_hQCEtGluGsZupQs10BmPDPIwWuUKTLA1vVvkViIw?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0RpcmVjdCJ9fQ&e=Ew5mbL">
