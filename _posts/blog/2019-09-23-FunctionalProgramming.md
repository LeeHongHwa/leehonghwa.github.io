---
layout: post
title: "FUNCTIONAL PROGRAMMING"
modified:
categories: blog
excerpt:
tags: [Functional Programming]
image:
feature:
date: 2018-05-22T12:00:00+09:00

---

**함수형 프로그래밍**

---

### 3가지로 구분된 프로그래밍 패러다임
 1. 저사양 컴퓨터 -> 최적화가 필요 -> 중복된 코드 제거, 메모리 재사용
 2. 컴퓨터 보급화 -> 많은 소프트 웨어 생산 -> 코드의 재사용 필요 -> OOP
 3. 고성능 컴퓨터(다수의 CPU(다수의 Core를 가진 CPU)) -> 병렬 처리(동시성) -> FP(외부에서 값을 변경하는 것을 제거하고 새로운 값을 만들자)

### FP의 오해
 1. map, reduce, higher order fuction, immutable data 이런 건 프로그래밍 기법이지 FP가 아니다.
 2. FP의 가장 큰 특징은 side effect를 없이 코드를 작성하는 것이다.

### 순수함수(Pure Function)
 - 함수형 프로그램은 함수의 조합으로 프로그래밍 하는데, 여기서 말하는 함수는 기존 함수 또는 메서드와 구분 하기 위해 순수함수라고 말한다.
 -  이 순수함수는 '특정 input에 대해서 항상 동일한 output을 반환하는 함수'를 의미한다.

```swift
var sum = 0
func 순수함수_만들기(_ nums: [Int]) -> Int {
    for i in nums {
        sum += i
    }
    return sum
}

func 순수함수_만들기_결과(_ nums: [Int]) -> Int {
    return nums.reduce(0, +)
}

//질문:
func 이건_순수힘수_일까(_ num: Int) -> Int {
    return Int.random(in: 0...100) % num
}

//답: No
```

### 고차함수(higher-order function)
- 함수를 파라미터로 받거나 함수를 리턴하는 함수를 고차함수 라고 한다.

### Composition
- 함수의 반환값이 다른 함수의 입력값으로 사용되는 것을 함수의 합성. 함수의 조합을 도와줌

```swift
func compose<A, B, C>(_ 합성_요소_1: @escaping (A) -> B, _ 합성_요소_2: @escaping (B) -> C) -> (A) -> C {
    return {
        return 합성_요소_2(합성_요소_1($0))
    }
}

func 짝수(_ A: [Int]) -> [Int] {
    return A.filter { $0 % 2 == 0 }
}

func 더하기(_ B: [Int]) -> Int {
    return B.reduce(0, +)
}

print("[filter even + sum] = \(compose(짝수, 더하기)([1, 2, 3, 4]))")
```

### Currying
-   여러개의 파라미터를 받는 함수를 하나의 파라미터를 받는 여러 개의 함수로 쪼개는 것 == 다항으로 이루어진 함수를 단항으로 실행 시킬 수 있는 함수.
-   결국 함수의 합성을 원활하게 하기 위해서 커링을 사용하는 것. OOP는 객체의 상호작용이라 하면 FP는 함수의 조합 이라고 생각한다.

```swift
func curry<A, B, C>(실행될_함수: @escaping (A, B) -> C) -> (A) -> (B) -> C {
    return { (a: A) -> (B) -> C in
        { (b: B) -> C in
            return 실행될_함수(a, b)
        }
    }
}

func 배수(_ 추가된_파라미터: Int, _ A: [Int]) -> [Int] {
    return A.filter { $0 % 추가된_파라미터 == 0 }
}

//질문: compose(배수, 더하기) 이렇게 합성 하고 싶으면?

//답:
print("[(filter_다른_파라미터 > curry) + sum] = \(compose(curry(실행될_함수: 배수)(5), 더하기)([1, 5, 10]))")
```

### Memoization
- 순수 함수를 유지하면서 기존 사용했던 연산을 캐시 하여 동일한 연산을 하지 않아도 되게끔 하는 기법.

**[기존]**

```swift
enum 뷰_타입: Hashable {
    case feed
    case posting
    case discovery
}

extension String {
    var height: CGFloat { return CGFloat(count) }
}

struct 모델 {
    let feedText: String
    let postingText: String
    let discoveryText: String
}

class 유동적인_높이를_가진_뷰_일반 {
    private var heights: [뷰_타입: CGFloat] = [:]
    
    func setupHeights(with model: 모델) {
        heights[.feed] = model.feedText.height
        heights[.posting] = model.postingText.height
        heights[.discovery] = model.discoveryText.height
    }
    
    func heights(with type: 뷰_타입) -> CGFloat {
        return heights[type] ?? 0
    }
}
```

**[메모이제이션]**

```swift
class 유동적인_높이를_가진_뷰_메모이제이션 {
    typealias HeightCacheType = [뷰_타입: CGFloat]
    
    enum CallType {
        case setup(모델)
        case get(뷰_타입)
    }
    
    static private func memoizeHeightsProcessing(with initHeights: HeightCacheType) -> (CallType) -> CGFloat? {
        var heights = initHeights
        return { callType in
            switch callType {
            case let .setup(model):
                heights[.feed] = model.feedText.height
                heights[.posting] = model.postingText.height
                heights[.discovery] = model.discoveryText.height
                return nil
            case let .get(viewType) :
                return heights[viewType]
            }
        }
    }
    
    let processHeights = 유동적인_높이를_가진_뷰_메모이제이션.memoizeHeightsProcessing(with: [:])
    
    func setupHeights(with model: 모델) {
        _ = processHeights(.setup(model))
    }
    
    func heights(with type: 뷰_타입) -> CGFloat {
        return processHeights(.get(type)) ?? 0
    }
}
```
### Iterable
-   순회 가능한 값
-   **IteratorProtocol:**  next라는 함수를 가지고 있는 프로토콜    
-   **Sequence:** next가 nil이 될 때 까지 for in을 할 수 있는 프로토콜

```swift
struct 거꾸로_실행되는_모델_Sequence: Sequence {
    let elements: [Int]
    
    func makeIterator() -> 거꾸로_실행되는_모델_Iterator {
        return 거꾸로_실행되는_모델_Iterator(sequence: self)
    }
}

struct 거꾸로_실행되는_모델_Iterator: IteratorProtocol {
    private let sequence: 거꾸로_실행되는_모델_Sequence
    private var elements: [Int] {
        return sequence.elements
    }
    var nextIndex: Int
    
    init(sequence: 거꾸로_실행되는_모델_Sequence) {
        self.sequence = sequence
        self.nextIndex = sequence.elements.count - 1
    }
    
    mutating func next() -> Int? {
        guard nextIndex >= 0 else { return nil }
        defer { nextIndex -= 1 }
        return elements[nextIndex]
    }
}

let reversedModelSequence = 거꾸로_실행되는_모델_Sequence(elements: [1, 2, 3, 4, 5])
for element in reversedModelSequence {
    print("[Reversed model 1]: \(element)")
}

//질문: 위 next에서 nextIndex를 초기화 해주지 않았는데 아래 처럼 한 번 더 실행하면 예상치 못한 결과가 나오지 않을까?
//답: for in 에서 새로운 iterator를 만들기 때문에 괜찮다.
for element in reversedModelSequence {
    print("[Reversed model 2]: \(element)")
}
```

### Lazy
-   지연 연산자
-   즉시 연산을 하는게 아니라서 불필요한 연산을 막아준다
-   원리는 아래 처럼 base.next를 호출함으로 가능하다.

```swift
(filter(map(next())))
```

**Lazy Map 구현**

```swift
struct FakeLazyMapSequence<Base: Sequence, Element> {
    let _base: Base
    let _transform: (Base.Element) -> Element
    
    init(_base base: Base, _ transform: @escaping (Base.Element) -> Element) {
        self._base = base
        self._transform = transform
    }
}

extension FakeLazyMapSequence {
    struct Iterator {
        var _base: Base.Iterator
        let _transform: (Base.Element) -> Element

        init(_base: Base.Iterator, _transform: @escaping (Base.Element) -> Element) {
            self._base = _base
            self._transform = _transform
        }
    }
}

extension FakeLazyMapSequence.Iterator: IteratorProtocol, Sequence {
    mutating func next() -> Element? {
        return _base.next().map(_transform)
    }

    func makeIterator() -> FakeLazyMapSequence<Base, Element>.Iterator {
        return self
    }
}

extension FakeLazyMapSequence: Sequence {
    func makeIterator() -> Iterator {
        return Iterator(_base: _base.makeIterator(), _transform: _transform)
    }
}
```

**Lazy Filter 구현**

```swift
struct FakeLazyFilterSequence<Base: Sequence> {
    let _base: Base
    let _predicate: (Base.Element) -> Bool
    
    init(_base: Base, _isIncluded: @escaping (Base.Element) -> Bool) {
        self._base = _base
        self._predicate = _isIncluded
    }
}

extension FakeLazyFilterSequence {
    struct Iterator {
        var _base: Base.Iterator
        let _predicate: (Base.Element) -> Bool
        
        init(_base: Base.Iterator, _ isIncluded: @escaping (Base.Element) -> Bool) {
            self._base = _base
            self._predicate = isIncluded
        }
    }
}

extension FakeLazyFilterSequence.Iterator: IteratorProtocol, Sequence {
    typealias Element = Base.Element
    
    mutating func next() -> Element? {
        while let n = _base.next() {
            if _predicate(n) {
                return n
            }
        }
        return nil
    }
    
    func makeIterator() -> FakeLazyFilterSequence<Base>.Iterator {
        return self
    }
}

extension FakeLazyFilterSequence: Sequence {
    typealias Element = Base.Element
    
    func makeIterator() -> Iterator {
        return Iterator(_base: _base.makeIterator(), _predicate)
    }
}
```

**결과**

```swift
extension LazySequence {
    func fakeFilter(_ isIncluded: @escaping (Base.Element) -> Bool) -> FakeLazyFilterSequence<Base> {
        return FakeLazyFilterSequence<Base>(_base: self.elements, _isIncluded: isIncluded)
    }
}

extension FakeLazyFilterSequence {
    func fakeMap<U>(_ transform: @escaping (Base.Element) -> U) -> FakeLazyMapSequence<FakeLazyFilterSequence<Base>, U> {
        return FakeLazyMapSequence<FakeLazyFilterSequence<Base>, U>(_base: self, transform)
    }
}

[1, 2, 3, 4, 5]
    .lazy
    .fakeFilter { $0 % 2 == 0 }
    .fakeMap { "\($0 * 2)" }
    .forEach { print($0) }
```

[[곰튀김 유료강의]](https://programmers.co.kr/learn/courses/4806) 참고