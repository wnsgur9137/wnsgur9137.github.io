---
layout: post
title: (swift) BASIC_09. DispatchSourceTimer, UIView Animation
description: "(swift) 타이머, 애니메이션"
tags: [swift, basic, 공부]
comments: true
---

> # [swift] BASIC_09. DispatchSourceTimer, UIView Animation

<br>

# DispatchSourceTimer

특정 시간이 지난 뒤 이벤트를 발생시킨다거나, 반복적인 주기로 특정 작업을 수행하는 등의 행위를 할 때 사용  

swift에서 timer class를 이용하여 타이머를 구현할 수 있지만, [pomodoroTimer](https://github.com/wnsgur9137/Swift_basic_projects/tree/master/pomodoroTimer)에서는 DispatchSourceTimer를 이용하여 구현하였다.  

``` swift
var timer: DispatchSourceTimer?

func startTimer() {
    if self.timer == nil {
        self.timer = DispatchSource.makeTimerSource(flags: [], queue: .main) // UI를 수정해야 하므로 .main(ios에서 오직 한 개만 존재하는 스레드)
        self.timer?.schedule(deadline: .now(), repeating: 1)
        self.timer?.setEventHandler(handler: { [ weak self] in
        guard let self = self else { return } // strong reference
        self.currentSeconds -= 1
        
        let hour = self.currentSeconds / 3600
        let minutes = (self.currentSeconds % 3600) / 60
        let seconds = (self.currentSeconds % 3600) % 3600
        self.lblTimer.text = String(format: "%02d:%02d:%02d", hour, minutes, seconds)

        self.progressView.progress = Float(self.currentSecnods) / Float(self.duration)

        if self.currentSeconds <= 0 {
            self.stopTimer()
            AudioServicesPlaySystemSound(1005)
        }
        })
    }
}

func stopTimer() {
    // 일시정지 상태에서 timer에 nil을 대입하면 에러가 난다. 그렇기에 resume() 메서드를 사용해야 한다.
    if self.timerStatus == .pause {
        self.timer?.resum()
    }
    self.timerStatus = .end
    self.timer?.cancel()
    self.timer = nil    // 타이머를 종료할 때 nil을 사용하여 해제시켜야 메모리를 소모하지 않는다.
}

@IBAction func tapStart(_ sender: UIButton) {
        self.duration = Int(self.datePicker.countDownDuration) // 2분 -> 120초와 같이 저장해줌.
//        debugPrint(self.duration)
        
        switch self.timerStatus {
        case .end:
            self.currentSeconds = self.duration
            self.timerStatus = .start
            self.startTimer()
        case .start:
            self.timerStatus = .pause
            self.timer?.suspend()   // 타이머 일시정지
        case .pause:
            self.timerStatus = .start
            self.timer?.resume()
        }
    }
```

<br>
<br>
<br>

# UIView Animation

UIView 클래스는 Animation에서 사용되는 api를 타입 메서드로 제공하고, 이 메서드를 활용하여 비교적 단순한 코드로 애니메이션을 구현하였다.  
[pomodoroTimer](https://github.com/wnsgur9137/Swift_basic_projects/tree/master/pomodoroTimer)에서 버튼을 hidden으로 구현하지 않고, alpha 값으로 구현하여 자연스럽게 구현하였다.  
또한, 타이머가 진행될 때 imageView를 회전시키는 애니메이션을 구현하였다.  

``` swift
enum TimerStatus {
    case start
    case pause
    case end
}

class ViewController: UIViewController {
    func setTimerInfoViewVisible(isHidden: Bool) {
        if isHidden {
            UIView.animate(withDuration: 0.5, animations: {
                self.lblTimer.alpha = 0
                self.progressView.alpha = 0
                self.datePicker.alpha = 1
                self.imgPomodoro.transform = .identity
            })
        } else {
            UIView.animate(withDuration: 0.5, animations: {
                self.lblTimer.alpha = 1
                self.progressView.alpha = 1
                self.datePicker.alpha = 0
            })
        }

        // hidden 사용
//        self.lblTimer.isHidden = isHidden
//        self.progressView.isHidden = isHidden
        
        self.btnStart.isSelected = !isHidden
        self.btnCancel.isEnabled = !isHidden
        self.datePicker.isHidden = !isHidden
    }

    @IBAction func tapStart(_ sender: UIButton) {
        self.duration = Int(self.datePicker.countDownDuration) // 2분 -> 120초와 같이 저장해줌.
//        debugPrint(self.duration)
        
        switch self.timerStatus {
        case .end:
            self.currentSeconds = self.duration
            self.timerStatus = .start
            self.setTimerInfoViewVisible(isHidden: false)
            self.startTimer()
        case .start:
            self.timerStatus = .pause
            self.btnStart.isSelected = false
            self.timer?.suspend()   // 타이머 일시정지
        case .pause:
            self.timerStatus = .start
            self.btnStart.isSelected = true
            self.timer?.resume()
        }
    }
}
```