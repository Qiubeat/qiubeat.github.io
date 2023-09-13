---
title: initializer is inaccessible due to 'private' protection level
tag: Swift
cage
---

[From Swift Forums](https://forums.swift.org/t/initializer-is-inaccessible-due-to-private-protection-level/54808)

复现代码：
```
struct MyStruct {
	var fruit: String
	private var animal: String?

	func setAnimal(animal: String) {
		self.animal = animal
	}
}

struct Variety {
	var my: MyStruct = MyStruct(fruit: "apple")
}
```

问题原因：
调用 `MyStruct` 在初始化成员时是最终会转化为 `init(fruit: String, animal: String?)` ，而`animal` 是 `private` 类型，`MyStruct` 外部访问不到 `animal` 属性，所以会报错。

解决方案：
1. 删掉 `private`
2. `private var` 换成 `private let` ，但是`private let` 的变量只能初始化一次，后续不可更改。



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzU4NTA1M119
-->