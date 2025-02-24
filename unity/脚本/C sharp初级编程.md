### 消息
#### Awake()
以下3种情况时调用Awake：
- 在加载场景时初始化包含脚本的活动GameObject时
- 在将非活动的GameObject设置为活动时
- 使用Object.Instantiate创建的GameObject之后

在脚本实例的生存周期内，Unity仅调用Awake一次。对于放置在场景中的活动GameObject，Unity在初始化场景中的所有活动GameObject后调用Awake。
#### Start()
在首次调用任何Update方法之前启用脚本时，在帧上调用Start
#### Update()
如果启用了`MonoBehaviour`，则每帧调用Update。由于帧数不稳定，所以帧数越高，同一时间内调用Update的次数就越多
#### FixedUpdate()
用于物理计算且独立于帧率的消息。在`FixedUpdate`之后，进行`Physics`系统计算。`FixedUpdate`的默认调用间隔为0.02秒
#### OnMouseDown()
当用户在有`Collider`的GameObject上按下鼠标左键时，将调用该消息

### 实例方法
#### Component.GetComponent\<T>()
获取GameObject上指定类型的组件的引用，否则为null
### 其他
#### 启用和禁用组件
获取到组件引用后，可以通过设置组件的`enabled`属性为`true`来启用组件。
#### 激活/停用GameObject
可以通过`GameObject.SetActive(true)`来激活GameObject。

还可以通过GameObject的`activeInHierarchy`属性来查看GameObject在Scene中是否处于活动状态。
以及`activeSelf`属性：此GameObject的本地活动状态
#### Transform
`Transform`类用于对象的位置、旋转和缩放。
- `translate`移动变换
- `rotate`旋转
- `LookAt`使向前矢量指向target
#### 线性插值
有时需要两个值之间的某个值，可以通过`Mathf.Lerp`函数来完成
```c#
//value == 4f
//Lerp(start,end,百分比)
//百分比指进行插值的距离
float value = Mathf.Lerp(3f,5f,0.5f);
```
#### Destory
`public static void Destroy (Object obj, float t= 0.0F);`
可以使用从Object继承的静态函数`Destory`来删除GameObject、组件或资源。t表示延迟多少秒
#### Input
##### GetButton和GetKey
检测指定的键或是按钮被按下
##### GetAxis
获取基于轴的输入，可在设置中修改虚拟轴。
`GetAxisRaw`方法与`GetAxis`相同，但`GetAxisRaw`没有应用平滑过滤
#### deltaTime
`Time.deltaTime`返回自上一帧完成以来经过的时间
#### Instantiate
使用`Instantiate`创建预制件，可以克隆对象并指定对象的位置、方向。
#### Invoke
`Invoke(funcName,time)`
可以延时执行指定名字的函数。
还可以使用`InvokeRepeating(函数名，延时时间，重复时间间隔)`来重复调用，可以用`CancelInvoke`函数取消