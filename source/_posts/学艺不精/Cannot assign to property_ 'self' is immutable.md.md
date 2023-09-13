---
title: Cannot assign to property: 'self' is immutable
tag: Swift
category: 学艺不精
---

[From Stack Overflow](https://stackoverflow.com/questions/49253299/cannot-assign-to-property-self-is-immutable-i-know-how-to-fix-but-needs-unde)

复现代码：
```Swift
struct MyStruct {
	var fruit = "apple"
	func setFruit(newFruit: String) {
		fruit = newFruit
	}
}
```
问题原因：
struct 是 值类型 (value type) ，初始化后不可修改。

解决方法：
1. 将 Struct 改为 Class
2. 将变量设置为 @State

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMTEwMzY5OF19
-->