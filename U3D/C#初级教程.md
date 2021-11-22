# C#初级教程

#### 1.Scripts as Behavior Components(作为行为组件的脚本)

​	可应用于对象、环境和工程管理中，显示于Inspector中。

#### 2.Variables and Functions(变量和函数)

​	设定盒子用法(确定变量类型)—给定盒子编号(命名变量)—装入物品(给定变量内容)。

​	函数/方法以存储信息的盒子为输入，后返回结果。

#### 3.Conventions and Syntax(约定和语法)

​	关于点运算符、分号、缩进和注释的解释。

#### 4.If Statements(IF语句)

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

#### 5.Loops(循环)

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

#### 6.Scope and Access Modifiers(作用域和访问修饰符)

​	变量作用域：代码中可使用此变量的区域

​	访问修饰符：定义能够看到变量或函数的位置

#### 7.Awake and Start：加载脚本时自动调用的两个函数

​	Awake：即使未启动脚本组件，适用在脚本与初始化之间设置任何引用

​	Start：在Awake后调用，在首次更新(update)前调用

​	注：Awake和Start在一个对象绑定脚本的生命周期内只能调用一次

#### 8.Update and FixedUpdate：实现每帧更改

​	Update：在每个使用它的脚本中每帧调用一次，不按固定时间调用

​	FixedUpdate：按固定时间调用(任何影响物理对象的动作应用此来执行，同时应用力来定义移动)

#### 9.Vector Maths(矢量数学)

​	简单的点积和差集科普

#### 10.Enabling and Disabling Components(启用和禁用Unity中的组件)

```c#
public class EnableComponents : MonoBehaviour
{
    private Light myLight;
    
    
    void Start ()
    {
        myLight = GetComponent<Light>();
    }
    
    
    void Update ()
    {
        if(Input.GetKeyUp(KeyCode.Space))
        {
            myLight.enabled = !myLight.enabled;
            //设置为非当前值，按下空格起到切换状态作用
        }
    }
}
```

#### 11.Activating GameObjects(通过脚本激活或停用对象)

​	SetActive函数

```C#
using UnityEngine;
using System.Collections;

public class ActiveObjects : MonoBehaviour
{
    void Start ()
    {
        gameObject.SetActive(false);
    }
}
```

​	注：父对象可被停用，同样停用场景中活跃的子对象，但其在层次结构中仍保持活跃状态。

​	状态查询脚本：

```c#
using UnityEngine;
using System.Collections;

public class CheckState : MonoBehaviour
{
    public GameObject myObject;
    
    
    void Start ()
    {
        Debug.Log("Active Self: " + myObject.activeSelf);
        Debug.Log("Active in Hierarchy" + myObject.activeInHierarchy);
    }
}
```

#### 12.Translate and Rotate(平移和旋转)

```c#
using UnityEngine;
using System.Collections;

public class TransformFunctions : MonoBehaviour
{
    public float moveSpeed = 10f;
    public float turnSpeed = 50f;
    
    
    void Update ()
    {
        if(Input.GetKey(KeyCode.UpArrow))
            transform.Translate(Vector3.forward * moveSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.DownArrow))
            transform.Translate(-Vector3.forward * moveSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.LeftArrow))
            transform.Rotate(Vector3.up, -turnSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.RightArrow))
            transform.Rotate(Vector3.up, turnSpeed * Time.deltaTime);
    }
}
```

#### 13.LookAt：让游戏对象的正向指向世界中另一个transform

```c#
//CameraLookAt
using UnityEngine;
using System.Collections;

public class CameraLookAt : MonoBehaviour
{
    public Transform target;
    
    void Update ()
    {
        transform.LookAt(target);
    }
}
```

#### 14.线性插值

​	Mathf.Lerp 函数接受 3 个 float 参数：一个 float 参数表示要进行插值的起始值，另一个 float 参数表示要进行插值的结束值，最后一个 float 参数表示要进行插值的距离。在此示例中，插值为 0.5，表示 50%。如果为 0，则函数将返回“from”值；如果为 1，则函数将返回“to”值。

​	Lerp 函数的其他示例包括 Color.Lerp 和 Vector3.Lerp。这些函数的工作方式与 Mathf.Lerp 完全相同，但是“from”和“to”值分别为 Color 和 Vector3 类型。在每个示例中，第三个参数仍然是一个 float 参数，表示要插值的大小。这些函数的结果是找到一种颜色（两种给定颜色的某种混合）以及一个矢量（占两个给定矢量之间的百分比）。

​	使用 Color.Lerp 时适用同样的原理。在 Color 结构中，颜色由代表红色、蓝色、绿色和 Alpha 的 4 个 float 参数表示。使用 Lerp 时，与 Mathf.Lerp 和 Vector3.Lerp 一样，这些 float 数值将进行插值。

```c#
// 在此示例中，result = 4
float result = Mathf.Lerp (3f, 5f, 0.5f);

Vector3 from = new Vector3 (1f, 2f, 3f);
Vector3 to = new Vector3 (5f, 6f, 7f);

// 此处 result = (4, 5, 6)
Vector3 result = Vector3.Lerp (from, to, 0.75f);
```

​	<u>**Lerp函数随时间平滑**</u>

​	如果光的强度从 0 开始，则在第一次更新后，其值将设置为 4。下一帧会将其设置为 6，然后设置为 7，再然后设置为 7.5，依此类推。因此，经过几帧后，光强度将趋向于 8，但随着接近目标，其变化速率将减慢。请注意，这是在若干个帧的过程中发生的。如果我们不希望与帧率有关，则可以使用以下代码：

```c#
void Update ()
{
    light.intensity = Mathf.Lerp(light.intensity, 8f, 0.5f * Time.deltaTime);
}
```

​	注：对值平滑使用SmoothDamp函数

#### 15.Destroy：运行时移除游戏对象/从游戏对象移除组件

```c#
//DestroyBasic
using UnityEngine;
using System.Collections;

public class DestroyBasic : MonoBehaviour
{
    void Update ()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(gameObject);
        }
    }
}

//DestroyOther
using UnityEngine;
using System.Collections;

public class DestroyOther : MonoBehaviour
{
    public GameObject other;
    
    
    void Update ()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(other);
        }
    }
}

//DestroyComponent
using UnityEngine;
using System.Collections;

public class DestroyComponent : MonoBehaviour
{
    void Update ()
    {
        if(Input.GetKey(KeyCode.Space))
        {
            Destroy(GetComponent<MeshRenderer>());
        }
    }
}
```

#### 16.GetButton and GetKey

```c#
//KeyInput
using UnityEngine;
using System.Collections;

public class KeyInput : MonoBehaviour
{
    public GUITexture graphic;
    public Texture2D standard;
    public Texture2D downgfx;
    public Texture2D upgfx;
    public Texture2D heldgfx;
    
    void Start()
    {
        graphic.texture = standard;
    }
    
    void Update ()
    {
        bool down = Input.GetKeyDown(KeyCode.Space);
        bool held = Input.GetKey(KeyCode.Space);
        bool up = Input.GetKeyUp(KeyCode.Space);
        
        if(down)
        {
            graphic.texture = downgfx;
        }
        else if(held)
        {
            graphic.texture = heldgfx;
        }
        else if(up)
        {
            graphic.texture = upgfx;
        }
        else
        {
            graphic.texture = standard; 
        }
        
        guiText.text = " " + down + "\n " + held + "\n " + up;
    }
}
```

```c#
//ButtonInput
using UnityEngine;
using System.Collections;

public class ButtonInput : MonoBehaviour
{
    public GUITexture graphic;
    public Texture2D standard;
    public Texture2D downgfx;
    public Texture2D upgfx;
    public Texture2D heldgfx;
    
    void Start()
    {
        graphic.texture = standard;
    }
    
    void Update ()
    {
        bool down = Input.GetButtonDown("Jump");
        bool held = Input.GetButton("Jump");
        bool up = Input.GetButtonUp("Jump");
        
        if(down)
        {
            graphic.texture = downgfx;
        }
        else if(held)
        {
            graphic.texture = heldgfx;
        }
        else if(up)
        {
            graphic.texture = upgfx;
        }
        else
        {
            graphic.texture = standard;
        }
    
        guiText.text = " " + down + "\n " + held + "\n " + up;
    }
}
```

#### GetAxis

​	Input.GetAxis：不同于GetKey与GetButton，GetAxis不返回布尔值，而是返回浮点数(介于-1到1之间)。

​	Negitive Button：负按钮

​	Positive Button：正按钮

​	Gravity：滑尺在按钮松开后归零的速度(越高则越快)

​	Dead：值越小操纵杆移动幅度越小

​	Sensitivity：控制输入的返回值到达1/-1的速度(越大则反应速度越快，越小越流畅)

​	Snap：同时按下正负按钮时归零

```c#
//AxisExample:有平滑
using UnityEngine;
using System.Collections;

public class AxisExample : MonoBehaviour
{
    public float range;
    public GUIText textOutput;
    
    
    void Update () 
    {
        float h = Input.GetAxis("Horizontal");
        float xPos = h * range;
        
        transform.position = new Vector3(xPos, 2f, 0);
        textOutput.text = "Value Returned: "+h.ToString("F2");  
    }
}

//AxisRawExample:无平滑
using UnityEngine;
using System.Collections;

public class AxisRawExample : MonoBehaviour
{
    public float range;
    public GUIText textOutput;
    
    
    void Update () 
    {
        float h = Input.GetAxisRaw("Horizontal");
        float xPos = h * range;
        
        transform.position = new Vector3(xPos, 2f, 0);
        textOutput.text = "Value Returned: "+h.ToString("F2");  
    }
}

//DualAxisExample
using UnityEngine;
using System.Collections;

public class DualAxisExample : MonoBehaviour 
{
    public float range;
    public GUIText textOutput;
    
    
    void Update () 
    {
        float h = Input.GetAxis("Horizontal");
        float v = Input.GetAxis("Vertical");
        float xPos = h * range;
        float yPos = v * range;
        
        transform.position = new Vector3(xPos, yPos, 0);
        textOutput.text = "Horizontal Value Returned: "+h.ToString("F2")+"\nVertical Value Returned: "+v.ToString("F2");    
    }
}
```

#### 18.OnMouseDown：检测对碰撞体或GUI文本元素的点击

```c#
//MouseClick
using UnityEngine;
using System.Collections;

public class MouseClick : MonoBehaviour
{
    void OnMouseDown ()
    {
        rigidbody.AddForce(-transform.forward * 500f);
        rigidbody.useGravity = true;
    }
}
```

#### 19.GetComponent：访问其他脚本和组件

```c#
//UsingOtherComponents
using UnityEngine;
using System.Collections;

public class UsingOtherComponents : MonoBehaviour
{
    public GameObject otherGameObject;
    
    
    private AnotherScript anotherScript;
    private YetAnotherScript yetAnotherScript;
    private BoxCollider boxCol;
    
    
    void Awake ()
    {
        anotherScript = GetComponent<AnotherScript>();
        yetAnotherScript = otherGameObject.GetComponent<YetAnotherScript>();
        boxCol = otherGameObject.GetComponent<BoxCollider>();
    }
    
    
    void Start ()
    {
        boxCol.size = new Vector3(3,3,3);
        Debug.Log("The player's score is " + anotherScript.playerScore);
        Debug.Log("The player has died " + yetAnotherScript.numberOfPlayerDeaths + " times");
    }
}
```

```c#
//AnotherScript
using UnityEngine;
using System.Collections;

public class AnotherScript : MonoBehaviour
{
    public int playerScore = 9001;
}
```

```c#
//YetAnotherScript
using UnityEngine;
using System.Collections;

public class YetAnotherScript : MonoBehaviour
{
    public int numberOfPlayerDeaths = 3;
}
```

#### 20.DeltaTime：两值之差

​	time类的DeltaTime属性基本指两次更新或固定更新函数调的间隔时长

​	作用：让用于移动其他增量计算的值变得平滑

```c#
using UnityEngine;
using System.Collections;

public class UsingDeltaTime : MonoBehaviour
{
    public float speed = 8f; 
    public float countdown = 3.0f;

    
    void Update ()
    {
        countdown -= Time.deltaTime;
        if(countdown <= 0.0f)
            light.enabled = true;
        
         if(Input.GetKey(KeyCode.RightArrow))
            transform.position += new Vector3(speed * Time.deltaTime, 0.0f, 0.0f);
    }   
}
```

#### 21.DataTypes(数据类型)

​	值类型：int、float、double、bool、char、Structs(Vector3和Quaternion)

​	引用类型：Classes(Transform和GameObject)

​	区别：值类型包含某个值；引用类型包含值存储位置的存储地址





​	

​	

