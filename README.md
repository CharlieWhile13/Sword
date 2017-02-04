# Sword - A Discord Library for Swift

[![Build Status](https://travis-ci.org/Azoy/Sword.svg?branch=master)](https://travis-ci.org/Azoy/Sword)

# Requirements
1. macOS or Linux (Foundation for Linux stability is not trustworthy, so use with caution)
2. Swift 3.0
3. An internet connection

# Adding Sword
In order to add Sword as a dependency, you must first create a Swift executable in a designated folder, like so `swift package init --type executable`. Then in the newly created Package.swift, open it and add Sword as a dependency

```swift
import PackageDescription

let package = Package(
    name: "yourswiftexecutablehere",
    dependencies: [
        .Package(url: "https://github.com/Azoy/Sword", majorVersion: 0, minor: 3)
    ]
)
```

After that, open Sources/main.swift and remove everything and replace it with the example below.

```swift
import Sword

let bot = Sword(token: "Your bot token here")

bot.on(.ready) { _ in
  bot.editStatus(playing: ["name": "with Swords!"])
}

bot.on(.messageCreate) { data in
  let msg = data[0] as! Message
  if msg.content == "!ping" {
    msg.reply(with: "Pong!")
  }
}

bot.connect()
```

# Links
http://sword.azoy.gg - Docs (created with https://github.com/Realm/Jazzy)
