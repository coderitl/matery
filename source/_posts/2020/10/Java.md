---
title: Java基础
date: 2020-10-13 18:44:19
tags: Java
categories: "Java" #分类
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Java.jpg
---

### Java 变量:

```java
class TypeodData {
    public static void main(String[] args) {
        // 变量的定义格式
        // 数据类型 变量名 = 变量值;
        int a = 10;
        System.out.println("变量的使用: "+a);
        // 变量就是内存中的空间，内部存储着不断发生变化的数据
    }
}
```

### 键盘录入:

```java
  		import java.util.Scanner;		
		// 键盘录入
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        System.out.println(num);

```

### 数值拆分:

```java
 
        // 键盘录入
        Scanner scan = new Scanner(System.in);
        // 123
        int num = scan.nextInt();
        
        int b = num % 10; // 123 除以 10 为商 12 余 3，%--> 只取余数
        int c = num / 10 % 10; // 123 除以 10 为 12 12%10 商 1 余 2
        int d = num / 100;

        System.out.println(b); // 3
        System.out.println(c); // 2
        System.out.println(d); // 1
```

### 自增自减运算符:

```java
class TypeodData {
    public static void main(String[] args) {
        int a = 1,b = 0;
        b = a--;
        System.out.println(b); // 1
        
        // 单独使用 a++
        a++;
        System.out.println(a); // 2
    }
}

    ++ / -- 单独使用: 效果一致

    参与操作:

        ++ 在前: 先对该变量做自增(++) 或者自减(--),然后在拿变量参与操作

        ++ 在后: 先将该变量原本的值，取出来参与操作，随后再进行自增(++),自减(--)

       只允许操作变量(++/--)
        
```

### 三元运算符:



```java
		
// 求两个数中的最大值 		
		int a = 1;
		int b = 0;
        int max = a>b ? a : b;
        System.out.println(max);

```

### 流程控制:

+ `if`

  ```java
  // 关系表达式为 true 执行 语句体
  
  if(关系表达式){
      语句体;
  }
  ```

+ `switch`

  ```java
          int age = 1;
          switch(age){
              case 1: System.out.println("1"); break;
              case 2: System.out.println("1"); break;
              
              default:
                  	System.out.println("3");
          }
  
  ```

  

+ `for` 循环

  ```java
          for(初始化语句;条件判断语句;条件控制语句){
              语句体;
          }
  		
  ```

  ```java
  // 水仙花数的求取
  
   // 水仙花数的求取
          for (int i = 100; i <= 999; i++) {
              int a = i % 10;
              int b = i / 10 % 10;
              int c = i / 100 % 10;
              if (a * a * a + b * b * b + c * c * c == i) {
                  System.out.println(i);
              }
          }
  ```

  

  ```java
  // 水仙花数换行输出
  
  class TypeodData {
      public static void main(String[] args) {
          // 水仙花数的求取
          int count = 0;
          for (int i = 100; i <= 999; i++) {
              int a = i % 10;
              int b = i / 10 % 10;
              int c = i / 100 % 10;
              if ((a * a * a + b * b * b + c * c * c) == i) {
                  System.out.print(i + " ");
                  count++;
                  if (count % 2 == 0) {
                      System.out.println();
                  }
              }
          }
      }
  }
  ```

  

### `while`循环:

```java
  while(条件判断语句){
           循环体;
      	   条件控制语句;
       }


// 求取珠穆朗玛峰在 0.1 毫米的纸张需要折叠的次数
class TypeodData {
    public static void main(String[] args) {
        // 定义纸张的厚度
        double paper = 0.1;
        // 定义珠穆朗玛峰的高度 (毫米)
        int zl = 8844430;
        // 定义计数器
        int count = 0;
        // 当纸张小于或等于 珠穆朗玛峰的高度时
        while (paper <= zl) {
            // 纸张折叠
            paper *= 2;
            // 计数器累加
            count++;
        }
        System.out.println(count);
    }
}
// count = 27
```



### `do  while` 循环:

```java
 	do{
        循环体;
      }
      while(条件语句)
    
```



### `for `和 `while`之间的区别: 

```java
// 条件控制语句所控制的自增变量因为归属 for 循环的语法结构中，在 for 循环结束后，就不能再次被访问到了

// 条件控制语句所控制的自增变量对于 while 循环来说不归属其语法结构中，在 while 循环结束后，该变量还可以继续使用

```

### `Random:`

```java
// 获取 1 ~ 10之间的随机数打印 10 次

import java.util.Random;

class TypeodData {
    public static void main(String[] args) {
        Random r = new Random();
        for (int i = 1; i <= 10; i++) {
            int num = r.nextInt(10)+1;
            System.out.println(num);
        }
    }
}

```



### 数组:

```java
// 数据类型[] 变量名
    
   int[] array =  {};

// 动态初始化
 
	int[] array = new int[数组长度];
```

### 求数组中的最大值:

```java
		int[] aray = {5, 2, 17, 9, 1};
        int max = aray[0];
        for (int i = 1; i < aray.length; i++) {
            if (aray[i] > max) {
                max = aray[i];
            }
        }
        System.out.println(max);
```

### 求数组的最小值:

```java
		int[] aray = {5, 2, 17, 9, 1};
        int min = aray[0];
        for (int i = 1; i < aray.length; i++) {
            if (aray[i] < min) {
                min = aray[i];
            }
        }
        System.out.println(min);
```

### 数组元素的反转(只能使用原数组):

```java
		int[] aray = {5, 2, 17, 9, 1};
		// 对称位置的交换 min = left(索引位置 0 ),max = right(位置 aray.length)
        for (int min = 0, max = aray.length - 1; min < max; min++, max--) {
            int temp = aray[min];
            aray[min] = aray[max];
            aray[max] = temp;
        }
        for (int i = 0; i < aray.length; i++) {
            System.out.println(aray[i]);
        }
```

```java
		// 优化 
		int[] aray = {5, 2, 17, 9, 1};
        for (int min = 0, max = aray.length - 1; min < max; min++, max--) {
            int temp = aray[min];
            aray[min] = aray[max];
            aray[max] = temp;
            }  
        }
		// 将数组作为参数传入
        public static void printArray(int[] aray) {
            for (int i = 0; i < aray.length; i++) {
                System.out.println(aray[i]);
            }
        }
```





### 方法的定义和使用:

```java
// 主方法之外定义
public static void eat(){
        System.out.println("eat····");
    }

// 调用
eat();
```

### 方法的重载:

```java
public static int methods(int a){
        System.out.println(a);
        return a;
    }

public static int methods(int a,int b){
    System.out.println(a+b);
    return a+b;
}
```



### 面向对象:

```java
面向过程: 当需要实现一个功能的时候，每一个步骤都需要亲力亲为，详细处理每一个细节
    
面向对象: 当需要实现一个功能的时候，不关心具体的步骤，而是找一个已经具有该功能的人，来帮我作事
```



### 类:

```java
类：是一组相关属性和行为的集合，可以看成是一类事物的模板，使用事务的属性特征和行为特征来描述该类事物
```

```java
class Student{
  // 成员变量
    int age = 12;
   	String name = "张三";
  // 成员方法
    public void learn(){
         System.out.println("learn·····");;
    }
}


 // 类的使用
 Student student = new Student();
 System.out.println(student.name);

 student.learn();
```



### `this`:

```java
通过谁调用的 this，谁就是 this
```



### 构造方法:

```java
public class Student{
    
    public Student(){
        // 无参构造
    }
    
    
}
```



```java
package com.ltd.aidou;

public class Random_demo {

    public Random_demo(){
        System.out.println("构造方法执行·········");
    }
    
    public static void main(String[] args) {
        Random_demo r = new Random_demo();
    }
}

```

### 对象数组

```java
package com.ltd.aidou;
public class Random_demo {

    public static void main(String[] args) {
        Student[] students = new Student[3];
        Student student = new Student(12,"as");
        Student student2 = new Student(22,"ss");
        Student student3 = new Student(32,"sass");
		
        
        students[0] = student;
        System.out.println(students[0].getName());
    }
}
```

```java
package com.ltd.aidou;

class Student {
    private int age;
	private String name;
    
    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### 集合:

```java
对于 ArrayList 来说，有一个尖括号 <E> 代表泛型
    
泛型: 也就是装在集合中的所有元素,全部是统一的什么类型

注意: 泛型只能是引用类型,不能是基本类型
    
```

```java
		ArrayList<String> list = new ArrayList<>();
        list.add("张三");
        list.add("李四");
        list.add("王麻子");
        System.out.println(list); // [张三, 李四, 王麻子]
```

```java
add(); // 添加
    
remove(); // 被删除的索引

size(); // 获取长度

get(); // 通过索引获取想要的位置
```

```java
		// 集合的遍历
		ArrayList<String> list = new ArrayList<>();
        list.add("张三");
        list.add("李四");
        list.add("王麻子");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }

	// 优化 for 循环
        for(String item:list){
            System.out.println(item);
        }
```

```java
		// 生成 6 个 1 ~ 33 之间的随机数，添加到 集中并遍历集合

        import java.util.ArrayList;
        import java.util.Random;

		ArrayList<Integer> list = new ArrayList<>();
        Random r = new Random();
        for (int i = 0; i < 6; i++) {
            int num = r.nextInt(32) + 1;
            list.add(num);
            System.out.println(list.get(i));
        }

```

```java
// 创建 4 个学生对象,并将学生添加在集合中，之后遍历集合

package com.ltd.aidou;

import java.util.ArrayList;

public class Random_demo {

    public static void main(String[] args) {
        Student one = new Student(12, "张三12");
        Student two = new Student(13, "张三13");
        Student three = new Student(14, "张三14");
        Student four = new Student(15, "张三15");

        ArrayList<Student> list = new ArrayList<>();
        // 添加
        list.add(one);
        list.add(two);
        list.add(three);
        list.add(four);
        // 遍历
        for (int i = 0; i < list.size(); i++) {
            Student s = list.get(i);
            System.out.println(s.getName());
        }
    }
}

```

```java
// 集合也可以作为方法的参数


package com.ltd.aidou;

import java.util.ArrayList;

public class Random_demo {

    public static void main(String[] args) {
        Student one = new Student(12, "张三12");
        Student two = new Student(13, "张三13");
        Student three = new Student(14, "张三14");
        Student four = new Student(15, "张三15");

        ArrayList<Student> list = new ArrayList<>();
        // 添加
        list.add(one);
        list.add(two);
        list.add(three);
        list.add(four);
        printArrlist(list);
    }

    public static void printArrlist(ArrayList<Student> list) {
        System.out.print("{");
        // 遍历
        for (int i = 0; i < list.size(); i++) {
            Student name = list.get(i);
            // list.size() -1  拿到最后一个值
            if (i == list.size() - 1) {
                System.out.print(name.getName() + "}");
            } else {
                System.out.print(name.getName() + "@");
            }
        }
    }
}


// 输出结果: {张三12@张三13@张三14@张三15}
```

### 字符串的概述和特点:

```java
** 字符串的内容不可变
```

```java
字符串的截取:

	substring(int index,int end); // 起始位置
```

### 数组工具类；

```java
import java.util.Arrays;

		// 转换为字符串数组
		// Arrays.tostring(); 
      	int[] array = {10,20,30}; 
        String newArray = Arrays.toString(array);
        System.out.println(newArray); // [10, 20, 30]

		sort(); // 排序
```

### 继承:

```java
主要解决 共性抽取
```

### 

### 抽象的概念:

```java
+ 抽象类不能被实例化。
    
+ 有抽象方法的类，一定是抽象类，但是抽象类可以没有抽象方法。
    
+ 当一个类继承的父类是抽象类的话，需要我们把抽象类中的所有抽象方法全部实现。
    
+ 抽象方法不能有方法体。
```

```java
package com.ltd.abStract;

public abstract class abStract_demo {
    // 定义抽象方法
    public abstract void cat();

    public static void main(String[] args) {
         Animail animail = new Animail();
         animail.cat();
    }
}
```



```java
package com.ltd.abStract;
// 继承之后使用抽象方法
public class Animail extends abStract_demo {
    public void say() {
        System.out.println("say Aniamail··········");
    }

    // 方法重写
    @Override
    public void cat() {
        System.out.println("猫吃鱼············");
    }
}

```



### 接口:

```java
public abstract 返回值类型(参数列表);

** 注意事项:
	
	1. 接口当中的抽象方法，修饰符必须是两个固定的关键字: public abstract
        
    2. 这两个关键字可以选择性的省略
        
```

```java
接口的使用步骤:

 1. 接口不能直接使用，必须有一个 “实现类” 来“实现” 该接口
     
 2. 接口的实现类必须覆盖重写(实现)接口中所有的抽象方法
    
```

### 多态：

```java
	左 父 右 子 为多态 (class Fu,class Zi)
    
    Fu obj = new Zi();

	
```


