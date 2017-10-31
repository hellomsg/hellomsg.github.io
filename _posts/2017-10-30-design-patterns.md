---
title: 设计模式吐槽
---

1. Template Method模式不就是抽象方法吗？  
	
	意图：模版类控制核心算法，代码复用，框架，模版类专注在算法本身，而子类提供完整的实现。
	
	应用：AQS, `Arrays.sort()`, `InputStream`
1. Adapter模式，有两种实现：
	* 使用继承：子类（Adapter适配器）实现接口（Target）调用父类（Adaptee被适配）的方法。
	* 使用委托：类（Adapter适配器）实现接口（Target）调用另一个接口（Adaptee被适配）的方法。

	意图：升级旧的实现以适合新的接口而又不需要重新实现所有功能。
	
	应用：`Hashtable.Enumerator<T> implements Enumeration<T>, Iterator<T>`，Iterator是从jdk1.2引入的，而Enumeration是原有的collection类型使用的，Hashtable为了适配新的接口Iterator，而又不需要重写代码，使Enumerator新增实现新接口，而新接口的方法实现是调用了旧接口的实现。这应该就是上面说的使用委托的方法实现的。
1. Bridge模式使用委托的方式实现的。将实现层次与功能层次拆分开来，Abstraction（基本框架）、RefinedAbstraction（对基本框架的扩展）、Implementor（被委托者，功能细节的定义）、ConcreteImplementor（功能细节的实现）

1. 装饰模式（Decorator），就是一层层包装自己。一个具体的类（ConcreteComponent）继承一个抽象的父类（Component）并实现所有抽象方法，一个装饰物（Decorator）继承上述抽象父类（Component）并包含一个对象（Component），具体的装饰物继承装饰物（Decorator）并实现所有抽象方法，实现时调用具体类（ConcreteComponent）。这种方法可以在实例化Decorator时，传入Component，多次嵌套Decorator，实现功能的不断叠加。
	
	应用：`FilterInputStream`, `BufferedInputStream`, `LineNumberInputStream`, `SynchronizedList`应该也算装饰模式，etc.
1. 观察者模式（Observer）

	应用：`java.util.Observable`
1. 工厂方法（factory method）

	[Apache Commons RNG](https://commons.apache.org/proper/commons-rng/userguide/rng.html#a2._Usage_overview) 的`RandomSource`。
	
	```
	import org.apache.commons.rng.UniformRandomProvider;
import org.apache.commons.rng.simple.RandomSource;
UniformRandomProvider rng = RandomSource.create(RandomSource.MT);
	```
1. 代理模式（Proxy）。

	- 远程代理：RMI
	- 虚拟代理：控制访问创建开销大的资源
	- 保护代理：基于权限控制的资源访问
	
1. 外观模式（Facade-Pattern）

	就是把一套复杂的流程包装起来。意图是提供子系统的一个简化接口。起到解耦的作用。
	
1. 策略模式（Strategy-Pattern)
