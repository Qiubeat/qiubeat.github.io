---
title: Cannot assign to property: 'self' is immutable
tag: Swift
category: 学艺不精
---
[From Stack Overflow](https://stackoverflow.com/questions/49253299/cannot-assign-to-property-self-is-immutable-i-know-how-to-fix-but-needs-unde)

复现代码：
```swift
struct MyStruct {
	var fruit = "apple"
	func setFruit(newFruit: String) {
		fruit = newFruit
	}
}
```
问题原因：
`struct` 是 值类型 (value type) ，初始化后不可修改。

解决方法：
1. 将 `struct` 改为 `class`
2. 将变量设置为 `@State`

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUxMjY3MjAyNiwtNzAxMTAzNjk4XX0=
-->