---
layout: post
title: "Thread Management-1"
modified:
categories: blog
excerpt:
tags: [Documentation, Foundation, Processes and Threads, Thread]
image:
  feature:
date: 2018-04-30T08:50:00+09:00
---
**왜 나는 GCD를 썼을까?**

----

### iOS에서 Thread 관리하기-1(NSThread)

비동기 작업을 해야지 하면 습관적으로

``` swift
DispatchQueue.global().async {
    //내용
}
```

이런식으로 사용을 했었는데 다른 방식으로도 비동기 작업을 할 수 있는데 왜 이걸 사용했을까? 라고 물어보면 대답할 수 없었습니다.
이유도 모르고 쓴다는게 부끄러워서 이렇게 정리를 해보기로 했습니다.

<sub>

1. 우선 공부를 Apple 공식 문서 API([NSThread(Thread)][Thread], [NSOperation(Operation)][Operation], [Dispatch][Dispatch])를 읽고
2. [Concurrency Programming Guide][Programming] 를 읽고
3. [Thread 관리의 장단점을 비교한 블로그][Blog]를 보고 이해 하는 순으로 글을 작성하겠습니다.

<br>
이번 블로그는 NSThread(Thread)의 문서를 보도록 하겠습니다.

---

#### Thread

 thread 실행

##### 개요
Objective-C 메서드를 다른 thread에서 실행하려는 경우 이 클래스를 사용해라. thread는 파일 읽어오기, 통신 등 비교적 느린 작업과 빠르게 처리해야 하는 작업을 동시에 처리하게 만들어 준다. 예를 들어 오래 걸리는 작업을 UI를 처리하는 main thread에서 실행시키지 않고 다른 thread에서 처리하게 만들어 UI가 굳지 않게 만들 수 있다. 그리고 큰 작업을 작은 작업 단위로 나눠서 멀티 코어의 이점을 잘 이용할 수 있다.

thread 클래스는 thread의 런타임 조건을 감시하는 기능을 가진 operation class와 비슷한 기능을 지원한다. operation과 비슷한 기능을 사용하여 thread의 실행을 취소하거나 thread가 아직 실행 중이거나 해당 작업을 완료했는지 확인할 수 있다. thread를 취소하려면 cancel 메서드를 사용해라.

<sub>**상속받을 때 주의할 점** <br>
thread를 상속받을 때 main 메서드를 재정의 하면 진입점(entry point)을 지정할 수 있으며 재정의하는 main 메서드에서 부모의 메서드를 호출하지 않아도 된다.(super.main())</sub>

---

#### Start

thread를 시작합니다.

##### 개요
비동기 적으로 thread를 생성하고 thread의 main() 메서드를 호출한다. isExecuting 프로퍼티는 thread가 실행을 시작하면 true를 반환한다.

만약에 target과 selector를 가지고 thread의 instance를 초기화한 경우에 기본 main() 메서드는 selector를 자동으로 호출한다.

thread가 처음으로 application에 분리된 thread라면 이 메서드는 NSWillBecomeMultiThreaded 이름으로 notification center에 post 한다.

---

#### Exit
현재의 thread를 종료한다.

##### 개요
current라는 클래스 메서드를 사용해 현재 thread에 접근한다. thread를 종료하기 전에NSThreadWillExit 이름으로 notification center에 post 한다. notification은 동기적으로 전달되므로 NSThreadWillExit의 모든 관찰자는 thread가 종료되기 전에 notification을 수신할 수 있다.

이 메서드를 호출하면 실행 중에 할당된 모든 리소스를 thread가 정리할 기회가 없으므로 이 메서드를 호출하면 안 된다.

---

#### Cancel
thread의 상태를 변경해서 종료되야 한다고 나타낸다.

Operation에 사용된 것과 동일한 의미를 가진다. thread의 상태를 변경하고 isCancelled 프로퍼티에 반영한다. 취소를 지원하는 thread는 주기적으로 isCancelled 메서드를 호출하여 thread가 실제로 취소되었는지 판별하고 종료된 경우 종료해야 한다.

---

이어서 사용법을 보겠습니다.(제가 궁금해서....)

``` swift
class ViewController: UIViewController {

    var nsLimitCount: Int = 0
    var detachLimitCount: Int = 0
    
    lazy var nsThread: Thread = {
        let thread = Thread(target: self, selector: #selector(task), object: nil)
        thread.name = "com.apple.ns-thread"//queue 이름이 아니라 thread의 이름이다.
        return thread
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        NotificationCenter.default.addObserver(self, selector: #selector(exit), name: .NSThreadWillExit, object: nil)
    }
    
    @objc func task() {
        if Thread.current == nsThread {
            print("Init NSThread Task")
            
            nsLimitCount += 1
            if nsLimitCount == 3 {
                Thread.exit()
                /*
                 현재 실행중인 스레드 즉각 취소
                 아 궁금해서 현재 스레드가 main thread 일 때 취소하면 취소될까 하고 해봤는데 취소가 됩니다. 재미있네요
                 참고로 문서에는 이 메서드를 사용하지 말라고하네요. 그 문서 번역본도 올려놨습니다.
                 */

                nsThread.cancel()
                /*
                 취소 상태로 변경해 준다.
                 nsThread.isCancelled로 상태를 보고 종료되기전에 처리해야하는 것들을 정리하고 현재 메서드를 종료 시켜줘서 exit를 시켜줘야한다. 아니면 계속 해서 task()를 호출하게 될것이다.
                 */
            }
            
            task()// -> guard !nsThread.isCancelled else { return }
            
        } else {
            print("Detach New Thread Task")
            detachLimitCount += 1
            if detachLimitCount < 3 {
                task()
            }
        }
    }
    
    @objc func exit() {
        //thread가 사라지기전에 사라질 thread에서 호출
        if Thread.current == nsThread {
            print("Init NSThread Exit")
        } else {
            print("Detach New Thread Exit")
        }
    }
    
    @IBAction func didTapNSThreadTriggerButton(_ sender: UIButton) {
        sender.isSelected = !sender.isSelected
        Thread.detachNewThreadSelector(#selector(task), toTarget: self, with: nil)
        if sender.isSelected {
            if !nsThread.isCancelled {
                nsThread.start()
            }
        } else {
            nsThread.cancel()
        }
    }
}
```

##### 느낀점
	1. 해당 selector의 메서드가 끝나면 thread가 종료가 된다는게(다시 만들어야 한다는게) 오버헤드가 클 것 같다.
	2. 취소가 쉽다.
	3. serial, concurrent queue 같이 해당 thread가 어떻게 처리할지 설정할 수 있는지 모르겠다.
	4. task를 sync인지 async인지 설정할 수 있는지 모르겠다.
	5. 그냥 비동기를 해보고싶다 하면 할 수 있을것 같지만 안하는게 좋을것 같다. 맨 마지막에 비교하는 블로그를 쓸 때 찾아보고 자세히 쓰겠습니다.

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Thread]: https://developer.apple.com/documentation/foundation/thread
[Operation]: https://developer.apple.com/documentation/foundation/operation
[Dispatch]: https://developer.apple.com/documentation/dispatch
[Programming]: https://developer.apple.com/library/content/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008091-CH1-SW1
[Blog]: https://cocoacasts.com/choosing-between-nsoperation-and-grand-central-dispatch/
