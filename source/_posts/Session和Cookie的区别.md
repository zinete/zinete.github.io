---
title: Session和Cookie的区别
date: 2022-06-03 20:08:05
tags: "问题记录"
archive: true
---

# Session 和 Cookie 的区别

`session` 和 `cookie` 是用于在客户端与服务器之间保持状态的两种技术，它们有一些显著的区别：

## 1. 存储位置

- **Cookie**  
  存储在客户端（浏览器），数据会随着每次请求自动发送到服务器。
- **Session**  
  存储在服务器，客户端只保存一个唯一的 `session_id`，通过它找到对应的会话数据。

## 2. 生命周期

- **Cookie**  
  默认会在浏览器关闭后失效，除非设置了 `expires` 或 `max-age` 属性，可以持久存储。
- **Session**  
  通常在用户关闭浏览器或服务器设定的超时时间到期后失效（如 30 分钟未操作）。

## 3. 安全性

- **Cookie**  
  数据存储在客户端，容易被窃取或篡改（如通过 XSS 攻击）。可以通过 `HttpOnly` 和 `Secure` 属性提高安全性。
- **Session**  
  数据存储在服务器，安全性更高，但需要依赖 `session_id` 的安全传递和存储。

## 4. 容量限制

- **Cookie**  
  单个 Cookie 的大小限制为 4KB 左右，且每个域名最多存储 20 个左右（不同浏览器限制不同）。
- **Session**  
  理论上不受容量限制，实际受服务器内存或存储空间的影响。

## 5. 适用场景

- **Cookie**  
  常用于保存一些小型的、非敏感的数据，例如用户偏好设置、记住用户名等。
- **Session**  
  常用于需要更高安全性或需要保存用户状态的场景，例如用户登录状态、购物车信息等。

## 6. 性能影响

- **Cookie**  
  由于每次请求都会附加到 HTTP 请求头中，大量使用可能增加网络开销。
- **Session**  
  存储在服务器，会消耗服务器资源。如果并发用户过多，可能导致性能问题。

## 总结

| 特性     | Cookie         | Session                |
| -------- | -------------- | ---------------------- |
| 存储位置 | 客户端         | 服务器                 |
| 生命周期 | 可配置         | 浏览器关闭或超时后失效 |
| 安全性   | 易被窃取/篡改  | 更安全                 |
| 容量限制 | 单个 4KB 限制  | 理论上无明显限制       |
| 适用场景 | 保存轻量级信息 | 保存敏感信息和状态     |

选择使用 `session` 或 `cookie` 应根据实际场景需求和安全性要求来决定。
