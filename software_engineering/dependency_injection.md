# Dependency Injection 依賴注入

以下先從 [Dependency injection on Android: Dagger (Part 1)](http://antonioleiva.com/dependency-injection-android-dagger-part-1/) 這篇言簡意賅的文章切入：

### What is a Dependency?

在瞭解為什麼要使用 Dependency Injection 之前，首要任務就是要定義「什麼是 Dependency」：

> a dependency is a coupling between two modules of our code

或者，從 Java 的角度，基本上只要 `new` ，就是把兩個 module 綁在一起了

```
public class Module1{
   private Module2 module2;

   public Module1(){
      module2 = new Module2();  // Module1 產生了對 Module2 的 dependency
   }

   public void doSomething(){
      ...
      module2.doSomethingElse();
      ...
   }
}
```

### 那怎麼辦? Dependency inversion

既然 `new` 就會產生 dependency，那要怎麼在 Module1 使用 Module2 ？ --> class constructor!

```
public class Module1{
   private Module2 module2;

   public Module1(Module2 module2){
      this.module2 = module2;   // 不要 new, 用 constructor + 參數傳入就好啦
   }

   public void doSomething(){
      ...
      module2.doSomethingElse();
      ...
   }
}
```

### Dependency Injection & Dependency Injector

於是， Dependency Injection 的意思就是

> passing dependencies (inject them) via constructor

在別的地方先 instantiate objects, 再透過 constructor 傳進來。

那這個「別的地方」是哪裡呢？那就要透過 Dependency Injector 啦， [Dagger](http://square.github.io/dagger/) 就是一種 Dependency Injector.


## Reference

* [Dependency injection on Android: Dagger (Part 1)](http://antonioleiva.com/dependency-injection-android-dagger-part-1/)
* [Dependency Injection 筆記 (1)](http://huan-lin.blogspot.com/2011/10/dependency-injection-1.html)

---

## Intro

- Definition
  - Dependency injection is a software design pattern that implements inversion of control and allows a program design to follow the dependency inversion principle. The term was coined by Martin Fowler -  [Wikipedia](http://en.wikipedia.org/wiki/Dependency_injection)
  - In charge of providing instances of the rest of modules

- Why
  - Reduction of boilerplate code
  - It promotes reusability, testability and maintainability.

## Tools

- [RoboGuice](https://github.com/roboguice/roboguice): Dependency injection. Google Guice on Android, version 3.0
  - Performance impact as it's done on runtime using reflection

- [Dagger](https://github.com/square/dagger): A fast dependency injector for Android and Java.
- [ButterKnife](https://github.com/JakeWharton/butterknife): View "injection" library for Android.

## Comparison

- [Difference between Dagger and ButterKnife Android](http://stackoverflow.com/questions/20821148/difference-between-dagger-and-butterknife-android)
  - ButterKnife only for view injection

- [Android's Options for Dependency Injection: Dagger, RoboGuice, and ButterKnife](http://java.dzone.com/articles/androids-options-dependency)
  - RoboGuice is powerful yet time consuming, while Dagger & ButterKnife is fast but not so powerful
