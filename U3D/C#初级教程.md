# C#初级教程

##### Scripts as Behavior Components(作为行为组件的脚本)

​	可应用于对象、环境和工程管理中，显示于Inspector中。

##### Variables and Functions(变量和函数)

​	设定盒子用法(确定变量类型)—给定盒子编号(命名变量)—装入物品(给定变量内容)。

​	函数/方法以存储信息的盒子为输入，后返回结果。

##### Conventions and Syntax(约定和语法)

​	关于点运算符、分号、缩进和注释的解释。

##### If Statements(IF语句)

```C#
using UnityEngine;
using System.Collections;

public class IfStatements : MonoBehaviour
{
    float coffeeTemperature = 85.0f;
    float hotLimitTemperature = 70.0f;
    float coldLimitTemperature = 40.0f;
    

    void Update ()
    {
        if(Input.GetKeyDown(KeyCode.Space))
      		TemperatureTest();
        
        coffeeTemperature -= Time.deltaTime * 5f;
    }
    
    
    void TemperatureTest ()
    {
        // 如果咖啡的温度高于最热的饮用温度...
        if(coffeeTemperature > hotLimitTemperature)
        {
            // ... 执行此操作。
            print("Coffee is too hot.");
        }
        // 如果不是，但咖啡的温度低于最冷的饮用温度...
        else if(coffeeTemperature < coldLimitTemperature)
        {
            // ... 执行此操作。
            print("Coffee is too cold.");
        }
        // 如果两者都不是，则...
        else
        {
            // ... 执行此操作。
            print("Coffee is just right.");
        }
    }
}

```

##### Loops(循环)

​	重复操作

```c#
//ForLoop利用可控数量的迭代创建循环
using UnityEngine;
using System.Collections;

public class ForLoop : MonoBehaviour
{
    int numEnemies = 3;
    
    
    void Start ()
    {
        for(int i = 0; i < numEnemies; i++)
        {
            Debug.Log("Creating enemy number: " + i);
        }
    }
}

//WhileLoop在满足条件时执行操作
using UnityEngine;
using System.Collections;

public class WhileLoop : MonoBehaviour
{
    int cupsInTheSink = 4;
    
    
    void Start ()
    {
        while(cupsInTheSink > 0)
        {
            Debug.Log ("I've washed a cup!");
            cupsInTheSink--;
        }
    }
}

//DoWhileLoop在循环主题结束后检验条件
using UnityEngine;
using System.Collections;

public class DoWhileLoop : MonoBehaviour 
{
    void Start()
    {
        bool shouldContinue = false;
        
        do
        {
            print ("Hello World");
            
        }while(shouldContinue == true);
    }
}

//ForeachLoop
using UnityEngine;
using System.Collections;

public class ForeachLoop : MonoBehaviour 
{   
    void Start () 
    {
        string[] strings = new string[3];
        
        strings[0] = "First string";
        strings[1] = "Second string";
        strings[2] = "Third string";
        
        foreach(string item in strings)
        {
            print (item);
        }
    }
}
```

##### Scope and Access Modifiers(作用域和访问修饰符)

​	变量作用域：代码中可使用此变量的区域

​	访问修饰符：定义能够看到变量或函数的位置

##### Awake and Start：加载脚本时自动调用的两个函数

​	Awake：即使未启动脚本组件，适用在脚本与初始化之间设置任何引用

​	Start：在Awake后调用，在首次更新(update)前调用

​	注：Awake和Start在一个对象绑定脚本的生命周期内只能调用一次

##### Update and FixedUpdate：实现每帧更改

​	

​	

​	

