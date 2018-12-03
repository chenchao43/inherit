JAVA中，所有的继承都是公有继承 
extends表名新类派生于一个已存在的类 
这个已存在的类被称为超类、基类或父类 
新类被称为子类，派生类或孩子类

超类和子类是JAVA程序员的常用术语

超和子是集合术语，子类比超类拥有更多的功能和特性

应该把通用的方法放到超类中，特殊的方法放到子类中

有时，子类中某些域的意义与超类中不同，所以需要覆盖(override)一些方法

子类无法访问超类中的私有域，必须要借助访问器，调用时也不能直接调用，要使用super.xxx

this和super是有区别的，this指代的是对象，super的意义是调用超类方法

子类中可以增加域，方法和覆盖超类的方法 
但是绝对不能删除继承的任何域和方法
super在构造器中的使用

public Manger(String n,double s,int year,int month,int day){
    super(n,s,year,month,day);
    bonus=0;
}

//子类构造器中必须先调用父类构造器(super())

this用途：引用隐式参数，调用该类的其他构造器 
super用途：调用超类的方法，调用超类构造器

继承层次
继承不至于一个层次，可以在子类的基础上再次继承。像树形结构一样。

多态
子类(is-a)是超类，所以子类可以被赋值给超类类型的变量

Employee e;
e=new Employee(...);
e=new Manager(...);

举例来说，Employee可以引用任何一个Employee类对象，也可以引用任何一个Employee类的子类的变量

多态：允许将子类类型指针赋值给父类类型

但是，这样做的原理是编译器将某对象视为超类类型。所以在使用子类私有方法时还是得用子类类型的对象去调用

//举例,详情见程序

staff[0].setBonus(5000);//Error
boss.setBonus(5000);//OK

这是因为,staff是Employee类的

不能把一个超类对象赋值给子类变量

JAVA中，子类数组可以转换成超类数组，不需要强制类型转换，但是最好不要这样使用，因为可能会发生一些不可预知的情况

动态绑定
把一个方法与其所在的类/对象 关联起来叫做方法的绑定。绑定分为静态绑定（前期绑定）和动态绑定（后期绑定）。

静态绑定：程序运行前就已经确定是这个类的了，如final,private,static

动态绑定：程序运行时通过解析才能知道到底调用哪个方法。

动态绑定是程序多态性的保证

注意：子类方法覆盖超类方法时可见性不得小于超类，比如超类是public，那么子类也得是public

阻止继承:final类和方法
人们把不允许扩展的类称为final类

final class Executive extends Manager{
    ...
}

如果用final修饰方法，则方法不可被覆盖 
如果用final修饰域，则域内容不可更改（常量化）

如果用finla修饰类，则不但阻止继承，且类中所有方法变成final类型，但是域不变。

final的主要目的：确保不会在子类中改变语义

final还可以避免动态绑定带来的系统开销，使用内联优化

内联优化：如果方法很短，且频繁使用没有被覆盖的情况下会使用。例如调动e.getName()会被自动替换为访问e.name

强制类型转换
double x=3.405;
int nx=(int)x;

//instanceof 运算符可以检测对象类型
if(staff[1] instanceof Manager){
    boss=(Manger)staff[1];
}
结论： 
只能在继承层次内进行类型转换 
超类转换为子类前，要先用instanceof进行检查

instanceof的左参数为null时结果为false

一般情况下应该减少使用强制类型转换

抽象类
abstract class Person{
    public abstract String getDescription();
}
