<!-- readme -->

<!-- outline-start -->

关于第一期的一些优化，包括重写棋盘，棋子，添加Global脚本等

<!-- outline-end -->

直接开始

## $ 02 / 01 Re:棋盘

在[Godot官方文档——你的第一个2D游戏:游戏主场景部分:主场景脚本](https://docs.godotengine.org/zh_CN/stable/getting_started/first_2d_game/05.the_main_game_scene.html#main-script)中找到了答案，这个例子在场景四周随即生存怪物，与我们自动生成棋子的需求相似，看看他们怎么做的

```
exdents Node2D

export(PackedScene) var mob_scene
#将 Mob.tscn 从“文件系统”面板拖放到 Mob 属性里    或    单击“[空]”旁边的下拉箭头按钮，选择“加载”，选择 Mob.tscn

func _create_mob():
	var new_mob = mob_scene.instance()
	add_child(new_mob)
	#这里我直接运行报错，根据保存信息修改为calldeferred("add_child", new_mob)
	#到这里mob已经出现在场景上了，视作子节点存在
	new_mob.position = Vector2(0.0, 0.0)
	#可以这样设置新mob的属性，也可以直接访问字节点的脚本内变量
```

说几点：
1. GDScript面向对象（大概。。。），所以可以自行了解一点面向对象的基本思想，以后有帮助。在这里，instance就是创建实例，你可以理解为原本的mob_scene是一个模板，无法使用，只有通过instance创建实例以后才是一个真正的mob，此外，创建多个mob以后各自的属性及脚步各自独立存在，互不影响
2. 创建了new_mob以后，如果之后想要再访问此mob，须将变量储存起来，推荐使用列表
（以上总结自[GodoterCN上我的提问](https://godoter.cn/d/181-ru-he-shi-yong-dai-ma-chuang-jian-zi-jie-dian)）

另外，介绍AnimatedSprite，这个节点类似scratch的姿态类似，可以更换材质做出动画

创建一个新的场景，起名BoardBlock，创建一个AnimatedSprite作为根节点，命名为 `Block` ，为Block新建SpriteFrames

创建两个150*150的材质，名为 `board-dark.png` 和 `board-light.png`

将两个材质添加进去，注意分别添加到两个动画里，分别命名为  `dark` 和 `light`

使用for循环创建棋盘格子
（其实使用tile也可以，但是我希望后续可以添加一次放大淡入的漂亮动画）

主场景根节点添加以下代码:
```
exdents Node2D

export(PackedScene) var board_scene  # 记得赋值，不然报null

func _prepare_board():
	for i in range(8):
		for j in range(8):
			var board = board_scene.instance()
			call_deferred("add_child", board)
			if(i % 2 == 0 && j % 2 == 0 || i % 2 == 1 && j % 2 == 1):
				block.play("light")
			else:
				block.play("dark")
			block.position.x = 150 * j + 150
			block.position.y = 150 * i + 150

func _ready():
	_prepare_board()
	pass
```

这次我们摒弃了上次的棋盘位置-75,因为这样会导致当棋子位于棋盘左上侧出界难以纠正

![效果](:2022-06-05-01.png)


## $ 02 / 02 小优化

项目设置中创建一个全局脚本，命名为Global（全球），用于储存一些常量  
例如 `block_size` 表示棋子格子的材质大小，赋值为150

## $ 02 / 02 Re:棋子

和棋盘格子一样，创建场景命名为Piece，AnimatedSprite，SpriteFrames，附加之前编写的棋子脚步

在根节点Node2D上附加脚步，使用for循环创建棋子：

```
```

## 啊呀

看来这篇教程烂尾了，如果你希望完成这个项目，可以尝试自己摸索，MHYC也接受提问