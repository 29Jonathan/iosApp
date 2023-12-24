<h1>HW4</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    var currentTime = Date.now
    var body: some View {
        VStack {
            
            TabView{
                Group{
                    VStack{
                        Text("\(currentTime, style: .time)")
                            .font(.system(size: 60))
                            .bold()
                            .offset(y:-70)
                        ScrollView{
                            HomeView(headline:"Messages", printline: "Jonathan: Have you finished hw4?")
                            HomeView(headline:"Instagram", printline: "Sam: Wanna play some games?")
                            HomeView(headline:"Gmail", printline: "Boss: You are fire and there's nothing I can do.")
                            HomeView(headline:"Messages", printline: "Yomi: Are you ok?")
                        }
                        .frame(width: 380, height: 180)
                    }
                    .tabItem { 
                        Image(systemName: "homekit")
                        Text("Home")
                    }
                    ContactsView()
                        .tabItem { 
                            Image(systemName: "person.crop.circle.dashed")
                            Text("Contacts")
                        }
                    KeypadView()
                        .tabItem{
                            Image(systemName: "circle.grid.3x3.fill")
                            Text("Keypad")
                        }
                    MessagesView()
                        .tabItem { 
                            Image(systemName: "message.fill")
                            Text("Messages")
                        }
                }
                //.toolbarBackground(Color.gray, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
                .toolbarColorScheme(.light, for: .tabBar)
            }
            //.tint(.blue)
        }
    }
}

struct HomeView: View{
    var headline:String
    var printline:String
    
    var body: some View{
        VStack{
            VStack(alignment: .leading, content: {
                Text(headline)
                    .font(.headline)
                    .foregroundStyle(.secondary)
                Text(printline)
                    .foregroundStyle(.primary)
            })
            .frame(minWidth: 0, idealWidth: 100, maxWidth: .infinity,minHeight: 70, alignment: .leading)
            .padding(.horizontal, 30)
        }
        .background(Color(red:211/255, green:211/255, blue:211/255))
        .clipShape(.rect(cornerRadius: 20))
        .padding(.horizontal, 30)
    }
}


struct ContactsView: View{
    struct Person {
        var image:String
        var name:String
        var number:String
    }
    var persons = [
        Person(image: "P1", name: "Mom", number: "0912345678"),
        Person(image: "P2", name: "Dad", number: "0911111111"),
        Person(image: "P3", name: "Sam", number: "0910000000"),
        Person(image: "P4", name: "Jonathn", number: "0911212121"),
        Person(image: "P5", name: "Yomi", number: "0999999999")
    ]
    var body: some View{
        VStack{
            NavigationView{
                List(persons, id:\.name){
                    thisPerson in
                    HStack{
                        Image(thisPerson.image)
                            .resizable()
                            .frame(width: 40, height: 40)
                            .cornerRadius(5)
                        Text(thisPerson.name)
                        Spacer()
                        Image(systemName: "phone")
                        Text(thisPerson.number)
                            .font(.footnote)
                    }
                }
                .navigationTitle("聯絡人")
            }
        }
    }
}

struct KeypadView: View{
    let nums = ["1", "2", "3","4", "5", "6", "7", "8", "9", "*", "0", "#"]
    var body: some View{
        VStack(spacing: 20){
            HStack(spacing: 20){
                ForEach(0..<3) { item in
                    Button(action: {print("\(nums[item])")}, label: {
                        Text(nums[item])
                            .font(.largeTitle)
                            .frame(width: 70, height: 70)
                            .foregroundColor(.black)
                            .background(Color.gray.opacity(0.5))
                            .cornerRadius(40)
                    })
                }
            }
            HStack(spacing: 20){
                ForEach(3..<6) { item in
                    Button(action: {print("\(nums[item])")}, label: {
                        Text(nums[item])
                            .font(.largeTitle)
                            .frame(width: 70, height: 70)
                            .foregroundColor(.black)
                            .background(Color.gray.opacity(0.5))
                            .cornerRadius(40)
                    })
                }
            }
            HStack(spacing: 20){
                ForEach(6..<9) { item in
                    Button(action: {print("\(nums[item])")}, label: {
                        Text(nums[item])
                            .font(.largeTitle)
                            .frame(width: 70, height: 70)
                            .foregroundColor(.black)
                            .background(Color.gray.opacity(0.5))
                            .cornerRadius(40)
                    })
                }
            }
            HStack(spacing: 20){
                ForEach(9..<12) { item in
                    Button(action: {print("\(nums[item])")}, label: {
                        Text(nums[item])
                            .font(.largeTitle)
                            .frame(width: 70, height: 70)
                            .foregroundColor(.black)
                            .background(Color.gray.opacity(0.5))
                            .cornerRadius(40)
                    })
                }
            }
            Image(systemName: "phone.circle.fill")
                .resizable()
                .frame(width: 68, height: 68)
        }
    }
}

struct MessagesView: View{
    @State private var messageText: String = ""
    @State private var messages: [(sender: String, message: String)] = [
        ("User1", "Hello!"),
        ("User2", "Hi there!"),
        ("User1", "How's it going?"),
        ("User2", "Pretty good, thanks!"),
        ("User2", "What do you want for dinner?")
    ]
    
    var body: some View {
        VStack {
            HStack{
                Image("P1")
                    .resizable()
                    .frame(width: 40, height: 40)
                Text("Peter")
                    .font(.title)
                    .offset(x:-10)
            }
            .background(Color.gray)
            .cornerRadius(10)
            .padding(.all, 20)
            List(messages, id: \.message) { message in
                if message.sender == "User1" {
                    HStack {
                        Spacer()
                        Text(message.message)
                            .padding(10)
                            .background(Color.blue)
                            .foregroundColor(.white)
                            .cornerRadius(10)
                    }
                    .listRowSeparator(.hidden)
                } else {
                    HStack {
                        Text(message.message)
                            .padding(10)
                            .background(Color.gray.opacity(0.2))
                            .cornerRadius(10)
                            .listRowSeparator(.hidden)
                        Spacer()
                    }
                    .listRowSeparator(.hidden)
                }
            }
            .listStyle(.plain)
            // Input Area
            HStack {
                TextField("Type your message...", text: $messageText)
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                    .padding(.horizontal)
                
                Button(action: sendMessage) {
                    Text("Send")
                }
                .padding(.trailing)
            }
            .offset(y:-30)
        }
        
    }
    
    func sendMessage() {
        if !messageText.isEmpty {
            messages.append(("User1", messageText))
            messageText = ""
        }
    }
}

    
```

<h1>
    <a href="https://yzu365-my.sharepoint.com/:v:/g/personal/s1103525_mail_yzu_edu_tw/EU2w-odbhoxAn63hLvZ5YagBVyyWXt4TBVc_p8ro3PuvSQ?e=N8Ddie">Video Link</a>
</h1>
