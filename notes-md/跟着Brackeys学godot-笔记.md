## 1. 准备工作

首先要做的事是——创建文件夹
![](brackers-godot/cb380b768442a65bef809ccdf413e9c3.png)
这样才能井然有序的进行制作

assets——放资产，字体，图片，音效等等
scenes——就是放场景的
scripts——就是放脚本的

## 2. 基本概念

- 总之就是，节点（node）构成godot内的游戏世界的万物
- 但是呢需要用场景（scene）来把一些基本的东西分开整理好
	- 比如主角可以由很多节点构成，然后单独放入一个场景里
	- 地图也有很多不同的场景，那么也可以单独把每个用节点制作的地图用场景（scene）分开
	- 关卡（level）的载体当然也是场景，也是由节点组成
- 嵌套（mesting）：就是场景之间的嵌套
	- 比如主角场景，地图场景，硬币场景这仨个都放在一个关卡场景里
- 然后场景也可以重复使用，比如某个关卡场景需要很多个硬币场景
- 场景树（scene tree）：也就是场景之间的嵌套关系构成的树状结构
	- ![](brackers-godot/7cbe41f01f16bb1224344e80f08cd76b.png)
	- 上边会有一个最开始的节点，称为根节点（root）


## 3. 动手吧

- 创建一个node节点并命名为Game
![](brackers-godot/9d8289838af558263df4bf8eb8cdd03a.png)
然后ctrl+s保存在scenes里


- 然后点播放键运行这个项目，并设置主场景为Game（选择当前就行了）
![](brackers-godot/a50bbb992fd0e2475ea80c7c558e5316.png)

接下来我们来制作主角

- 点击加号创建场景![](brackers-godot/458265d411a66a43ae4dcd3fd57c5d53.png)
ctrl+a找到characterBody2D并创建

然后我们需要给他一个视觉表现，也就是添加一个图片节点（sprite2D，这个sprite是图片的意思），但这是静态的没什么意思，那就添加一个动态的动画节点（AnimatedSprite2D）

也就是添加一个这个子节点![](brackers-godot/c4f1359af91f72ae2bd840f7ee563b20.png)

然后点击这个animatedsprite2d节点保证是亮着的，然后在右侧的属性里找到spriteframes![](brackers-godot/70b2a33aedff11810d4b76af22e51590.png)
添加一个新的spriteframes![](brackers-godot/fb0088d7fdbed82851e890214e22dd60.png)

单击一下这个![](brackers-godot/cb6f98739749c477f00c6c54b2d96cf9.png)

- 再点一下这个![](brackers-godot/528c886fb72fa283cb52afebbf967546.png)
	这是用来导入人物的立绘表的
	![](brackers-godot/da4c00e00b1cd055a8b6181f4a12c3f1.png)- 双击这个knight,它长这样![](brackers-godot/1344c96689d4849fac6713d099a1c3e9.png)
- 但是很明显这个没框住单个人物，那么在这里![](brackers-godot/04424a8dbdc9f9f6c6547d763c34a47e.png)改成8就行了
	![](brackers-godot/0b19b5069c0b2bc7d967df7b205b0d33.png)
这样就对了

IDLE——待机动画

按照这个顺序选择图片，那么人物会照这个顺序动![](brackers-godot/1110bd4884fd43e1f6e65298259e4a9e.png)

按F聚焦中心，可以看到我们的角色了![](brackers-godot/0b855a419b8913935a54d4e8beba434e.png)

但是发现它很糊，那么我们需要关闭纹理平滑

在项目设置里找到纹理改成nearest就行![](brackers-godot/13b2d482ab8a90fec870da2eef66d611.png)

- 这样就好多了，可以点击这里![](brackers-godot/b2ee8680d9979b05d48297d01fcb205a.png)播放看看

- ![](brackers-godot/190c80c20643bd0e0ff9f353f8cbd086.png)这里可以改成10 fps，就会变化的更快

- ![](brackers-godot/79cb79dac5d17621a092f75c7467c775.png)这里名字改成待机动画（idle）

- 然后这里点一下![](brackers-godot/71f98a66316a611fcfddf184defd6203.png)
- 稍微移动一下人物![](brackers-godot/393e6554ef4cd501586d93a85cadec81.png)
- 让他站在线上


但是捏注意到上边有一个![](brackers-godot/e6e90d9083284d198fabab09f822cf46.png)

点一下看看![](brackers-godot/7b780f3964c9afa93fbb9a1d0749b259.png)

很明确，我们要加一个节点来做参与物理碰撞的检测形状

那就加一个![](brackers-godot/6e1d9a0e98d6fdf38185e82f2bf1bab0.png)


新建圆形![](brackers-godot/513c754e998ee2f39c9a9276a898438d.png)

然后调整一下![](brackers-godot/c35c9c97ddcfd6af4cb7dfbe31c6c464.png)

经验——一般来说不需要完美覆盖人物，甚至只需要人物图像包含整个形状就行

根节点改成player然后保存到scenes文件夹里![](brackers-godot/ac3906973ceb7fb74ce487379b45a39b.png)


回到Game场景里把player拖进去![](brackers-godot/4640d7a11a5754e5b51b71898f4947ef.png)


然后，需要有一个摄像机，来控制游戏显示的东西
添加一个camera2D节点![](brackers-godot/3d31f569fc611437a00321361df7fb79.png)
记得要放在Game下边，不是player下边

然后我们就能看到这个相机的尺寸了![](brackers-godot/243eb6bad1b70a5802131387ceb39b2f.png)

在右边改成4 * 4的就行![](brackers-godot/eccd5a207515065d1a51bfa7cde00856.png)

然后把相机中心拖到player上![](brackers-godot/4ce2fad0420b873ed1e6825dd1fba672.png)

播放试试，ok没问题

## 4. 让人物动起来

回到player场景，在player节点上新建一个脚本，记得放在scripts里，当然我们使用模板文件就行![](brackers-godot/179e0eb686ee770c0ee721797683502d.png)

但是现在我们播放这个场景，角色就会掉下去，因为这个角色下边啥也没有嘛

我们在Game场景里加一个staticbody2D（2D静态物体）节点，当然，别忘了碰撞形状节点![](brackers-godot/79365d699e1430764c31722173201228.png)

然后创建一个![](brackers-godot/9f72b7d1d24979227ea67f1a31d5b88d.png)这个世界边界图形

然后点击这个staticbody节点切换到移动模式移动一下位置到玩家下边![](brackers-godot/ea167de7183d4ba689742ff5d9c45588.png)
注意别只移动collisionshape2D节点。

播放看看效果，ok

但是移动太快了，那就修改一下脚本吧
速度和跳跃速度改成这样![](brackers-godot/437ceb1d74288dbf9c33b3a6caf86ec1.png)

就正常了

## 5. 创建世界

现在我们把这个静态物体节点删了，还是得有个样子的环境才行嘛

然后添加tilemapplayer，别添加tilemap因为![](brackers-godot/ce82564f651d750eff2b1317214650bb.png)

介绍TILES（瓷砖）世界的概念：就是在一个平面网格中给每一个小网格添加图块来构建2D世界
这样的
![](brackers-godot/e8656d0ab2f2a4c3ccc0af9b5649047e.png)

然后这些不同的图块自然也集合在同一张图中，成为TILESET![](brackers-godot/1f5525348d7e956b4132bec812d12bf1.png)

就和前边的人物一样的

 那么这个tilemapplayer节点就是用来构建这个tileworld的

首先像之前配置人物那样，新建一个![](brackers-godot/a06fbfd461d2356a2aab556941c10251.png)
然后检查一下tile的尺寸![](brackers-godot/7b95dce241a18f79d67d0a2130ba4217.png)
和我们的素材中的每一个tile尺寸大小时不时一致的，不一样要调整
然后呢，要先在下边载入tileset![](brackers-godot/cbaa01bf8b4f27759c48a3e5bba6fe1b.png)

在左边的资源管理器里拖进来就行![](brackers-godot/1b9c4e8ae9b0f10b8f2dde3de1437444.png)![](brackers-godot/390dc1e0eee46dcee79825a2e08709f2.png)

点击是，就欧克

然后捏，把窗口放大，处理一下这个tileset
![](brackers-godot/6498aa94f1644285029e453023048ef8.png)

处理啥呢，要把它错误区分的图块修正
比如![](brackers-godot/c04f8f84db92d958323bd6e9970ee3f4.png)这个本来是一个树的图块，它砍成了3个网格
那我们就点击橡皮擦![](brackers-godot/1d423b7af38f002081e2f75fb2e71466.png)

然后单击这些块![](brackers-godot/775354cf2304731a9181615de101ef96.png)让他们变灰
然后再点一下橡皮擦![](brackers-godot/2599c21e6a0b5dc311839bf4fd307ae0.png)退出擦除模式

然后是从一个合适的格子开始，按住shift同时鼠标单击并拖到覆盖完这个图块的最后一个格子

然后就行了![](brackers-godot/f58fc7d862d37a2410ad7a634305be63.png)
这就显示一个整体的图块了

呃呃，好像就是三个格子就可以了，别动。。。。。这个可以设计不同高度的树木图块。。

按ctrl+z撤回把

但是把这个搞一下![](brackers-godot/b8126e372acbfc28d8b3da9f024be331.png)


接下来点击tileset旁边的tilemap开始拼图

确保这俩按钮是选择上的![](brackers-godot/5f29fdc2616a251d7508d34e3eaafe8b.png)

我稍微微调了下这个tilemapplayer的位置![](brackers-godot/d0360e6c3510866684c71e7bfcc332ce.png)

ok，然后呢，在下方左键单击选中一个图块/tile，也可以按住左键点击拖动选中多个图款然后在屏幕上的格子中铺图块吧

左键填充格子，右键删除格子中的图块，也可以长按左键填充，长按右键删除

效果如下
![](brackers-godot/42b7c7434488804f1b11675ea016ee1d.png)

再说一下![](brackers-godot/9686808381247ccaffaf3ea557050c84.png)这个五个功能中，前一个是选择功能可以用来移动tiles，后边都是创建tiles的方式，单击，直线，矩形，油漆桶，
油漆桶是这个效果![](brackers-godot/efc928b8e357b2934629a0286c2567cd.png)

然后捏，可以加一些装饰，巧妙用一下这些素材

这样
![](brackers-godot/62cfe465dedddf19040ae463e45c4718.png)

做完了，别着急运行这个场景，毕竟和之前一样，这些tiles都没有物理层，主角还是会掉下去的

添加物理层的方式：
先找到物理层
![](brackers-godot/3abb13082fcd6abad29d442aeb0d49d5.png)
然后添加元素，那就加好了一个物理形状

再在下边的tileset，选择绘制![](brackers-godot/80f657b9c7c72a98ca3ec711abefc8c9.png)
然后选择属性里的物理层就看到了
![](brackers-godot/0c9a4a88049c94dfeecd1df2edd3c40f.png)

然后单击选择（当然可以拖动选择）你想让玩家与其产生碰撞的图块
F键可以切换到选择模式，C键可以切换到取消选择模式

但是对于绳索![](brackers-godot/796362d21498ec5cb4f0356e8d6cfe99.png)我们只需要碰到那么一点而不是整个方块，那么就可以在左边这里编辑整个物理层形状
![](brackers-godot/af23c2b195a841a43c1ebd0222d273f4.png)
通过添加顶点，移动顶点调整到合适的形状，然后再单击选择右边的图块就可以恰好覆盖了
![](brackers-godot/c77672726101c7820524cb0cf9a987b7.png)
效果是
![](brackers-godot/024a9924708e2c3a5a00d51e5121dc8b.png)这样子

![](brackers-godot/08ac9093a12b247617b23e01d88ec904.png)
哦对了，可以在这里把形状变回正方形
![](brackers-godot/fd992704436177e163f93bffa5119665.png)

然后把这个map节点放到最上边
![](brackers-godot/3958e4ec8fdfc79a7aa5dcce309ce57d.png)
然后来运行一下场景试试，ok没问题，但是摄像机不跟随主角移动。

解决办法是把camera节点移动到player下边，直接拖动就行
![](brackers-godot/0bf67bf5b58e6f053eb0a0201fd78a99.png)
然后打开这个相机位置平滑
![](brackers-godot/e6895b27d9cc426917d5cb55131d5403.png)


这下有感觉了，但是player掉下去后不会重新开始，需要改改

## 6. 移动平台

这可以增加游戏的可玩性

那么这种平台自然需要一个新的场景来构建

在新的场景里我们添加animatablebody2D节点
![](brackers-godot/5c8ee7c36a444371861fba3351566239.png)

然后添加一个sprite2D子节点作为立绘

然后直接把platforms.png拖进texture就行

![](brackers-godot/6f12782546a7c4cb5678c058f72f62a1.png)

在2D视图里我们就能看到了
![](brackers-godot/53e1093a4fe1b164270bc775505144cf.png)

这么多肯定不是一起呈现，所以我们进行一下裁剪
把这个region的enabled打开
![](brackers-godot/86df3043354095a2b7d792d4300ce29f.png)

然后点击编辑
![](brackers-godot/5d4bfac5eebef3c933e731b7d8f17a38.png)
再编辑就行了![](brackers-godot/0bc208f85c49783f62c22bfc0295ad61.png)
记得把上边的吸附模式改为像素吸附

调整完![](brackers-godot/297756b6be4f38d983379db8477315cc.png)关了就行

![](brackers-godot/f6c9a5cd634ac59c4f94a0a7f83d54f6.png)这里说明我们还得加一个collisionshape2D，加长方形的就是了

![](brackers-godot/ab22985f010b175322a6ff526ea56656.png)这样就行

养成好习惯，命名
![](brackers-godot/3885183767964b676ea0cbb845fa62fd.png)

保存在场景里就好
切换到Game场景里

我们直接拖过来
![](brackers-godot/b7621ac647e49647eafcd1cf7e924ac4.png)

注意一下![](brackers-godot/8ed96ea056157153bb996aab6cc35f00.png)==一定要在根节点下啊啊啊==
不然会导致整个平台跟着玩家动

运行一下，ok没问题

但是捏，这个平台我们得能从下方跳上来

所以修改一下吧

回到platform场景，点击collisionshape2D节点，把这个单向碰撞
![](brackers-godot/60c4ec74c1d80a26d27590e3406d3d24.png)

但是呢，我们是从平台的这个立绘的背后跳上来的，而不是正面
![](brackers-godot/bfb1fbb50b4cfd97114f37d94960b853.png)

这个原因呢是godot引擎的渲染机制，就像下边这样
![](brackers-godot/27172a2406f440af9100a563c0af69a5.png)
意思就是平台这个立绘比人物立绘先渲染

- 所以解决办法是
	- 要么我们把![](brackers-godot/c51cbbc0ae20b091d1d375d5bc10eb56.png)这俩顺序调换一下
	- 要么我们直接就把z轴改了，这样不管先后渲染都有明确的视觉呈现关系
		- 回到player场景，把![](brackers-godot/7ef1eccf195f81a8bad173be26c20e77.png)这里改成5就行了

我们在另一个地方放平台作一个移动平台吧
![](brackers-godot/82bbe9661ae016b06feef470a738525d.png)

然后我们在Game场景下，对这个platform节点添加animationplayer子节点
![](brackers-godot/1a7296577f29ad036a4001a0615f59e3.png)

![](brackers-godot/23788252645b60d8fd51a82e997e0970.png)

然后在下边![](brackers-godot/b19b9f5fb61d5586e114f384b45f7a51.png)
新建一个move动画
![](brackers-godot/669caaa9dd5fbeea4ece7eb92873a5f5.png)

然后点击platform2节点，在右边的node的transform属性里
![](brackers-godot/3d5a6eab17438ba823c2f6d73e73a8b4.png)
这个就是我们的k帧用的按钮

调整一下第0帧时刻的位置![](brackers-godot/cd96cf329504a9337f4e8253c6e78e98.png)

然后如果发现时间线界面不见了，要先点这个![](brackers-godot/3a6d2a735496c962d4ecb1d30d8a0fc3.png)再
在底下
![](brackers-godot/4490b1bef98d9f094dbb9c3e778242b7.png)
点这个动画就出现了

单击刚才说的那个钥匙按钮
![](brackers-godot/005ab8ea9a7a5a00aab6560a182811b9.png)
点击创建就可以了
这样就出现了第一个关键帧
![](brackers-godot/4de8494411ce80372658c517855f026f.png)

这里我们在这里调整到第1秒
![](brackers-godot/1cf1447c1f9f28434c98173662db809d.png)

然后再调整平台的位置（可以按住shift键进行平行位移，或者直接改这个transform里的position的数值）
![](brackers-godot/6f25431bb27eb3123c88e67ef8a47c65.png)
再点一下钥匙按钮就创建了第二个关键帧

![](brackers-godot/4d4870812944acdda040bcc7dae66816.png)
点这个就可以播放了，ok，效果可以
右边有一个循环按钮，点亮后再按播放就可以循环播放![](brackers-godot/714eafe26b2828891e5a3bd2d6c68127.png)

但是再点一次就会进入“pingpong”循环![](brackers-godot/194be448733fa9ad42a5b4acca279f98.png)
就是正着来和反着来

![](brackers-godot/69835df8e0d8730fed4f6d3d4bf82174.png)这里是动画总时长

所以，修改的时候记得要改这里要改

然后可以拖动关键帧![](brackers-godot/715d0f84ac61c78be751de21137099e0.png)

这样子就行

最后一步，把这个自动播放按钮点上![](brackers-godot/c8acdcb2e77d542b6b45aea028242f68.png)

就可以保存运行看看了


## 一个硬硬的东西——coin

新建一个场景

我们需要一个Area2D节点来检测碰撞物体并做出变化

同样的，静态的图片选择sprite2D，动态变化的要选择animatedsprite2D
选择animatedsprite2D

![](brackers-godot/e592c8df0cf38d9d206bc5fbecc1ce44.png)

和之前操作一样

记得调整一下网格大小 ![](brackers-godot/14c68f867345c71952780c7c9740314a.png)

这里改成10 fps![](brackers-godot/67b42662711f457144abc680d4dc06b7.png)

 记得都点上![](brackers-godot/0d2311e103a56d6cc0e7e775c49665aa.png)

然后添加collisionshape2D，加个圆形

![](brackers-godot/2d3ed06bc3bbdaba045d11118278b3ac.png)

然后改个名
![](brackers-godot/c1baa27325317ace31c94360b2da60aa.png)

保存到场景（scenes）里

回到Game主场景里，像之前一样把coin拖到场景里就行，然后我们可以用ctrl+D来复制节点

随便放一下![](brackers-godot/c402b5963fda6128b21a4b59775c59fa.png)

保存并运行一下，ok

接下来要给硬币加上一些脚本，让主角能获取硬币

回到coin场景，我们来添加脚本
![](brackers-godot/c6c307f52e161b8c7dd5cd003577c456.png)

设置如下
![](brackers-godot/c33f4743d8f61ae8602e8a95c5a2bd7e.png)

然后呢，删除这些多余的东西
![](brackers-godot/69ad980e5f8ed7cd4826270827ffe73d.png)

我们需要用到特定的信号（signal）来触发硬币脚本运行

点击area2D再在右边点击“节点”就可以看到很多信号，这里我们需要body entered信号
![](brackers-godot/de50cd7abd7401c413124932a2e657b2.png)
双击然后创建
![](brackers-godot/51309785dbb4c68385e287b873f91dfe.png)
就有了这个函数了

测试一下
![](brackers-godot/6201320c9e83d530680fc6d79b30c8d1.png)

运行，ok
![](brackers-godot/bda3009823349a58d25f803794bb4037.png)


但是问题来了，此时任意物体进入这个硬币的检测区域都会发送信号并执行print语句，这并不是我们想要的，我们只要当玩家进入硬币区域才会执行print语句

解决办法是
- 1是写一个判断代码，判断进入检测的物体是否为角色，进而决定是否执行print代码
- 2是可以把玩家放在另一个物理图层上
	- 介绍一下这俩
		- 这个是指可以扫描的物理层有哪些![](brackers-godot/2da088d0c86e06e0a0c6cf7bceeb6e70.png)
		- 这里是指这个节点存在于哪些物理层中![](brackers-godot/258b0b04bc0f7f13b9e2c6f134dc2f17.png)
	- 这里的物理图层指的是玩家根节点上的collisionobject2D属性里的图层
	- ![](brackers-godot/8aca0cdea36e3c1db6ba7417fcd96fc7.png)
	- 我们把Layer里的1换成2![](brackers-godot/0e3cfe33095659703f714013733ac82f.png)这需要我们先点一下1再点亮2
	- 再来到coin场景里，把mask改成这个![](brackers-godot/8255346e7fb07f5f645279c7acebb7c5.png)
	- 这样就行了


然后，我们希望玩家碰到coin后，coin就会消失

那么加一个queue_free()函数——这是一个用来清除节点的函数
![](brackers-godot/a9adc52b2898b428ae59e2edc25861e0.png)
就实现了

介绍：![](brackers-godot/4f6976d654fc09d3e7cb3bb507d8c216.png)


## 7. 欸，你怎么私了——死亡机制

这里首先设置一下相机，让相机不会跟着主角一起掉下去

这里我们在相机的limit属性里修改即可
![](brackers-godot/d2a050f495e967a0c74f36d3b80f1565.png)

在上边找到尺子按钮（也就是测量模式）![](brackers-godot/4770f865f269d2111bc5aacba38ad7d6.png)
并选择

然后我们量一下，记得要从这个坐标轴先开始量
![](brackers-godot/b1e20a18f35df81746381afde44c3740.png)

差不多是90，也就是说底部（buttom）最大限度是90
![](brackers-godot/e4ad8b8ad326dc0052c3b40c3085aa89.png)
顺便把这个平滑开了
![](brackers-godot/2550f1f936d30f337855ac1575360965.png)

这样就不会一直下去了![](brackers-godot/dde2945fffbb6a4e59b4303faaddf808.png)

 接下来，让我们创建一个新场景，我们需要一个检测区域
创建area2D节点，记得把collisionobject2D属性的mask改成2，毕竟我们的主角现在存在于第二个物理层

改为killzone，这是一个我们想要复用的场景，就是说，我们要需要在这个节点下创建不同形状的碰撞区域（collisionshape2D节点）
![](brackers-godot/4dfe4ef272b05b657f1bf60881e4938d.png)

回到game场景，我们可以点击
![](brackers-godot/7da7c7cc546a7e079dbb8064382d259e.png)
来选择这个场景（和拖进来一样的）

记得要让他在根节点的下边，而不是子节点的下边

 ok，在killzone节点下新建一个collisionshape2D节点
 ![](brackers-godot/ef769ebc402e32dc3d93e571c86c8499.png)
 创建这个

然后点击killzone节点调整一下位置（反复强调）
![](brackers-godot/7ba581d106cc5c8a706c81f87605a803.png)
这样子，别担心，这个是一个无限长平面。

ok，碰撞区域有了，我们还需要脚本来判断主角是否死了

回到killzone场景，新建一个脚本，这次选择空模板的脚本吧，记得放在scripts文件夹里
![](brackers-godot/7690391ad9fe7d23df4747ac26f5aa27.png)

然后和前边一样，选择根节点，然后在右边的信号里找到 body entered信号双击创建
![](brackers-godot/ab403fe625b1760f68d5dc2ec197a764.png)

然后写上print
![](brackers-godot/63cf73393f67b8094dfb31f067a934bf.png)

ok，这下有提示了，我们还需要一个倒计时来提示玩家多久重启游戏

需要用计时器（Timer节点）节点，那就创建一个
![](brackers-godot/6756241325a5b2b181abcb5a15a5f7e3.png)
把计时的时间改短一点
![](brackers-godot/06fe3b0ba356603492773ffe11359e81.png)


然后我们需要在脚本中引用它，怎么办呢？你不知道引用的语句，没事
先点击这个节点然后拖拽到**脚本界面**，先别松手，按ctrl再松手

![](brackers-godot/478601643e8d857bc2d7476461b75e2a.png)
就有了
如果没按ctrl就会是
![](brackers-godot/a53171dcd835c89807e367fa1c9280e1.png)
这是计时器节点的路径，直接这么写没用，还会报错

然后我们写一下
![](brackers-godot/5bfffb53a62edd57ba428147488942e7.png)

然后计时器启动了就应该会发出信号，啥呢，timeout信号

所以接下来我们要创建这个信号
![](brackers-godot/d7e7680765cc4214c970d73e817ef7bc.png)
![](brackers-godot/db95babe50a59ee33d00f4931018f70b.png)
这个函数会在计时结束时触发执行

根据前边讲的渲染顺序，我们需要用场景树
![](brackers-godot/8db2d3297bf390a313e7a8121ccce7cc.png)
- 解释：
	- ![](brackers-godot/cf64618ae991217456b37f22902717c5.png)
	- ![](brackers-godot/8ffe56f42b710581667641c7777fc395.png)


## 环境设计2.0

虽然复用场景已然帮我们整洁了主场景的节点
![](brackers-godot/6eb695b65e510cb8c8161a8bde75b6aa.png)

但是太多了

有什么办法可以再整理整理，归归类呢
在场景栏里我们只能添加节点，但是根据节点的父子关系，我们可以将节点当作文件夹来使用
比如Node节点

让我们整理一下
![](brackers-godot/3631845f42cdf5b41e4cf33cd4a7432c.png)
ok，好多了

再优化一下世界
![](brackers-godot/25752386333dc587696a331c7cca944c.png)

ok，没有背景感觉怪怪的，那就再加一个tilemaplayer
原因：![](brackers-godot/f04e9f8658bc06e54c07977470673c82.png)

和之前同样的操作
不过这次不用设置物理层
需要把z轴调一下
![](brackers-godot/f8d7f8b881c4dd1ae6a1411a5f6fa1f7.png)
负的就行
效果
![](brackers-godot/e9f4ccba0b127bd8f3e36288c3838538.png)
然后，我们来保存运行一下，ok没问题


## Enemy——敌人

有个可攻击对象会很爽

由于此处不需要像主角那样有一个物理碰撞的效果（比如主角不能穿过敌人，但是现在不需要）
那就只需要一个普通的2D节点——Node2D节点就行了

新建场景，创建根节点，然后这个敌人也得是动态的吧，那就加一个动画图片节点——animatedsprite2D
![](brackers-godot/4ef509a8ba5617b9e2fd853f3d390fe4.png)

和前边一样，新建spriteframes，然后以精灵表（其实就是网格切割为小图块）的方式导入合图（包含所有立绘状态的图）
![](brackers-godot/466404652af9923ace087a29523acbb7.png)
调整一下![](brackers-godot/df8434b369e9b36ef5acd5ad2d543634.png)
![](brackers-godot/057c547947e520ade5c6de295c852d18.png)
按顺序导入吧
第一行是怪物苏醒
第二行是待机
第三行是收到攻击
![](brackers-godot/c4a4e5ebe3e57f0494a9004c8aedcb13.png)改改设置
待机动画就做好了，现在我们需要利用之前创建的killzone来给敌人设置死亡机制

![](brackers-godot/47515c48c99779744bdb3664b600fbd1.png)
点这里实例化这个killzone场景，然后添加一个collisionshape2d节点，新建一个形状覆盖住敌人（按住alt键可以居中调整形状）

![](brackers-godot/72fcffc87e50f5d371a59ff55ea54b8c.png)
像这样。

这是一个slime（史莱姆）
![](brackers-godot/cf79e29d2e9f39f9490d8cf3d59c0553.png)
然后改名保存到场景里

然后再game场景里拖入这个怪物吧
![](brackers-godot/cf2e485e2825619ed4c789d0a2dd6ac9.png)

运行试试看，ok，确实有效果

ok，接下来让我们的史莱姆移动起来
这里可以通过动画节点来做到移动，但是，我们想让它在不同距离的墙里有同样的左右移动行为，那么就需要脚本了

那么就新建脚本吧，记得放在scripts文件夹里

![](brackers-godot/f3f02e42ded8680074cd5bd3cd058809.png)把ready函数删了，留个这个

一些原理介绍：
- ready函数只会在进入场景后的开始执行一次，但是之后就不会了![](brackers-godot/ea01f78ba21c248307e040019ae6d5d4.png)
- 而process顾名思义就是在游戏运行的每一帧都会执行![](brackers-godot/ddeef486144c27fe579008972e3ee197.png)

这就适合我们做一些关于敌人自动移动的操作

然后呢这里有个小知识，游戏内的帧率众所周知是非固定的，那么这个process函数执行的速度也是不固定的。

这里呢写脚本前再需要一个概念——射线投射节点（raycast2D）——发射不可见的射线来探测障碍物距离

![](brackers-godot/07f8ea5814b1d5d41c2a8b5cb06966ff.png)

![](brackers-godot/446f05b89ec5cacf835605a36fe4e917.png)
这样子，让我们调整一下
![](brackers-godot/b2095d18d74812af81f22eb0cec67ba2.png)
由于之前没把slime放在线上，这里调整一下

ok这是一个右侧射线，现在我们还要一个左侧射线
![](brackers-godot/1969d344d075baf4720e4145c808cf46.png)
缩进去一点，这样就对了，再改个名
![](brackers-godot/51e6837f19b1b657aae2502629517f78.png)

然后来到脚本界面，像之前做的那样，ctrl拖入这两个节点
![](brackers-godot/04a3cd76a75ecef6553f0a51744d078e.png)

现在开始写脚本
![](brackers-godot/1b24226d2f96d7aa411afc84405f6d6b.png)
- 解释：
	- @onready 是一个注解，表示这些变量将在节点树准备好后自动初始化。
	- ray_cast_2_dright 和 ray_cast_2_dleft 是两个 RayCast2D 节点的引用，分别指向场景中的 RayCast2Dright 和 RayCast2Dleft 节点。
	- RayCast2D 用于检测指定方向上的碰撞。
	- SPEED 是敌人的移动速度，单位是像素/秒。
	- direction 是敌人的移动方向，1 表示向右移动，-1 表示向左移动。
	- - `_process` 函数每帧都会被调用一次，`delta` 参数表示从上一帧到当前帧的时间间隔（以秒为单位）。
	- 在每一帧中，脚本会检查 ray_cast_2_dright 和 ray_cast_2_dleft 是否检测到碰撞。
		- 如果 ray_cast_2_dright 检测到碰撞（即右边有障碍物），则将 direction 设置为 -1，使敌人向左移动。
		- 如果 ray_cast_2_dleft 检测到碰撞（即左边有障碍物），则将 direction 设置为 1，使敌人向右移动。
	- 最后，根据 `direction` 和 `SPEED` 更新敌人的位置：
	    - `position.x` 是敌人的X坐标。
	    - `direction * SPEED * delta` 计算出每帧应该移动的距离。
	    - `position.x += direction * SPEED * delta` ==更新敌人的X坐标，使其向左或向右移动，这是一个通用公式。==

然后呢，敌人移动方向变了，自然立绘也要翻转
那就需要在脚本中对animatedshape2D节点的flip h属性做控制
![](brackers-godot/838bcdc9b96c657fd936aad685c650b4.png)

当然不能直接修改这个flip h，而是先引用这个animatedshape2D节点
![](brackers-godot/8d48ebb6ea2a781c358e9aac775d9a35.png)
稍微改了下变量名

然后就可以想调用python方法那样来调用这个节点的属性

![](brackers-godot/d205bf110efc187b082ef06b93eed403.png)

这样就行了

## 更好的死亡，怎么会有人喜欢关注自己怎么似的

这可以通过改变游戏的时间尺度（时间流逝速度）来实现

来到killzone场景脚本加入这些代码
![](brackers-godot/75d98c9d7289bccdc384f6666900c015.png)
上下都调用修改了Engine的time_scale属性，一旦碰到就打印，然后把游戏时间尺度变慢，计时结束重启游戏前把时间尺度调回来，这样就可以了

接下来，我们再加入一些细节，比如
让主角进入killzone后直接失去物理层然后掉落

也就是清除物理层了，想起来之前做硬币时有个queue_free（）函数，那么就可以在这里使用
回到killzone场景脚本里，加入下边的代码
![](brackers-godot/92bbd675596fd7064b193c9807aaddb5.png)
这里的body就是这个killzone所接触的物体，也就是我们的player，这样就可以调用对应的物理层也就是collisionshape2D节点再调用queuefree方法就行了

## 更好的玩家——让我看看！（player的脚本里写的是啥）

首先区分以下process和physical process这两个函数
![](brackers-godot/07892eb2062b9536612f8337b88a2c5b.png)
前者是根据实际游戏运行帧数来执行对应代码的
而后者则是严格地在固定的帧数上以相同的时间间隔来执行代码的（一般是60帧/秒）

现在看看这个模板代码写了什么
![](brackers-godot/c6c1ddf33f5bc9380f91218f4dbc0d8e.png)

> [!NOTE] `_physics_process` 函数内部
>**重力处理**
如果玩家不在地面上（即没有接触地面），则应用重力。`get_gravity()` 返回当前世界的重力向量，乘以 `delta` 时间间隔后加到 `velocity` 上。
**跳跃处理**
检查是否刚刚按下跳跃键（默认为 `ui_accept`，通常是空格键或回车键）并且玩家在地面上。
如果满足条件，则将玩家的垂直速度设置为 `JUMP_VELOCITY`，使玩家向上跳跃。
**输入方向和移动处理**
`Input.get_axis("ui_left", "ui_right")` 获取水平输入轴的方向。`ui_left` 和 `ui_right` 是默认的输入动作名称，分别对应左移和右移。
如果检测到水平输入（`direction` 不为0），则将玩家的水平速度设置为 `direction * SPEED`。
如果没有检测到水平输入（`direction` 为0），则使用 `move_toward` 函数逐渐将水平速度减小到0，实现减速效果。
**移动和滑动**
`move_and_slide()` 是 `CharacterBody2D` 的一个方法，用于根据当前的速度 (`velocity`) 更新玩家的位置，并处理与地形的碰撞。这个方法会自动处理斜坡、墙壁等复杂地形。

其中
![](brackers-godot/48054e5e1e56031a7000fe232f5e62a8.png)
然后呢，这种通过按键绑定来执行动作的机制叫动作系统（action system），知道就行
接下来我们就可以修改一下输入映射

上边代码里有一些默认的输入映射
比如ui_accept,ui_right,ui_left就分别代表键盘的空格键，左方向键，右方向键。
当然我们也可以在
![](brackers-godot/3dbc57e165b309a1d7015a0cd411f3e3.png)
这里手动设置，先在“添加新动作”这一行里填写映射的名称，然后在下边每一个映射右边有个加号键就能添加了
效果
![](brackers-godot/17f96ed213bae4e93da0656747fa1023.png)

然后我们来改一改
![](brackers-godot/37cb4cf5dc8b7a731a5f6ceb996fb7a1.png)
就行了

然后是解决主角的立绘反转问题
同样，先ctrl拖入引用animatedshape2d节点
然后加一段判断语句就行了
![](brackers-godot/3d550371ef7e2f64da52522166f5de71.png)
注意，这里不要添加等于0的情况，否则会很怪的。

再给玩家添加一些不同状态下的动画吧

来到player场景在animatedshape2D添加两个新动作jump和run，并且我们在脚本中控制这三个动作动画的播放
![](brackers-godot/1d0c74179f6f9311b6e979744457bf01.png)
![](brackers-godot/ae84b78ef16c81e04db5f220b90b3b80.png)

就ok了


## 文字——你也不想让sensei知道你的哒教对象罢

其实展示文字的方式有很多，很灵活，这里介绍一下常用的一个节点
Label——![](brackers-godot/0386472d72b00b35d214c4771b3c0960.png)

在右边的检查器里就可以修改要显示的文字了，自然也可以移动
![](brackers-godot/6f0f3fc15bb08d0b41a4124710f98167.png)
![](brackers-godot/3a131033c409e24735248fdf20a16a12.png)
在这里可以拖入你的字体
![](brackers-godot/802c2ced0f311b5a215662950afb7612.png)
好多了

 这里的字体很特殊
 ![](brackers-godot/fad5be49b4fc3e47913477a56c85e0f9.png)
 当调整font size时记得改成8的倍数
![](brackers-godot/040f98392d19ace8ccf23027e49ef3c6.png)
颜色在这里改

效果
![](brackers-godot/148eb0ff08757e04f2f0a169859a3f89.png)

## 计分系统——你记得今早吃了多少卡路里吗？


很明显，需要代码存储与计算你的得分
需要文字来展示你的得分

新建一个node2D（）节点作为“游戏管理器”
![](brackers-godot/afe11f6bcc0de2e396d40fea7836f90a.png)

并创建脚本
![](brackers-godot/4821933b9a516a33b87113ee3ce2f8d2.png)
忘记改路径了也可以手动拖入对应文件夹
![](brackers-godot/7b6f729f4edd965f9792b33a958485ad.png)

 这里呢，由于这个GameManager节点只有一个，我们引用的时候会带着很多../../的东西，这是不好的习惯，所以我们右键它然后选择![](brackers-godot/9ee1f498551eabe6d5b4134b629a9d67.png)
 这样引用的时候就变成
![](brackers-godot/771c4ab467334b513c0e74d98c080e34.png)


那么我们在gamemanager脚本里写
![](brackers-godot/24931aabafd3228f61cc397cd262da1e.png)

然后在coin的脚本里写
![](brackers-godot/2e42126a9b2f0314df5cd710b648cb5c.png)

这样就完成了得分的计算与存储
接下来新建一个label放游戏管理器节点里
![](brackers-godot/ce9a7bfe2a49e11ec29e27cc68eca9c6.png)

然后在manager脚本里写这些代码（引用一下label）
![](brackers-godot/216f3eed26554e4486e1dd416a0f8fc2.png)

就有了![](brackers-godot/fee9a40686bc189ad59ff736d1d3b739.png)


## 音效——做游戏最灵魂的一步

需要Audiostreamplay节点
![](brackers-godot/1af78fcfbfa064d8cc556f602b084696.png)

把资产里的音乐拖过来
![](brackers-godot/d3c61bf466e45794e65b069cdcddea25.png)

启动自动播放
![](brackers-godot/f246248b589b6b87617a4b33c6f0c875.png)

然后双击这个
![](brackers-godot/452cae62ee771d630e0fb63ea7c28c82.png)

打开这个
![](brackers-godot/90e89e5206be933fe5e886990f8d3849.png)
然后重新导入

学习一下这个自带的音频编辑器

![](brackers-godot/f2177ee40477c71c4b6b92c2122f7444.png)

添加两个总线，一个是背景音乐，一个是音效
![](brackers-godot/35bd9b316963c9c9231f9c56b1b8f63d.png)
然后在右边把总线改为music
![](brackers-godot/355e66d0f3d6acbc885678a81a6fe1da.png)

再在编辑器里控制声音
![](brackers-godot/c971fae94fa6285af3847831d5a13664.png)
把背景音乐调小吧

问题来了，音乐会随着角色的死亡而重头开始，我们想让音乐自己放自己的，不受角色干扰
那么就可以把它设置为场景，然后在game场景中删掉它
![](brackers-godot/5bc76670b0639ebcffec403864a224e1.png)
直接拖入就行
![](brackers-godot/5a1610296905fe48767c4c65cbe83a07.png)

![](brackers-godot/b31ecace45d3e57d6917219b0493e4ce.png)

然后在项目设置里找到自动加载
![](brackers-godot/e10c51fa36c86861dbce2a75aa16fb62.png)
这样添加就解决了


然后添加硬币拾起音效
![](brackers-godot/88e86e7fcad7811b1146da0c20166b8d.png)
![](brackers-godot/698296dcd71628830e07a8583a8547c7.png)
![](brackers-godot/a547312d74a06988170dc7fa79d4e961.png)

这里有个问题，在脚本中，硬币被检测到时就会被删除，这个时间很短，甚至连让音效播放的机会都没有，所以这里有一个小技巧来解决这件事
- 步骤：
	- 创建一个animationplayer
	- 选中![](brackers-godot/25dc2a29110531215facca790b986348.png)
	- 来到这里并拖到1秒![](brackers-godot/a5851ae79c6f0aed363f1a8c8197c72a.png)
	- 在右边点这个![](brackers-godot/c5b407d71af4743ffaf60417d45e3fd8.png)
	- 然后![](brackers-godot/20147c5e4e756c65cbb00947aed11773.png)创建
	- 再拖到1秒![](brackers-godot/50d904b8e5d8a037c6590d475855c0f4.png)
	- 然后把![](brackers-godot/72aaf2a5c9b25f4101b88c41fa76cff3.png)点一下，不启用
	- 这样这个动画结束时硬币不可见
	- 接下来点这个![](brackers-godot/a6cba6890b08e8e16c01923fe08c5cee.png)
	- 然后![](brackers-godot/12e4c08d8ca41eb23df2457447f03996.png)点钥匙按钮
	- 然后再点启用
	- ![](brackers-godot/50e5c716600cb57a9a79632df307f37f.png)
	- ![](brackers-godot/17b5197b127f43bfe3277b4b87086e31.png)
	- 然后![](brackers-godot/be472fd544fa5fb3b8347a6bfa4e898f.png)
	- ![](brackers-godot/220b8f55a7eee4f4e02386c470930f82.png)
	- 最后![](brackers-godot/45a5c722071341b0157d7a5554e4d84d.png)
	-  然后呢回到newanimation
	- ![](brackers-godot/0a6bad8136e250244431ee105ccf6719.png)选择这些关键帧
	- ![](brackers-godot/68596f018cd42109f73167f44ac4eda5.png)拉到最开始
	- 然后![](brackers-godot/ab2579d9ae5b6850c34775cb5f8b464c.png)
	- ![](brackers-godot/fc0cada8502158f1149942b384e13fa9.png)
	- 选择coin节点
	- ![](brackers-godot/63f8bd7ff5bfccaef25c5e9691e6617a.png)在这里右键
	- ![](brackers-godot/c3f27f9afe92aff46de999bf1f6b97e4.png)
	- ![](brackers-godot/964725e1b4740e528b54330086a1b078.png)选择这个并打开
	- 这样就ok了
![](brackers-godot/fbd633623505222b74e6ff6ae3578472.png)![](brackers-godot/c3e77d8f08e735dcf6b493c9c6856b12.png)
改一下名字
回到coin脚本
改成这个代码
![](brackers-godot/88fd81f8ac71025710c39e51a7d8baaa.png)

觉得硬币消失时间太长可以改这里![](brackers-godot/c89e2c6d90e87ca4a9c341055dfbd30e.png)
拖一下就好了









