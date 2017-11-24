# Markdown 语法：PlantUML 图

云雀通过集团的[服务](https://puml.alipay.com/)，支持 [PlantUML](http://plantuml.com/) 图。

下面是一些例子。


```plantuml
@startuml

actor 用户

participant "第一级" as A
participant "第二级" as B
participant "第三级" as C

用户 -> A: 开始
activate A
A -> B: 发出请求
activate B
B -> C: 处理
activate C
C --> B: 处理完成
destroy C
B --> A: 发出请求
deactivate B
A --> 用户: 完成
deactivate A

@enduml
```

<pre>
```plantuml
@startuml

actor 用户

participant "第一级" as A
participant "第二级" as B
participant "第三级" as C

用户 -> A: 开始
activate A
A -> B: 发出请求
activate B
B -> C: 处理
activate C
C --> B: 处理完成
destroy C
B --> A: 发出请求
deactivate B
A --> 用户: 完成
deactivate A

@enduml
```
</pre>

```plantuml
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
@enduml
```

<pre>
```plantuml
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice &lt;-- Bob: another authentication Response
@enduml
```
</pre>

```plantuml
@startuml
Class01 <|-- Class02
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 -- Class10
@enduml
```

<pre>
```plantuml
@startuml
Class01 &lt;|-- Class02
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 -- Class10
@enduml
```
</pre>

```plantuml
@startuml

start

repeat
  :read data;
  :generate diagrams;
repeat while (more data?)

stop

@enduml
```

<pre>
```plantuml
@startuml

start

repeat
  :read data;
  :generate diagrams;
repeat while (more data?)

stop

@enduml
```
</pre>

```plantuml
@startuml
:Ready;
:next(o)|
:Receiving;
split
 :nak(i)<
 :ack(o)>
split again
 :ack(i)<
 :next(o)
 on several line|
 :i := i + 1]
 :ack(o)>
split again
 :err(i)<
 :nak(o)>
split again
 :foo/
split again
 :i > 5}
stop
end split
:finish;
@enduml
```

<pre>
```plantuml
@startuml
:Ready;
:next(o)|
:Receiving;
split
 :nak(i)&lt;
 :ack(o)>
split again
 :ack(i)&lt;
 :next(o)
 on several line|
 :i := i + 1]
 :ack(o)>
split again
 :err(i)&lt;
 :nak(o)>
split again
 :foo/
split again
 :i > 5}
stop
end split
:finish;
@enduml
```
</pre>

```plantuml
@startuml
skinparam monochrome true
skinparam shadowing false

class user {
  小孩
  ==
  #userId int(20) -- 用户 id
  gender -- 性别
  nick -- 昵称
  header -- 头像
  birthday -- 生日
  total -- 星星总数
  yebAccount -- 余额宝子账号
}

class guardian {
  监护人
  ==
  #guardianId string(50) -- 监护人 id 主键
  userId -- 支付宝账号 id
  children Array<string> -- 小孩
}

class wish {
  心愿
  ==
  #wishId string(50) -- 心愿 id
  price int(100) -- 价值
  audio string(100) -- 音频地址
  description string(200) -- 心愿描述
  userId
}

class task {
  任务
  ==
  taskId string(50)
  icon string(100) -- 任务图标
  title string(100) -- 任务标题
  value int(10) -- 价值
}

class bill {
  消费、收入记录
  ==
  billId
  userId
  eventType -- 类型 add, sub, task, wish
  originId -- 消费对应的任务或者心愿
  amount -- 数量
  description -- 说明
}

class log {
  日志
  ==
  logId
  action -- createTask,createWish..
  userId -- 操作人
}

user --> wish
guardian -right-> user
user --> task
user --> bill
bill -- wish
bill -- task
@enduml
```

<pre>
```plantuml
@startuml
skinparam monochrome true
skinparam shadowing false

class user {
  小孩
  ==
  #userId int(20) -- 用户 id
  gender -- 性别
  nick -- 昵称
  header -- 头像
  birthday -- 生日
  total -- 星星总数
  yebAccount -- 余额宝子账号
}

class guardian {
  监护人
  ==
  #guardianId string(50) -- 监护人 id 主键
  userId -- 支付宝账号 id
  children Array<string> -- 小孩
}

class wish {
  心愿
  ==
  #wishId string(50) -- 心愿 id
  price int(100) -- 价值
  audio string(100) -- 音频地址
  description string(200) -- 心愿描述
  userId
}

class task {
  任务
  ==
  taskId string(50)
  icon string(100) -- 任务图标
  title string(100) -- 任务标题
  value int(10) -- 价值
}

class bill {
  消费、收入记录
  ==
  billId
  userId
  eventType -- 类型 add, sub, task, wish
  originId -- 消费对应的任务或者心愿
  amount -- 数量
  description -- 说明
}

class log {
  日志
  ==
  logId
  action -- createTask,createWish..
  userId -- 操作人
}

user --> wish
guardian -right-> user
user --> task
user --> bill
bill -- wish
bill -- task
@enduml
```
</pre>

```plantuml
@startuml
actor actor
agent agent
artifact artifact
boundary boundary
card card
cloud cloud
component component
control control
database database
entity entity
file file
folder folder
frame frame
interface  interface
node node
package package
queue queue
rectangle rectangle
storage storage
usecase usecase
@enduml
```



