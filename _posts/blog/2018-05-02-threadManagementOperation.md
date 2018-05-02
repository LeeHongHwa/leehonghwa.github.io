---
layout: post
title: "Thread Management(1-2)"
modified:
categories: blog
excerpt:
tags: [Documentation, Foundation, Task Management, Operation]
image:
  feature:
date: 2018-05-02T09:00:00+09:00
---
**왜 나는 GCD를 썼을까?(Operation)**

----

### iOS에서 Thread 관리하기 1-2 (NSOperation)

이번 블로그는 [NSOperation(Operation)][Operation]과 [NSOperationQueue(OperationQueue)][OperationQueue]의 문서를 보도록 하겠습니다.

예전에 원본을 번역해야지 하는 생각으로 글을 쓰다가 저도 무슨 말인지 모르는데 그냥 해석해놓은 느낌으로 쓴 적이 있습니다. 
그런 글 쓰는방식이 좋지 않은 것 같아 이번에는 번역한 것이 아니라 이해한 대로 설명드릴 거라 아마 틀릴 수도 있습니다. 

혹시나 틀린 점 있으면 꼭 알려주시면 감사하겠습니다.

---

#### Operation

 작업 하나를 나타내는 추상 클래스(추상 클래스라 하면 '공통된 기능을 가진 놈이다.' 라고 생각하면 편하다)

##### 개요
추상 클래스이기 때문에 직접 사용하지 말고 상속받아서 사용해라. 또는 기본으로 제공되는 BlockOperation을 사용해도 좋다.<br>
추상 클래스에는 기본적인 구현이 다 되어있기 때문에 사용자들은 본인이 필요한 로직만 작성하면 된다.<br>
operation 한번만 실행 가능하며, 일반적으로는 OperationQueue에 추가하면 OperationQueue는 직접 thread에서 operation을 실행시키거나 dispatch GCD라고 알려진 libdispatch library를 사용해서 operation을 실행시킨다.<br>
start() 메서드를 사용해서 operation을 직접 사용할 수 있지만 작업이 준비되지 않은 상태에서 실행 시키면 exception을 발생시키므로 추가적인 코드를 사용해야한다.(isReady 프로퍼티 사용)

##### Operation Dependencies (Dependencies란 말그대로 의존적, B작업을 하려면 A가 있어야해)
addDependency(_:) 메서드를 사용해서 B의 작업이 끝날때 A작업을 실행해줘 라고 할 수 있다.<br>
removeDependency(_:)를 사용하면 지울수 있다.<br>
A의 작업이 A-1, A-2, A-3 있다면 A-3이 끝나면 B는 준비상태가 된다.<br>
A의 작업이 완료가 되면은 B가 시작될 텐데 A의 작업이 끝났다는 게 성공적으로 끝난 건지 실패로 끝났는지 모르므로 추가적인 작업을 해줘야 한다.

##### KVO-Compliant Properties
아래는 operation 클래스에서 KVC와 KVO를 준수하는 프로퍼티 목록이다. 상속해서 프로퍼티를 추가하는 경우에는 KVC와 KVO를 준수하면 좋다. 

    isCancelled - read-only: 취소 요청이 들어왔냐?
    isAsynchronous - read-only: operation이 concurrently하냐?
    isExecuting - read-only: operation 실행 중이냐?
    isFinished - read-only: operation 성공이거나 취소되거나 끝난 상태
    isReady - read-only: operation 할 꺼니?
    dependencies - read-only
    queuePriority - readable and writable: QOS
    completionBlock - readable and writable

KVO의 알림이 어느 thread에서 실행될지 몰라 cocoa binding(view와 관련된 행위라 main thread에서만 실행되어야 하므로)은 피해야 한다. 그렇지만 cocoa binding은 UIKit에서는 지원하지 않는 것으로 알고 있다.(아니라면 알려주세요) 따라서 신경쓸 필요가 없다.<br>
<sub>Important: Cocoa bindings is available to Cocoa Objective-C applications running OS X version 10.3 and later<sub>

##### Multicore Considerations
hread는 stack만이 독립된 자원이기 때문에 다른 메모리에 있는 자원들을 공유할 때 안전해야 한다. operation 클래스에서는 멀티 코어까지 고려해서 안전하게 메서드를 호출할 수 있다. 그렇지만 operation 클래스를 상속받고 메서드를 재정의 하면 내가 알아서 thread-safe 하게 동기적으로 처리해야 한다.

##### Asynchronous VS Synchronous Operations
queue에 넣지 않고 수동으로 시작하는 경우는 기본으로는 별도의 thread를 만들지 않고 현재 thread에서 동기적으로 실행된다. 반면 비동기 작업을 하려면 별도의 thread에서 비동기 메서드로 작업을 해야 한다.

queue에 넣고 동기로 일을 처리하면 operation 하나당 하나의 thread에서 작업을 한다 따라서 상태를 추적하는 것이 쉽지만 수동으로 비동기 작업을 한다고 한다면 (하나의 operation을 multi thread로 작업을 처리할 경우) 내가 알아서 KVO를 사용해서 모니터링하고 상태의 변경사항을 보는 코드가 생겨야 한다. 상황에 맞게 해야 하지만 queue에 넣고 쓰는 걸 추천한다. 쓰게 된다면 각 operation마다 각각 thread를 만들어 순차적으로 실행되고 각각 operaion(각기 다른 thread) 들은 operation queue의 maxConcurrentOperationCount 프로퍼티에 따라 concurrent 하게 작동이 된다.

operation queue에 operation을 추가한다면 operation의 isAsynchronous의 프로퍼티값이 무엇이든지 single thread에서 작업이 된다. 즉 multi thread로 할  생각 이여도 무시된다.

---

##### Subclassing Notes
concurrently or non-concurrently 둘 중 뭘로 할건가에 따라서 달라진다.

###### Methods to Override

###### non-concurrently
일반적으로 main() 메서드만 재정의 하면된다.
main()
이 메서드 안에서 작업을 실행하면 된다. 그리고 만약에 data의 setter랑 getter를 custom 하게 만든다면 thread-safe하게 만들어야한다.

###### concurrently
많은 메서드를 재정의 해야 한다. 아래 최소한 이건 재정의 해야 한다고 쓰여있는 목록이다.

start()
isAsynchronous
isExecuting
isFinished

start()에서 비동기 방식으로 작업을 하고 isExecuting 프로퍼티도 thread-safe 하게 설정하고 적절하게 KVO 알림을 보내야 한다.

작업 완료 또는 취소 시에 isExecuting 및 isFinished 프로퍼티의 값을 thread-safe 하게 설정하고 적절하게 KVO 알림을 보내야 한다.
취소된 경우도 isFinished를 true로 해야 한다는 것을 잊지 말자.

    중요한 점
    start()에서 super를 호출해야 한다. operation을 시작하기 전에 operation이 isCancelled 상태이면 중단해야 한다.

위에 내용만 override 하면 거의 되지만 dependency를 custom 하게 하려면 isReady의 KVO 알림을 적절하게 제공해야 한다. 그 뒤에는 Operation 클래스에 이미 정의된 되로 작업이 될 것이다.

---

##### Maintaining Operation Object States
내부적으로 현재 작업 상태를 외부에게 알려주는데 올바르게 알려줘야한다.

###### isReady
작업을 실행할 상태이면 true, 아니면 false를 반환한다.

###### isExecuting
operation이 진행중이라면 true 아니면 false를 반환하고 concurrently한 operation을 구현한다면 다른 프로퍼티로 교체하고 KVO 설정도 해줘야한다.

###### isFinished
operation이 취소되거나 완료된다면 true 그렇지 않다면 false를 반환한다.
true를 반환할때 까지 operation queue는 대기하고 있고, dependency로 등록 되있는 operation도 기다리므로 start()메서드를 사용해서 concurrently 하게 작업을 하는경우 isFinished상태에 대한 적절한 KVO 알림을 해줘야 한다.

###### isCancelled
작업 취소 요청이 들어왔으면 ture 아니면 false를 반환한다. 언제 어디서 취소 요청이 들어올지 모르므로 긴 시간이 걸리는 작업 앞뒤에 isCancelled 프로퍼티를 자주 사용해서 취소됐다면 return 시켜 줘야 한다.

---

##### Responding to the Cancel Command
operation queue에 넣은 operation 을 취소 요청을 하려면 cancel() 메서드를 사용하면 되고cancelAllOperations()를 하면 전체 취소 요청을 할 수 있다. 말 그대로 취소 요청이지 즉시 중단된다는 것은 아니다. operation에서 이 상태 값을 보고 return을 시켜줬다면 취소가 잘 됐을 것이다. operation이 operation queue에 등록되기 전에 cancel이 된다면 기본적으로 operation은 return 시킨다. (queue에 추가되거나 start 하기 전에 isCancelled를 확인한다는 뜻이다.)

---

#### Operation Queue

 operation 관리자

##### 개요
우선순위와 준비 상태에 따라 실행되며 isFinished 상태가 true 이면 operation은 queue에 제거되고 직접 제거할 수는 없다.

    중요한 점
    Suspending 상태 이면 finished 상태가 아니므로 memory leak이 날 수 있다.

##### Determining Execution Order
operation의 의존성과, 우선순위, 태에 따라 실행되며, 우선순위가 같고 상태가 isReady == true 이면 queue에 등록된 순서대로 실행된다.

##### Canceling Operations
cancel() 메서드는 취소 요청을 하는 거지 바로 취소를 한 것은 아니다.<br>
operation에서 작업을 할 때 isCancelled 메서드를 자주 확인하며 그에 따른 처리를 해야 한다.<br>
operation queue에 등록되었지만 실행되지 않은 operation은 내부에서 start() 메서드를 호출할 때 기본 구현으로 이를 체크할 것이므로 괜찮다.

    중요한 점
    dependency때문에 기다리고 있는 operation을 취소하면 dependency를 무시하고 가능한 빨리 start() 메서드를 실행시켜 완료 상태로 변경해 준다.

##### KVO-Compliant Properties
OperationQueue 클래스는 KVC, KVO를 준수한다.

    operations - read-only
    operationCount - read-only
    maxConcurrentOperationCount - readable and writable
    isSuspended - readable and writable
    name - readable and writable

##### Thread Safety
multi thread(operation 하나당 thread 하나)에서 사용하는 것이 객체에 대한 접근을 동기화할 수 있어서 안전하다.
Dispatch framework를 사용하여 queue에 들어있는 작업들을 시작한다.

---

제 마음대로 사용해 보겠습니다.

``` swift
class OperationViewController: UIViewController {
    
    let imageOperationQueue = ImageOperationQueue()
    
    let taskNumber = ["1", "2", "3", "4", "5", "6", "7", "8"]
    let taskString = ["a", "b", "c", "d", "e", "f", "g", "h"]
    
    let imageDataArray: [ImageData] = {
        var _imageDataArray = [ImageData]()
        for _ in 0..<10 {
            _imageDataArray.append(ImageData(state: .new, url: URL(string: "http://leehonghwa.github.io/")!))
        }
        return _imageDataArray
    }()
    
    @IBAction func didTapOperationTriggerButton(_ sender: UIButton) {
        /*
            add operation 할 때마다 thread를 만들어 준다.
            operation이 끝나면 thread를 없애준다.
         */
        
        //************************
        //***** 내 마음대로 예제 ******
        //************************
        
        /*
         closure
        operationQueue.addOperation {
            for numberString in self.taskNumber {
                print("\(Thread.current): \(numberString)")
            }
        }
        operationQueue.addOperation {
            for string in self.taskString {
                print("\(Thread.current): \(string)")
            }
        }
         */
        
        /*
        Operation subClass
        operationQueue.addOperation(CustomOperation(taskElement: taskNumber))
        operationQueue.addOperation(CustomOperation(taskElement: taskString))
         */
        
        /*
         Start
         현재 메서드를 호출하는 thread에서 실행됨
         CustomOperation(taskElement: taskNumber).start()
         */
        
        //**********************
        //***** 실용적인 예제 ******
        //***********************
        
        //다운로드
        imageDataArray.enumerated().forEach { (offset, imageData) in
            let operation = ImageOperation(imageData: imageData)
            //dependency 추가
            ResizeImageOperation().addDependency(operation)
            imageOperationQueue.downloadImage(id: offset, operation: operation)
        }
        //취소
        imageOperationQueue.cancelDownloadImage(id: 1)
        
    }
}

class CustomOperation: Operation {
    let taskElement: [String]
    init(taskElement: [String]) {
        self.taskElement = taskElement
    }
    
    override func main() {
        guard !isCancelled else { return }
        task()
    }
    
    func task() {
        for element in self.taskElement {
            print("\(Thread.current): \(element)")
        }
        //cancel을 한다고 현재 진행중인 메서드가 끝나는것은 아니므로 이렇게 상태값을 확인한뒤 return 시켜줘야한다.
        guard !isCancelled else { return }
    }
}

// MARK: - Image
class ImageData {
    enum State {
        case new
        case downloading
        case downloaded
    }
    
    var state: State
    let url: URL
    var image: UIImage?
    
    init(state: State, url: URL, image: UIImage? = nil) {
        self.state = state
        self.url = url
        self.image = image
    }
}

//이런식으로도 사용할 수 있을것 같아요
class ImageOperation: Operation {
    let imageData: ImageData
    
    init(imageData: ImageData) {
        self.imageData = imageData
    }
    
    override func main() {
        if imageData.state == .new {
            //시작하기전 검사
            guard !isCancelled else { return }
            imageData.state = .downloading
            imageData.image = ImageService.downloadImage(url: imageData.url)
            //오래걸리는 작업 후 검사
            guard !isCancelled else { return }
            imageData.state = .downloaded
        }
    }
}

class ImageOperationQueue {
    private var currentOperation = [Int: ImageOperation]()
    
    let operationQueue: OperationQueue = {
        var queue = OperationQueue()
        queue.name = "operation-queue"
        //한번에 몇개 실행할건가?
        queue.maxConcurrentOperationCount = 1
        return queue
    }()
    
    func cancelDownloadImage(id: Int) {
        guard let operation = currentOperation[id], operation.imageData.state != .downloaded else { return }
        currentOperation.removeValue(forKey: id)
        operation.cancel()
    }
    
    func downloadImage(id: Int, operation: ImageOperation) {
        if currentOperation[id] == nil {
            currentOperation[id] = operation
        }
        operation.completionBlock = { [weak self] in
            self?.currentOperation.removeValue(forKey: id)
        }
        operationQueue.addOperation(operation)
    }
}
```

##### 느낀점
	1. 취소가 쉽다.
	2. 의존성이 있는 작업을 할 때 좋을것 같다.
	3. KVO를 제공해 상태를 알기 쉽다.
	4. suspend하기 좋다.
	5. operation을 상속하고 그안에서 작업을 하기 때문에 캡슐화 하기좋다.
    6. thread를 작업단위로 만들어서 오버헤드가 클 것같다.
    7. thread-safe 하다.

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>


[Operation]: https://developer.apple.com/documentation/foundation/operation
[OperationQueue]: https://developer.apple.com/documentation/foundation/operationqueue