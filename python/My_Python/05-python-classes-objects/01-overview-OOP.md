#! https://zhuanlan.zhihu.com/p/568468685
# Python面向对象简介

面向对象编程（Object Oriented Programming，简称OOP)，是利用“类”和“对象”来创建各种模型来实现对真实世界的描述

## 常见概念

### 面向过程

面向过程（Procedure Oriented 简称PO），是一种常见的程序设计思想，

- 核心是过程，即计算机要处理流水线来模拟现实事物发展变化的全过程
- 函数看着程序的最基本单元，一个函数包括要处理的数据及算法逻辑
- 编程是不同函数之间的互相调用
- 抽象层度相对较低
- 优点：极大的降低了写程序的复杂度，只需要顺着要执行的步骤，堆叠代码即可
- 缺点：一套流程只能解决一个(种)实际问题, 且牵一发而动全身。
 - 复用性差
 - 可维护性差

### 面向对象

面向对象（Object Oriented，简称OO），是一种新和程序设计思想

- OOP把对象作为程序的基本单元。
- OOP把程序看做不同对象的相互调用 
- OOP的抽象程度比函数要高

面向对象的常见概念: 

- 类(Class): 描述具有相同的属性和方法的对象集
 - 类变量：定义在类中且在各函数体(方法)之外。
 - 局部变量：定义在方法中的变量，只作用于当前实例的类。
 - 实例变量：类的属性在声明时也采用变量来表示的(self.variableName)。
- 实例化：由抽象类创建一个类的实例，即属于这个类的具体对象。
- 方法：类中定义的函数,必须有一个参数self，放在位置参数的第一位。
- 对象：包括两个数据成员（类变量和实例变量）和操作它们的具体方法。
- 方法重写：如果从父类继承的方法的进一步具体化,也叫方法的覆盖（override）

## 类的创建


```python
class Person():
    # 国籍定义为类变量比较好
    citizenship = "中国"
    
    #通过构造方法实现对实例变量的初始化
    def __init__(self,name,ID,birthdate):
        #定义并对实例变量进行初始化
        self.name = name
        self.ID = ID
        self.birthdate = birthdate
    def  info(self):#显示对象属性的方法
        print("姓名是%s、身份证%s、出生日期是%s" %(self.name,self.ID,self.birthdate))
```

创建的是一个`人`的基本类, 由这个类可以建立一个子类, 比如`学生`.


```python
class Student(Person):
    #声明类变量
    career = '学生'
    
    #通过构造方法实现对实例变量的初始化
    def __init__(self,name,ID,birthdate,student_pass,grade_class):
        #调用父类的方法对前三个属性初始化
        Person.__init__(self,name,ID,birthdate)
        #初始化本类属性
        self.student_pass = student_pass
        self.grade_class = grade_class

    #定义info，显示对象属性的方法, 此处对父类info进行了覆盖
    def  info(self): 
        return self.name,self.ID,self.birthdate,self.student_pass,self.grade_class
```

下面建立一个具体的学生对象


```python
student_1 = Student('张三','43000093434343','1998-08-03','200205001', '02-02')
```


```python
student_1.info()
```




    ('张三', '43000093434343', '1998-08-03', '200205001', '02-02')



 可以再创建一个成绩表类


```python
class scores(Student):
    year = "2022"
    
    def __init__(self, student_pass, physics, mathematics):
        self.student_pass = student_pass
        self.physics = physics
        self.mathematics = mathematics 
        
    def  info(self): 
        return self.student_pass, self.physics, self.mathematics
        
```


```python
scores_1 = scores('200205001', 80, 90)
```


```python
if scores_1.student_pass == student_1.student_pass :
    average = (scores_1.physics + scores_1.mathematics)/2
    print("%s在%s年度的平均成绩为: %d" %(student_1.name, scores_1.year, average))

```

    张三在2022年度的平均成绩为: 85

