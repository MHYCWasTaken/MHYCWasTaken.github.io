# 【中】项目Chess--使用Godot的国际象棋（01）

<!-- readme -->

<!-- outline-start -->

学校的希沃里发现了一些先辈的遗产，是三国杀，虽然只剩下快捷方式了，但我们也萌生了给希沃留下一些遗产的念头

反复思考之后，我选择了棋子数量较少而同时具有挑战性并且经典的国际象棋

<!-- outline-end -->

（出于对希沃性能考虑，但是没想到他的配置比我的笔记本都好qwq）

# 项目定位

1. 希沃遗产
2. 一个国际象棋程序
3. 比市面上的其他国际象棋程序要好，做完希望可以上架steam赚钱（哼，自不量力）

## $ 01 / 01 : 选择引擎

1. 因为我的笔记本是ubuntu系统，所以引擎跨平台是硬要求
2. 打包完的程序尽可能小
3. 易用
4. 开源，MIT协议
5. 最好能支持去除启动时的引擎动画

宗上，我选择了GODOT引擎，此引擎达成以上除了第二点以外所有条件，令我十分满意

## $ 01 / 02 : 开始吧！

本博客不包含新人指引及GDScrpit教程，建议先自行了解godot编辑器基本操作，如有需要可以参见相关链接，了解完以后可以跟着写出来
项目选用GLES 2.0，*会涉及代码，极少量数学，极少量godot外操作*，有耐心的话还是很简单的
跟随教程时请同时加入思考，码农基本素养

### 01 棋盘

项目窗口大小默认Stretch Mode为2D，Aspect为expand（窗口拉伸时的拉伸）
创建场景，根节点为Node2D，创建Sprite，命名为Board
新建Camera2D，AnchorMode为Fixed Top Left，Current启用
这里使用fixed top left是因为如果使用center，坐标系原点在中间，棋子坐标需要考虑正与负，不好计算（第一版用的center，难受）
材质偷懒直接画出来了，格子150*150px：

![棋盘材质](:2022-06-04-01.png)

添加坐标（可有可无），我用的是 `Lable` ，字体是 `Harmony_sans_bold` ，具体怎么添加就不赘述了，所有lable放到Board的子结点，并设置Board无法选中，防止不小心移动

棋盘位置设置为75,75因为格子是150*150的，所以棋子设置为150的倍数可以直接位于格子中间

camera2D位置设置为-225,-225，zoom为2.5,2.5可以以一个舒服的位置显示棋盘（左边，右边以后会有GUI）

![运行效果](:2022-06-04-02.png)

### 02 棋子

这里开始有挑战性了（对我这个第一次用godot做东西的屑）

第一个问题是国际象棋总共32颗棋子，创建32个sprite并分别写脚本太傻了，且后续出现问题难以统一修改，经典屎山代码
我们一同查阅，互联网上并没有相关类似教程，我们的这个项目定位比较特殊，没有线性剧情，没有固定场景，所以资料较少
所以我决定就这样了，32个sprite就32个吧

屎山下一版会修的，我直接全部重新写，如果不想要实践可以跳到[下一版](http://mhyc.tech/zh/2022-06-05-chess-how-02.html)，看看是如何修复的

先添加一个棋子，添加材质

因为棋子材质太大了，我们把棋子的scale设置为0.3, 0.3

[此处下载棋子材质](/assets/files/uploads/pieces-textures.zip)

为sprite添加脚本

我们想要比较别具一格的移动棋子方式，所以我们决定实现拖动棋子移动（后续会添加点击移动，画大饼（逃））
在任何图形化的应用的鼠标事件分为3种：刚按下，刚松开，按着
那么点击呢？你可以在按下时记录时间，松开时记录时间，再一减，就能得到按住的时间，如果不大于150ms就判断为点击

_（不过这次我们先做拖动，比较简单）_

```
extends Sprite


var mouse_pos

func _abs_value(var i) -> int:
	return int(max(i, -i))

func _physics_process(_delta):  #物理事件方法，每帧调用
	mouse_pos = get_global_mouse_position()  #gd自带方法获取鼠标位置
	if Input.is_action_just_pressed("left_mouse_button"):  #Input事件获取鼠标左键刚按下
		var abs_x = _abs_value(mouse_pos.x - self.position.x)
		var abs_y = _abs_value(mouse_pos.y - self.position.y)
		print("icos")
	if Input.is_action_pressed("left_mouse_button"):
		self.position = mouse_pos
		print("moved")
	if Input.is_action_just_released("left_mouse_button"):
		print("released")
	pass

```

除此之外，还需要判断是否点击在自己身上，否则无论点击哪里都可以拖动：
![效果](:2022-06-04-05.gif)
点击时记录鼠标位置，与自己位置的x和y分别相减，取绝对值，都不大于75就是点击在自己

```
extends Sprite


var texture_size = 150
var is_clicked_on_self = false
var mouse_pos

func _abs_value(var i) -> int:  # 一个绝对值的算法，可以照抄:)
	return int(max(i, -i))

func _physics_process(_delta):  # 物理事件方法，每帧调用
	mouse_pos = get_global_mouse_position()  # gd自带方法获取鼠标位置
	if Input.is_action_just_pressed("left_mouse_button"):  # Input事件获取鼠标左键刚按下
		var abs_x = _abs_value(mouse_pos.x - self.position.x)
		var abs_y = _abs_value(mouse_pos.y - self.position.y)
		if abs_x < texture_size / 3 && abs_y < texture_size / 3:  # 点击在自己
			is_clicked_on_self = true
			print("icos")
	if Input.is_action_pressed("left_mouse_button") && is_clicked_on_self:  # 鼠标拖动且点击在自己
		self.position = mouse_pos  # 移动至鼠标位置
		print("moved")
	if Input.is_action_just_released("left_mouse_button"):  # 鼠标松开
		print("released")
		is_clicked_on_self = false  # bool复原
	pass

```

![效果](:2022-06-04-04.gif)

### 03 修正用的格子

现在很明显，棋子随便摆哪里不是我们想要的，我们想要放下时可以自动摆正假设棋子的位置是 `piece_pos` ，我们需要的是：

1. 寻找最近的格子中心点
2. 出棋盘一定范围可以回正
3. 如果出棋盘太远回到之前位置

既然这样，我们不如先制作一个光标，一来可以更方便的调试算法，二来这个功能似乎也很有必要

添加一个sprite，命名为 `CorrectorBlock` (纠正方块)，材质随便一个颜色的150*150方块（最好要有透明度）：
![纠正方块材质](:2022-06-04-03.png)

将这个spite放到board下棋子上（图层）并把他摆到一个镜头看不见的地方

接下来解决移动逻辑

我们之前对棋盘的一系列设置已经使得只要纠正方块处于150倍数的坐标是一定处于格子中心，那么我们直接将x和y分别处以一150向下取整再乘150即可

接下来添加脚本：

```
extends Sprite


var mouse_pos = get_global_mouse_position()

func _ready():
	pass

func _physics_process(delta):
	mouse_pos = get_global_mouse_position()
	if mouse_pos.x >= -75 && mouse_pos.x <= 1125 && mouse_pos.y >= -75 && mouse_pos.y <= 1125:
		self.position = mouse_pos
	else:
		self.position = Vector2(-300.0 , -300.0)
```

（这个应该看得懂，不加注释了，看不懂对照之前代码）
运行以后，可以发现，光标在离开棋盘以后会消失，但是和我们想要的效果还是差了许多，我们希望这个光标可以用来纠错，方便调试

修改代码：

```
extends Sprite


var mouse_pos = get_global_mouse_position()

func _ready():
	pass

func _physics_process(delta):
	mouse_pos = get_global_mouse_position()
	if mouse_pos.x >= -75 && mouse_pos.x <= 1125 && mouse_pos.y >= -75 && mouse_pos.y <= 1125:  # 看看鼠标在不在棋盘里
		mouse_pos.x += 75  # 鼠标位置各加75,因为坐标系是-75
		mouse_pos.y += 75  #
		self.position.x = int(mouse_pos.x / 150) * 150
		self.position.y = int(mouse_pos.y / 150) * 150
	else:
		self.position = Vector2(-300.0 , -300.0)
```

这样好多了:)

![效果](:2022-06-04-06.gif)

### 04 棋子摆放

现在就简单了，把修正格子的逻辑般过来就行了

```
extends Sprite

var texture_size = 150
var is_clicked_on_self = false
var mouse_pos
var orig_pos  # 记录拿起的位置

func _ready():
	orig_pos = self.position
	pass

func _abs_value(var i) -> int:
	return int(max(i, -i))

func _drop_piece():
	mouse_pos = get_global_mouse_position()
	if mouse_pos.x > -100 && mouse_pos.x < 1125 && mouse_pos.y > -100 && mouse_pos.y < 1125:
		print("in")
		mouse_pos.x += 75
		mouse_pos.y += 75
		self.position.x = int(mouse_pos.x / 150) * 150
		self.position.y = int(mouse_pos.y / 150) * 150
	else:
		print("out")
		self.position = orig_pos

func _physics_process(_delta):
	mouse_pos = get_global_mouse_position()
	if Input.is_action_just_pressed("left_mouse_button"):
		var abs_x = _abs_value(mouse_pos.x - self.position.x)
		var abs_y = _abs_value(mouse_pos.y - self.position.y)
		if abs_x < texture_size / 3 && abs_y < texture_size / 3:
			orig_pos = self.position
			is_clicked_on_self = true
	if Input.is_action_pressed("left_mouse_button") && is_clicked_on_self:
		self.position = mouse_pos
	if Input.is_action_just_released("left_mouse_button") && is_clicked_on_self:
		_drop_piece()
		is_clicked_on_self = false
	pass
```

![效果](:2022-06-04-07.gif)

## $ 01 / 03 饼

至此，第一版本已经完成，但仍旧有许多问题，以后版本会修复

[下一版](http://mhyc.tech/zh/2022-06-05-chess-how-02.html)
