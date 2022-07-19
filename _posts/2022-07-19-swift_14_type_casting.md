---
layout: post
title: (swift) 14. Type casting (타입 캐스팅)
description: "(swift) 타입 캐스팅"
tags: [swift, 공부]
comments: true
---

> # [swift] 14. Type casting (타입 캐스팅)

<br>

타입캐스팅이란 인스턴스의 타입을 확인하거나 어떠한 클래스의 인스턴스를 해당 클래스 계층 구조의 슈퍼 클래스나 서브 클래스로 취급 하는 방법을 말한다.  

swift에서는 타입 캐스팅을 **is**, **as**로 구현할 수 있다.

<br>
<br>
<br>

# 예제

``` swift
class MediaItem {
    var name: String
    init(name: String) {
        self.name = name
    }
}

class Movie: MediaItem {
    var director: String
    init(name: String, director: String) {
        self.director = director
        super.init(name: name)
    }
}

class Song: MediaItem {
    var artist: String
    init(name: String, artist: String) {
        self.artist = artist
        super.init(name: name)
    }
}

let library = [ // library는 타입 추론에 의해 MediaItem 타입의 배열이다.
    Movie(name: "기생충", director: "봉준호")
    Song(name: "Lemon Tree", artist: "Post Malone")
    Movie(name: "올드보이", director: "박찬욱")
    Song(name: "Ballin", artist: "Parisalexa")
    Song(name: "Peter Pan Was Right", artist: "Anson Seabra")
]

var movieCount = 0
var songCount = 0

for item in library {
    if item is Movie {
        movieCount += 1
    } else if item is Song {
        songCount += 1
    }
}

print("Media library contains \(movieCount) movies and \(songCount) songs")

for item in library {   // library 배열의 모든 항목
    if let movie = item as? Movie { // as?는 옵셔널 값을 반환한다.
        print("Movie: \(movie.name), dir. \(movie.director)")
    } else if let song = item as? Song {
        print("Song: \(song.name), by \(song.artist)")
    }
}
```

출력 결과  
```
Media library contains 2 movies and 3 songs
Movie: 기생충, dir. 봉준호
Song: Lemon Tree, by Post Malone
Movie: 올드보이, dir. 박찬욱
Song: Ballin, by Parisalexa
Song: Peter Pan Was Right, by Anson Seabra
```