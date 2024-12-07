# **Problem:如何得知物件狀態改變?**

## Intent: Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

## Applicability(以下情況使用)
- When an abstraction has two aspects, one dependent on the other. Encapsulating these aspects in separate objects lets you vary and reuse them independently.
==就是兩邊都有interface且(狀態改變的物件)依賴(接收者)的情況下==
- When a change to one object requires changing others, and you don't know how many objects need to be changed.
==不知道是因為接收者數量是未知，所以是一對多的情況==
- When an object should be able to notify other objects without making assumptions about who these objects are. In other words, you don't want these objects tightly coupled.
==不需要知道接收者是誰(因為有interface)，所以耦合變低==

![Observer1](../img/Observer1.png)
## Consequence
- **抽象耦合**  
    主體與觀察者只透過抽象介面互動，無需依賴具體實現，適合不同層級的分工。
    
- **廣播通知**  
    主體自動通知所有訂閱者，允許動態新增或移除觀察者，簡化通信流程。
    
- **潛在風險**
    
    - 未明確的依賴關係可能導致意外的連鎖更新。
    - 更新協議缺乏細節，觀察者需額外判斷改變內容。