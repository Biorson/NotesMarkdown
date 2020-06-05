# Java8的变化

Java8核心新特性：Lambda（匿名函数）、流、默认方法

## 1.流处理

流是一系列数据项，一次只生成一项。程序可以从输入流中一个一个读取数据项，然后以同样的方式将数据项写入输入流。一个程序的输出流可能是另一个程序的输入流。

通过输入，将另外一个可以输出另外一个处出输出流


## 6.收集器
### Collectors类的静态工厂方法
#### toList
返回类型：**List<T>**
用途：把流中所有项目收集到一个List
```java
List<Dish> dishs = menuStream.collect(toList());
```
#### toSet
返回类型：**Set<T>**
用途：把流中所有项目收集到一个Set,删除重复项
```java
Set<Dish> dishs = menuStream.collect(toSet());
```
#### toCollection()
返回类型：**Collection<T>**
用途：把流中所有项目收集到给定的供应源创建的集合
```java
Collection<Dish> dishes = menuStream.collect(toCollection(),
                                            ArrayList::new);
```
#### counting
返回类型：**Long**
用途：计算流中元素的个数
```java
long howManyDishes = menuStream.collect(counting());
```
#### summingInt
返回类型：**Integer**
用途：把流中项目的一个整数属性求和
```java
int totalCalories = menuStream.collect(summingInt(Dish:getCalories));
```
#### averagingInt
返回类型：**Double**
用途：把流中项目Integer属性的平均值
```java
double avgCalories = menuStream.collect(averagingInt(Dish:getCalories));
```
#### summarizingInt
返回类型：**IntSummaryStatistics**
用途：收集关于流中项目Integer属性的统计值，例如最大、最小、总和与平均值
```java
IntSummaryStatistics menuStatistics = menuStream.collect(summarizingInt(Dish:getCalories));
```
#### joining
返回类型：**String**
用途：连接对流中每个项目调用toString()方法所生成的字符串
```java
String shortMenu = menuStream
                       .map(Dish::getName)
                       .collect(joining(", "));
```
#### maxBy
返回类型：**Optional<T>**
用途：一个包裹了流种风格按照给定比较器选出的最大元素的Optional,或如果流为空则为Optional.empty();
```java
Optional<Dish> fattest = menuStream
                       .collect(maxBy(comparingInt(Dish:getCalories)));
```
#### minBy
返回类型：**Optional<T>**
用途：一个包裹了流种风格按照给定比较器选出的最小元素的Optional,或如果流为空则为Optional.empty();
```java
Optional<Dish> lightest = menuStream
                       .collect(minBy(comparingInt(Dish:getCalories)));
```
#### reducing
返回类型：归约操作产生的类型
用途：从一个作为累加器的初始值开始，利用BinaryOperator与流中的元素逐个结合，从而将流归约为单个值
```java
Optional<Dish> lightest = menuStream
                       .collect(reducing(0,Dish::getCalories,Integer:sum));
初始值 T
转换函数(R) -> T
累加函数(T,T)-> T

```
