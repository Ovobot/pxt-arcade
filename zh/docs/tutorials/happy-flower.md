# 开心的小花

### ~button /#tutorial:/tutorials/happy-flower

试试这个教程！

### ~

## Introduction @unplugged

花使周围的每个人都快乐，尤其是从花蜜中提取花蜜的蜜蜂。 为了说明这一点，我们可以创建一朵花，将快乐的小蜜蜂送回蜂巢。

![Happy thoughts](/static/tutorials/happy-flower/happy-thoughts.gif)

## 第 1 步

在`||sprites:精灵||`中找到`||variables:将 mySprite 设为||`. 将其拖入 `||loops:当开机时||`, , 并画一朵花。 接下来, 拖入一个积木块 `||scene:设置背景颜色为||` 并选择`light blue`.

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
```

## 第 2 步

打开`||game:游戏||`栏，拖拽 `||game:当游戏每隔 500 毫秒更新时||` 程序块到编程区. 设置时间为 `1000 ms`.

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {

})
```

## 第 3 步

在`||sprites:精灵||` 中找到`||sprites:将 projectile 设为 弹射物 从 mySprite||`.将它拖入到`||game:当游戏每隔 1000 毫秒更新时||`.

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    let projectile = sprites.createProjectileFromSprite(img`
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
`, mySprite, 0, 100)
})
```

## 第 4 步

在`||sprites:弹射物||` 程序块上，点击灰色椭圆区域，绘制一个可爱的小蜜蜂。

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    let projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, 0, 100)
})
```

## 第 5 步

拖拽 `||Math:选取随机数 范围为0 至 10||`. 程序块到`||sprites:弹射物||`上的`||sprites:vx||` 位置，将`0` 修改为 `-25` ，将 `10` 修改为`25`.

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    let projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, Math.randomRange(-25, 25), 100)
})
```

## 第 6 步

将鼠标放在`||Math:选取随机数 范围为-25 至 25||` 程序块上，右击选择重复，将复制出来的程序块拖拽到 `||sprites:弹射物||`上的`||sprites:vy||` 位置。

```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    let projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, Math.randomRange(-25, 25), Math.randomRange(-25, 25))
})
```

## 第 7 步 @fullscreen

在`||sprites:精灵||` 中找到`||sprites:将 mySprite 的 x 设为 0||` ，放在`||variables:将 projectile 设为||`程序块后面，将`||variables:mySprite||` 改为`||variables:projectile||`. 点击`||sprites:x||` to `||sprites:生命周期||` ，并且把`0`修改为`3000`.

![Adding life span](/static/tutorials/happy-flower/life-span.gif)

```blocks
let projectile: Sprite = null
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, Math.randomRange(-25, 25), Math.randomRange(-25, 25))
    projectile.lifespan = 3000
})
```

## 第 8 步

恭喜，您的开心的小花已经完成！ 现在它将送回快乐的小蜜蜂。 在模拟器中运行程序，看看蜜蜂飞走了。 您是否注意到一些蜜蜂向后飞？ 您想尝试一些额外的东西吗？ 如果是这样，我们可以让一些蜜蜂朝相反的方向飞走。 继续下一步。

## 第 9 步

让我们设置一个条件，如果蜜蜂向左飞走，我们换一张蜜蜂的图像。找到 `||logic:如果为 则||` 程序块并放在 `||sprites:设置 projectile 生命周期||`.后面。在 `||logic:如果为 则||`程序块上用`||logic:0 < 0||`程序块替换掉`true` 条件。将`||sprites:mySprite x||`放在第一个 `0` 的位置上。 将 `||variables:mySprite||` 修改为`||variables:projectile||`，然后将`||sprites:x||` 修改为 `||sprites:vx (velocity x)||`.

```blocks
let projectile: Sprite = null
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, Math.randomRange(-25, 25), Math.randomRange(-25, 25))
    projectile.lifespan = 3000
    if (projectile.vx < 0) {
    }
})
```

## 第 10 步

打开 Go to the Toolbox and open the **高级** 标签栏，在. In `||images:图像||`  中找到 `||images:水平翻转 picture||` 程序块。将它拖拽到 `||logic:如果为 则||`程序块内部，现在，回到 `||sprites:精灵||`标签栏，选择 `||sprites:mySprite 的图像||` 并且拖拽到`||images:水平翻转 picture||` 的`||variables:picture||` 位置上，最后将  `||variables:mySprite||` 修改为 `||variables:projectile||`.

![Flip image of the bee](/static/tutorials/happy-flower/bee-flip.gif)

```blocks
let projectile: Sprite = null
let mySprite: Sprite = null
scene.setBackgroundColor(9)
mySprite = sprites.create(img`
. . . 4 . . . . . . 2 2 . . . .
. . . 4 4 4 3 . 3 2 2 . . . . .
. . . . 4 e 5 5 5 e 2 . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . . 5 5 e 5 5 . . . . . .
. . . . 3 5 5 5 5 5 3 . . . . .
. . . . 2 e 5 5 5 e 4 . . . . .
. . . . 2 2 3 7 3 4 4 4 . . . .
. . . 2 2 . . 7 . . . 4 . . . .
. . . . . . . 7 . . . . . . . .
. . . 7 7 7 . 7 . 7 7 . . . . .
. . . . 7 7 . 7 . 7 7 . . . . .
. . . . . 7 7 7 7 7 . . . . . .
. . . . . . 7 7 7 . . . . . . .
. . . . . . . 7 . . . . . . . .
. . . . . . . 7 . . . . . . . .
`, SpriteKind.Player)
game.onUpdateInterval(1000, function () {
    projectile = sprites.createProjectileFromSprite(img`
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . b b . . b . . . . . . .
. . . . . b b b b . . . . . . .
. . . . . . . b b . . . . . . .
. . . . . f 5 f 5 f . . . . . .
. . . . 5 f 5 f 5 f 1 . . . . .
. . . . 5 f 5 f 5 f 5 b . . . .
. . . . . . 5 f 5 f 5 . . . . .
. . . . . e . . . e . . . . . .
. . . . e . . . . e . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . .
`, mySprite, Math.randomRange(-25, 25), Math.randomRange(-25, 25))
    projectile.lifespan = 3000
    if (projectile.vx < 0) {
        projectile.image.flipX()
    }
})
```

## 完成

好吧，现在您的蜜蜂可以快乐地向两个方向飞走了！
