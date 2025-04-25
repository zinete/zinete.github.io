---
title: 学习swift ui笔记
date: 2021-08-04 11:08:05
tags: "学习"
categories:
archive: true
  - [学习]
---

# SwiftUI 学习笔记

### 视图操作

> SwiftUI 常用方法 官方学习教程 https://developer.apple.com/tutorials/swiftui/

```swift
func scaleEffect(_ scale: CGSize, anchor: UnitPoint = .center) -> some View
```

##### 相对于锚点，按给定的垂直和水平尺寸大小缩放此视图的渲染输出

- **scale**

  相对于水平和垂直方向的缩放比

- **anchor**

  默认为 UnitPoint/center 的点 定义视图中应用的位置

```swift
func hueRotation(_ angle: Angle) -> some View
```

- **Angle(degrees: 180)**

  对视图进行色调调整

```swift
func grayscale(_ amount: Double) -> some View
```

- **.grayscale(0.50)**

  对视图添加灰度效果

### 数据操作

```swift
@inlinable public func environmentObject<T>(_ object: T) -> some View where T : ObservableObject
```

##### 向子元素 传递 ObservableObject 对象使数据可以被监听
