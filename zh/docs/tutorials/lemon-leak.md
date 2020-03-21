# 守护柠檬

### ~button /#tutorial:/tutorials/lemon-leak

试试这个教程！

### ~

## Introduction @unplugged

![Game animation](/static/tutorials/lemon-leak.gif)

嘿，让我们做一个野草莓出没来攻击我们玩家所控制的柠檬的游戏。 目的是通过躲避草莓来防止柠檬汁流失。 草莓与柠檬碰撞时，柠檬会渗出部分果汁。

## 第 1 步   @fullscreen

打开`||scene:场景||`，拖拽 `||scene:设置背景颜色为||`程序块，将其嵌入到 `||loops:当开机时||` 程序块。选择颜色 `purple` 。打开`||sprites:精灵||`栏，拖拽程序块  `||variables:将 mySprite 设为||`  程序块，将其也放在里面。点击灰色椭圆区域,从图库里面选择柠檬图像。打开`||controller:控制器||` 栏，拖拽程序块 `||controller:使用按键移动 mySprite||` 并吸附到{code8}||variables:将 mySprite 设为||{/code8}  程序块下方。这样我们就能移动柠檬了。

![Pick the lemon image](/static/tutorials/lemon-leak/pick-a-lemon.gif)

```blocks
scene.setBackgroundColor(10)
let mySprite = sprites.create(img`
    4 4 4 . . 4 4 4 4 4 . . . . . .
    4 5 5 4 4 5 5 5 5 5 4 4 . . . .
    b 4 5 5 1 5 1 1 1 5 5 5 4 . . .
    . b 5 5 5 5 1 1 5 5 1 1 5 4 . .
    . b d 5 5 5 5 5 5 5 5 1 1 5 4 .
    b 4 5 5 5 5 5 5 5 5 5 5 1 5 4 .
    c d 5 5 5 5 5 5 5 5 5 5 5 5 5 4
    c d 4 5 5 5 5 5 5 5 5 5 5 1 5 4
    c 4 5 5 5 d 5 5 5 5 5 5 5 5 5 4
    c 4 d 5 4 5 d 5 5 5 5 5 5 5 5 4
    . c 4 5 5 5 5 d d d 5 5 5 5 5 b
    . c 4 d 5 4 5 d 4 4 d 5 5 5 4 c
    . . c 4 4 d 4 4 4 4 4 d d 5 d c
    . . . c 4 4 4 4 4 4 4 4 5 5 5 4
    . . . . c c b 4 4 4 b b 4 5 4 4
    . . . . . . c c c c c c b b 4 .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
```

## 第 2 步

为了防止柠檬离开屏幕，拖动`||sprites:设置 mySprite 保持在屏幕中||` 程序块吸附在 {code5}||controller:使用按键移动 mySprite||{/code5} 后面。将开关滑动到`开`。找到程序块`||info:开始倒计时||` ，然后吸附在最后。修改时间 `10` 为`30`。

```blocks
scene.setBackgroundColor(10)
let mySprite = sprites.create(img`
    4 4 4 . . 4 4 4 4 4 . . . . . .
    4 5 5 4 4 5 5 5 5 5 4 4 . . . .
    b 4 5 5 1 5 1 1 1 5 5 5 4 . . .
    . b 5 5 5 5 1 1 5 5 1 1 5 4 . .
    . b d 5 5 5 5 5 5 5 5 1 1 5 4 .
    b 4 5 5 5 5 5 5 5 5 5 5 1 5 4 .
    c d 5 5 5 5 5 5 5 5 5 5 5 5 5 4
    c d 4 5 5 5 5 5 5 5 5 5 5 1 5 4
    c 4 5 5 5 d 5 5 5 5 5 5 5 5 5 4
    c 4 d 5 4 5 d 5 5 5 5 5 5 5 5 4
    . c 4 5 5 5 5 d d d 5 5 5 5 5 b
    . c 4 d 5 4 5 d 4 4 d 5 5 5 4 c
    . . c 4 4 d 4 4 4 4 4 d d 5 d c
    . . . c 4 4 4 4 4 4 4 4 5 5 5 4
    . . . . c c b 4 4 4 b b 4 5 4 4
    . . . . . . c c c c c c b b 4 .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setFlag(SpriteFlag.StayInScreen, true)
info.startCountdown(30)
```

## 第 3 步

现在，打开`||game:游戏||`栏，拖拽 `||game:当游戏每隔 500 毫秒更新时||` 程序块到编程区。设置间隔时间为 `1000` ms, ,或者1 秒（1 second）。在`||sprites:精灵||`中找到 `||variables:将 projectile 设为||` `||sprites:弹射物 从边上||` 程序块，将它拖入到 `||game:当游戏每隔 1000 毫秒更新时||`内部，灰色椭圆区域,从图库里面选择草莓图像。

```blocks
let projectile: Sprite = null
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, 50, 100)
})
```

## 第 4 步

打开 `||math:数学||` 栏，拖拽 `||math: 选取随机数||` 程序块放在弹射物程序块的`vx` 上。修改`||math:选取随机数||` 的第1个数值`0` 为`-50` ，第2个数值`10` 为`50`。复制这个程序块并放到`vy`上。

```blocks
let projectile: Sprite = null
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, Math.randomRange(-50, 50), Math.randomRange(-50, 50))
})
```

## 第 5 步

打开 `||sprites:精灵||`标签栏，拖拽程序块`||sprites:当 sprite 类型 与 otherSprite 类型 重叠||`到编程区。位于Set the kind for `otherSprite` 类型 后面的第二个{code9}||sprites:Player||{/code9}打开菜单，选择类别为 `Projectile`。打开 `||sprites:精灵||` 标签栏, 拖拽`||sprites:mySprite 开启 特效||` 到`||sprites:当 sprite 类型 与 otherSprite 类型 重叠||` 内部。点击**(+)**  按钮，然后设置特效持续时间为 `200` 毫秒。

```blocks
let mySprite: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    mySprite.startEffect(effects.spray, 200)
})
```

## 第 6 步

最后，为了记录柠檬被草莓碰撞的分数， 打开 `||info:游戏信息||` 标签栏并拖拽程序块`||info:将得分值增加||` 到`||sprites:mySprite 开启 特效||` 程序块后面。

```blocks
let mySprite: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    mySprite.startEffect(effects.spray, 200)
    info.changeScoreBy(1)
})
```

## 完成 @fullscreen

就这样！现在继续移动柠檬，尽量不要失去太多的果汁。每次草莓打到你的柠檬上，都会漏出一些果汁，草莓队就会得分。看看你能不能在`30` 秒的比赛中把分数保持在最低。

![Playing Lemon Leak](/static/tutorials/lemon-leak/play-lemon-leak.jpg)
