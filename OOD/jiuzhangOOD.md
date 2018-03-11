### OOA vs OOD vs OOP
* OOA (Analysis)
* OOD (Design)
* OOP (Programming)

### OOD和面试
* These question are not so much about regurgitating design patterns as they are about demonstrating that you understand how to create elegant, maintable object-oriented code. Poor performance on this type of question may raise serious red flags.
* 高频公司：Amazon, Bloomberg, TripAdvisor, EMC, Uber...

### 出题问法
* Can you design an elevator system? (设计一个完整系统，little amount of code)
* Can you design scheduler for elevator system? (设计系统中的一部分， need implementation)

### OOD面试陷阱
* 先下手为强。要通过和面试官交流来获取有效信息，而不是自己在那里定义。
* 指鹿为马。询问清楚题目要求，分清楚具体考的是algorithm，还是OOD， 还有system design。OOD注重可用性，而system design注重scalability。
* 反复修改。先给面试官呈现一个usable的成果，然后如果需要改进的地方再进一步修改。
* 虎头蛇尾。做完以后检查自己写的user case,看看是不是都能支持。查漏补缺。

### 如何评判一轮OOD面试
* Communication: 不要自说自话，了解到面试官想要看到的需求。
* Thinking process： 不要思维跳跃，设计过程当中，思路要清晰。
* Correctness： 是否实现了面试官要求的场景。
* Reasonable： 
  * elegant, maintainable, extendable. 
  * 注意使用三要素，封装，继承，多态。
  * 三要素具体表现形式：SOLID原则。
    * S - Single responsibility principle: 一个类应该有且只有一个去改变他的理由， 这意味着一个类应该只有一项工作。
    * O - Open close principle： 对象或实体应该对扩展开放， 对修改封闭 (Open to extension, close to modification)。
    * L - Liskov substitution principle： 任何一个子类或派生类应该可以替换它们的基类或父类。
    * I - Interface segregation principle： 不应该强迫一个类实现它用不上的接口。
    * D - Dependency inversion principle： 抽象不应该依赖于具体实现， 具体实现应该依赖于抽象。
* Good practice
* Design pattern

### 5C解题法
* Clarify: 通过和面试官交流， 去除题目中的歧义， 确定答题范围。
  * What: 针对题目中的关键字来问， 帮助自己更好的确定答题范围。大多数的关键字为名词， 通过名词的属性来考虑。
  * How: 针对问题主题的规则来问， 帮助自己明确解题方向。此类问题没有标准答案， 你可以ᨀ出一些解决方法， 通过面试官的反应，选择一个你比较有信心（简单） 的方案
  * Who：设计由人主导 VS. 设计由系统主导。Optional, 通过思考题目当中是否有人的出现， 来帮助确定解题范围， 一般可以考虑人的角色以及人的属性， 看是否题目需要
  * When： Optional, 通过思考题目当中和时间相关的属性， 来帮助确定解题范围。和时间相关的问题一般都比较细节， 可能会有意想不到的帮助
  * What and how is more important。
* Core objects: 确定题目所涉及的类， 以及类之间的映射关系。
  * 定义：为了完成设计，需要的class。
  * 为什么需要：这是和面试官初步的纸面contract，起到了承上启下的作用，来自于clarify的结果，成为了use case的依据。也为花类图打下基础。
  * 如何定义： 以一个object作为基础，线性思考。 还可以确定object之间的映射关系。
    * Access modifier
      * package (default): 如果什么都不声明， 变量和函数都是package level visible的， 在同一个package内的其他类都可以访问, 在类图中， 避免使用default的package level access
      * public (+): 如果声明为public， 变量和函数都是public level visible的， 任何其他的类都可以访问
      * private (-):如果声明为private， 变量和函数都是class level visible的， 这是所有access modifier中限制最多的一个。 仅有定义这些变量和函数的类自己可以访问。private也是OOD当中实现封装的重要手段。
      * protected (#): 如果声明为private， 变量和函数都是class level visible的， 这是所有access modifier中限制最多的一个。 仅有定义这些变量和函数的类自己可以访问。private也是OOD当中实现封装的重要手段。
* Cases: 确定题目中所需要实现的场景和功能。
  * 定义：在你设计的系统中， 需要支持哪些功能。
  * 为什么需要：
    * 这是你和面试官白纸黑字达成的第二份共识， 把你将要实现的功能列在白板上。
    * 帮助你在解题过程中， 理清条例， 一个一个Case实现。
    * 作为检查的标准。
  * 怎么写：
    * 利用定义的Core Object, 列举出每个Object对应产生的use case。
    * 每个use case只需要先用一句简单的话来描述即可。
* Classes: 通过类图的方式， 具体填充题目中涉及的类。
  * 定义：
  
* Correctness: 检查自己的设计， 是否满足关键点。
