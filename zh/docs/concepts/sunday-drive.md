# 周日驾驶

[Open this tutorial in the editor!](/#tutorial:/concepts/sunday-drive)

## Introduction @unplugged

游戏往往需要动作反复出现——需要创造敌人和收集的物品，需要检查获胜条件，等等。``||game:当游戏每隔 500 毫秒更新时||``事件允许您将代码设置为在设置的时间段内运行，以便重复发生。

## 第 1 步 @fullscreen

删除当前编程区中的任何内容，然后在``||game:游戏||``中找到``||game:当游戏每隔 500 毫秒更新时||``。将其拖到编程区中。

```blocks
game.onUpdateInterval(500, function () {

})
```

## 第 2 步 @fullscreen

在``||game:当游戏每隔 500 毫秒更新时||``上更改500为1000。这将使事件每秒发生一次，因为1毫秒是千分之一秒。

```blocks
game.onUpdateInterval(1000, function () {

})
```

## 第 3 步 @fullscreen

在``||sprites:精灵||``中找到``||variables:将 projectile 设为||``，并拖拽到``||game:当游戏每隔 500 毫秒更新时||``。打开``||variables:弹射物||``上的图像编辑器，选择或者创建一辆面向**右**的汽车。

```blocks
let projectile: Sprite = null;
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . .
. . . . 2 2 2 2 2 2 2 2 . . . .
. . . 2 4 2 2 2 2 2 2 c 2 . . .
. . 2 c 4 2 2 2 2 2 2 c c 2 . .
. 2 c c 4 4 4 4 4 4 2 c c 4 2 d
. 2 c 2 e e e e e e e b c 4 2 2
. 2 2 e b b e b b b e e b 4 2 2
. 2 e b b b e b b b b e 2 2 2 2
. e e 2 2 2 e 2 2 2 2 2 e 2 2 2
. e e e e e e f e e e f e 2 d d
. e e e e e e f e e f e e e 2 d
. e e e e e e f f f e e e e e e
. e f f f f e e e e f f f e e e
. . f f f f f e e f f f f f e .
. . . f f f . . . . f f f f . .
. . . . . . . . . . . . . . . .
`, 50, 100)
})
```

## 第 4 步 @fullscreen

在``||sprites:弹射物||``上设置``||sprites:vy||``的值为0，这样汽车**只会**向右开。

```blocks
let projectile: Sprite = null;
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . .
. . . . 2 2 2 2 2 2 2 2 . . . .
. . . 2 4 2 2 2 2 2 2 c 2 . . .
. . 2 c 4 2 2 2 2 2 2 c c 2 . .
. 2 c c 4 4 4 4 4 4 2 c c 4 2 d
. 2 c 2 e e e e e e e b c 4 2 2
. 2 2 e b b e b b b e e b 4 2 2
. 2 e b b b e b b b b e 2 2 2 2
. e e 2 2 2 e 2 2 2 2 2 e 2 2 2
. e e e e e e f e e e f e 2 d d
. e e e e e e f e e f e e e 2 d
. e e e e e e f f f e e e e e e
. e f f f f e e e e f f f e e e
. . f f f f f e e f f f f f e .
. . . f f f . . . . f f f f . .
. . . . . . . . . . . . . . . .
`, 50, 0)
})
```

## 第 5 步 @fullscreen

从``||sprites:精灵||``中找到``||sprites:将 mySprite 的 x 设为 0||``，并拖拽到``||variables:将 projectile 设为||``的下方。更改``||variables:mySprite||``为``||variables:projectile||``,更改``||sprites:x||``为``||sprites:y||``。

```blocks
let projectile: Sprite = null;
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . .
. . . . 2 2 2 2 2 2 2 2 . . . .
. . . 2 4 2 2 2 2 2 2 c 2 . . .
. . 2 c 4 2 2 2 2 2 2 c c 2 . .
. 2 c c 4 4 4 4 4 4 2 c c 4 2 d
. 2 c 2 e e e e e e e b c 4 2 2
. 2 2 e b b e b b b e e b 4 2 2
. 2 e b b b e b b b b e 2 2 2 2
. e e 2 2 2 e 2 2 2 2 2 e 2 2 2
. e e e e e e f e e e f e 2 d d
. e e e e e e f e e f e e e 2 d
. e e e e e e f f f e e e e e e
. e f f f f e e e e f f f e e e
. . f f f f f e e f f f f f e .
. . . f f f . . . . f f f f . .
. . . . . . . . . . . . . . . .
`, 50, 0)
    projectile.y = 0
})
```

## 第 6 步 @fullscreen

从``||math:数学||``中找到``||math:选取随机数，范围为 0 至 10||``，并替换掉在``||sprites:将 projectile 的 y 设为 0||``的 0。

这将把``||variables:projectile||``放在0到10之间的随机``||sprites:y||``位置。

```blocks
let projectile: Sprite = null;
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . .
. . . . 2 2 2 2 2 2 2 2 . . . .
. . . 2 4 2 2 2 2 2 2 c 2 . . .
. . 2 c 4 2 2 2 2 2 2 c c 2 . .
. 2 c c 4 4 4 4 4 4 2 c c 4 2 d
. 2 c 2 e e e e e e e b c 4 2 2
. 2 2 e b b e b b b e e b 4 2 2
. 2 e b b b e b b b b e 2 2 2 2
. e e 2 2 2 e 2 2 2 2 2 e 2 2 2
. e e e e e e f e e e f e 2 d d
. e e e e e e f e e f e e e 2 d
. e e e e e e f f f e e e e e e
. e f f f f e e e e f f f e e e
. . f f f f f e e f f f f f e .
. . . f f f . . . . f f f f . .
. . . . . . . . . . . . . . . .
`, 50, 0)
    projectile.y = Math.randomRange(0, 10)
})
```

## 第 7 步 @fullscreen

在``||scene:场景||``中找到``||scene:屏幕高度||``，替换掉在``||math:选取随机数，范围为 0 至 10||``上的10。

``||scene:屏幕高度||``就是屏幕的高度(120),因此这会将``||variables:projectile||``放在屏幕左侧的随机位置。

```blocks
let projectile: Sprite = null;
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . .
. . . . 2 2 2 2 2 2 2 2 . . . .
. . . 2 4 2 2 2 2 2 2 c 2 . . .
. . 2 c 4 2 2 2 2 2 2 c c 2 . .
. 2 c c 4 4 4 4 4 4 2 c c 4 2 d
. 2 c 2 e e e e e e e b c 4 2 2
. 2 2 e b b e b b b e e b 4 2 2
. 2 e b b b e b b b b e 2 2 2 2
. e e 2 2 2 e 2 2 2 2 2 e 2 2 2
. e e e e e e f e e e f e 2 d d
. e e e e e e f e e f e e e 2 d
. e e e e e e f f f e e e e e e
. e f f f f e e e e f f f e e e
. . f f f f f e e f f f f f e .
. . . f f f . . . . f f f f . .
. . . . . . . . . . . . . . . .
`, 50, 0)
    projectile.y = Math.randomRange(0, scene.screenHeight())
})
```

## 完成

恭喜你，你可以让汽车在屏幕上随机行驶！你可以用这个来开始你自己的过路游戏——例如，让一只鸡或一只鸭过马路。记住，默认情况下，``||sprites:弹射物||``属于``||sprites:Projectile||``类型。