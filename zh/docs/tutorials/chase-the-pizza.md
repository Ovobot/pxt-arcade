# 披萨猎人

### ~button /#tutorial:/tutorials/chase-the-pizza

试试这个教程！

### ~

## Introduction @unplugged

![Game animation](/static/tutorials/chase-the-pizza.gif)

在本教程中，您将创建一个包含2个精灵的游戏, 一个`||sprites:玩家||` 精灵 和 一个`||sprites:披萨||` 精灵。游戏的目标是在时间用完之前尽可能多地吃披萨！ 每次玩家吃到披萨时，您都会获得积分并重新开始倒计时。

## 第 1 步

打开 `||scene:场景||` 栏，拖拽`||scene:设置背景颜色为||` 程序块，将其嵌入到 `||loops:当开机时||` 程序块。 点击**下一步** 继续。

```blocks
// @highlight
scene.setBackgroundColor(0)
```

## 第 2 步

在 `||scene:设置背景颜色为||` 程序块上，点击灰色椭圆区域，在打开的色板上点选喜欢的颜色作为背景色。 现在屏幕左侧的模拟器里，就能看到刚才设置的变化。

![Choose background color](/static/tutorials/chase-the-pizza/background-color.jpg)

## 第 3 步

打开`||sprites:精灵||` 栏，拖拽第一个程序块 `||variables:将 mySprite 设为||` 程序块，将其嵌入到 编程区 `||loops:当开机时|` 程序块内。 这将会为你的游戏，创建一个新的 `||sprites:Player||` 角色。

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(7)
// @highlight
mySprite = sprites.create(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, SpriteKind.Player)
```

## 第 4 步

要绘制你的`||sprites:Player||` 可以通过单击`||variables:将 mySprite 设为||` 程序块中的灰色矩形，打开精灵编辑器。 使用色板和设计工具在网格画布上绘制图像。 完工后单击 **完成** 按钮。

![Image editor](/static/tutorials/chase-the-pizza/image-editor.gif)

## 第 5 步

打开  `||controller:控制器||` 栏，拖拽程序块 `||controller:使用按键移动 mySprite||` 并吸附到  `||variables:将 mySprite 设为||` 程序块下方。 这将允许使用方向按键，移动场景里的 `||sprites:Player||` 角色。 完成后在游戏模拟器中试试。（也可以使用键盘上的"WASD"控制）

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(7)
mySprite = sprites.create(img`
. . . . . 5 5 5 5 5 5 . . . . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. 5 5 5 5 5 5 5 5 5 5 5 5 5 5 .
. 5 5 5 f f 5 5 5 5 f f 5 5 5 .
5 5 5 5 f f 5 5 5 5 f f 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 f 5 5 5 5 5 5 5 5 5 5 f 5 5
5 5 5 f 5 5 5 5 5 5 5 5 f 5 5 5
. 5 5 5 f 5 5 5 5 5 5 f 5 5 5 .
. 5 5 5 5 f f f f f f 5 5 5 5 .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . . . . 5 5 5 5 5 5 . . . . .
`, SpriteKind.Player)
// @highlight
controller.moveSprite(mySprite)
```

## 第 6 步

打开  `||sprites:精灵||` 栏，再次拖拽程序块  `||variables:将 mySprite2 设为||` 将其嵌入到 编程区`||loops:当开机时||` 的程序块里。 这将是我们游戏中的**披萨** 精灵。

```blocks
let mySprite: Sprite = null
let mySprite2: Sprite = null
scene.setBackgroundColor(7)
mySprite = sprites.create(img`
. . . . . 5 5 5 5 5 5 . . . . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. 5 5 5 5 5 5 5 5 5 5 5 5 5 5 .
. 5 5 5 f f 5 5 5 5 f f 5 5 5 .
5 5 5 5 f f 5 5 5 5 f f 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 f 5 5 5 5 5 5 5 5 5 5 f 5 5
5 5 5 f 5 5 5 5 5 5 5 5 f 5 5 5
. 5 5 5 f 5 5 5 5 5 5 f 5 5 5 .
. 5 5 5 5 f f f f f f 5 5 5 5 .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . . . . 5 5 5 5 5 5 . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
// @highlight
mySprite2 = sprites.create(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, SpriteKind.Player)
```

## 第 7 步

在 `||variables:将 mySprite2 设为||` 程序块，点击`||variables:mySprite2||` 打开菜单，并选择 `重命名变量...` 输入 `披萨` 作为新的精灵的名称并点击 **确定**.

![Rename mySprite2](/static/tutorials/chase-the-pizza/rename-mysprite2.gif)

## 第 8 步

在 `||variables:设置 披萨||` 程序块，点击`||sprites:Player||`打开精灵类别的设置菜单。选择`||sprites:Food||` 作为 `||variables:披萨||`  精灵的类别。

![Set sprite kind](/static/tutorials/chase-the-pizza/sprite-kind.jpg)

## 第 9 步

点击 `||variables:将 披萨 设为||`，然后选择  **图库** 。 滚动找到小披萨的图像 (或您喜欢的任意图像！) ，选中加载到图像编辑器后再点击完成按钮。

![Image gallery](/static/tutorials/chase-the-pizza/image-gallery.gif)

## 第 10 步

打开 `||sprites:精灵||`标签栏，拖拽程序块`||sprites:当 sprite 类型 与 otherSprite 类型 重叠||`到编程区(你可以把这个程序块放置任意位置)。

```blocks
// @highlight
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
	
})
```

## 第 11 步

在程序块`||sprites:当 sprite 类型 与 otherSprite 类型 重叠时||` ，点击程序块上，位于 `||variables:otherSprite||`类型 后面的，第二个`||sprites:Player||`，打开菜单。 选择类别为  `||sprites:Food||` 。

![Overlap sprite kind](/static/tutorials/chase-the-pizza/overlap-kind-sprite.png)

## 第 12 步

当我们的 `||sprites:Player||` 与精灵 `||variables:披萨||` 重叠的时候，让我们的游戏得分加一。 打开`||info:游戏信息||` 标签栏并拖拽程序块`||info:将得分值增加||` 到`||sprites:当 sprite 类型 与 otherSprite 类型 重叠时||` 的程序块内。

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    // @highlight
	info.changeScoreBy(1)
})
```

## 第 13 步

让我们将  `||variables:披萨||` 设置为在屏幕范围内随机出现。 打开 `||sprites:精灵||` 栏，拖拽程序块  `||sprites:设置 mySprite 的位置为||` ，将其嵌入到 编程区`||sprites:当 sprite 类型 与 otherSprite 类型 重叠时||` 的程序块里。

```blocks
let mySprite: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    // @highlight
    mySprite.setPosition(0, 0)
})
```

## 第 14 步

在 `||sprites:设置 mySprite 的位置为||` 程序块， 点击`||variables:mySprite||` 变量打开菜单，并选择你的精灵为`||variables:披萨||` 。

![Change mySprite to pizza](/static/tutorials/chase-the-pizza/sprite-position-rename.png)

## 第 15 步

打开  `||math:数学||` 栏，并拖拽两个 `||math:选取随机数||` 程序块到编程区。 将一个程序块拖到 `||sprites:设置 披萨 的位置为||` 上的 `x` 坐标，另一个则拖到 `y`坐标，以替代原来的`0` 。

```blocks
let pizza: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    pizza.setPosition(Math.randomRange(0, 10), Math.randomRange(0, 10))
})
```

## 第 16 步

Arcade的游戏屏幕是`160` 像素宽, and `120` 像素高。 在`||sprites:设置 披萨 的位置为||` 的第一个代表`x`坐标的`||math:选取随机数||` 程序块里， 将随机数的产生范围的最大值，由`10` 改为 **160**。 在 第二个代表 `y`坐标的`||math:选取随机数||` 程序块里， 将随机数的产生范围的最大值， 由`10` 改为**120**.

```blocks
let pizza: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    pizza.setPosition(Math.randomRange(0, 160), Math.randomRange(0, 120))
})
```

## 第 17 步

让我们每次都重新开始倒计时。打开 `||info:游戏信息||` 标签栏并拖拽程序块 `||info:开始倒计时||` 到`||sprites:当 sprite 类型 与 otherSprite 类型 重叠时||` 的程序块内。

```blocks
let pizza: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    pizza.setPosition(Math.randomRange(0, 160), Math.randomRange(0, 120))
    // @highlight
    info.startCountdown(10)
})
```

## 完成

恭喜，您已完成了该游戏的编写！ 使用游戏模拟器尝试移动你的 `||sprites:Player||` ，在倒计时结束前吃到尽可能多的披萨。 你的最好记录是多少分？

```blocks
let pizza: Sprite = null
let mySprite: Sprite = null
scene.setBackgroundColor(7)
mySprite = sprites.create(img`
. . . . . 5 5 5 5 5 5 . . . . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. 5 5 5 5 5 5 5 5 5 5 5 5 5 5 .
. 5 5 5 f f 5 5 5 5 f f 5 5 5 .
5 5 5 5 f f 5 5 5 5 f f 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 5 5 5 5 5 5 5 5 5 5 5 5 5 5
5 5 f 5 5 5 5 5 5 5 5 5 5 f 5 5
5 5 5 f 5 5 5 5 5 5 5 5 f 5 5 5
. 5 5 5 f 5 5 5 5 5 5 f 5 5 5 .
. 5 5 5 5 f f f f f f 5 5 5 5 .
. . 5 5 5 5 5 5 5 5 5 5 5 5 . .
. . . 5 5 5 5 5 5 5 5 5 5 . . .
. . . . . 5 5 5 5 5 5 . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
pizza = sprites.create(img`
. . . . . . b b b b . . . . . .
. . . . . . b 4 4 4 b . . . . .
. . . . . . b b 4 4 4 b . . . .
. . . . . b 4 b b b 4 4 b . . .
. . . . b d 5 5 5 4 b 4 4 b . .
. . . . b 3 2 3 5 5 4 e 4 4 b .
. . . b d 2 2 2 5 7 5 4 e 4 4 e
. . . b 5 3 2 3 5 5 5 5 e e e e
. . b d 7 5 5 5 3 2 3 5 5 e e e
. . b 5 5 5 5 5 2 2 2 5 5 d e e
. b 3 2 3 5 7 5 3 2 3 5 d d e 4
. b 2 2 2 5 5 5 5 5 5 d d e 4 .
b d 3 2 d 5 5 5 d d d 4 4 . . .
b 5 5 5 5 d d 4 4 4 4 . . . . .
4 d d d 4 4 4 . . . . . . . . .
4 4 4 4 . . . . . . . . . . . .
`, SpriteKind.Food)

sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    pizza.setPosition(Math.randomRange(0, 160), Math.randomRange(0, 120))
    // @highlight
    info.startCountdown(10)
})
```
