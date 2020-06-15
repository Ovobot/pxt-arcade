# 星空

## Introduction @unplugged

通过设置场景背景中星星的运动对太空游戏的动态效果是一种很有效的方式。填充屏幕的星星作为移动的投射物可以创造一个玩家精灵在空间中加速的错觉，即使它仍然在屏幕上的相同位置。

![Starfield background playing](/static/concepts/star-field/star-field-background.gif)

## 第 1 步

在``||game:游戏||``标签栏，找到``||game:当游戏更新时||``程序块并拖拽到编程区。

```blocks
game.onUpdate(function () {

})
```

## 第 2 步

从``||sprites:精灵||``中找到内部包含``||sprites:弹射物从边上||``的``||variables:将 projectile 设为||``程序块。拖拽到``||game:当游戏更新时||``内部。修改`vx`的值为`0` `vy`为`100`。

```blocks
game.onUpdate(function () {
    let projectile = sprites.createProjectileFromSide(img`
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
`, 0, 100)
})
```

## 第 3 步 @fullscreen

单击``||sprites:弹射物从边上||``中的灰色框，创建单个像素的白色星星。

![Creating star image](/static/concepts/star-field/creating-star-image.gif)

```blocks
game.onUpdate(function () {
    let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, 100)
})
```

## 第 4 步 @fullscreen

从``||Math:数学||``中拖拽``||Math:选取随机数 范围为0 至 10||``，将其放在``||sprites:弹射物||``的 ``||sprites:vy||`` 插槽中，就在``100``上方。 在``||Math:选取随机数 范围为0 至 10||``中，将``0``更改为``20``，将``10``更改为``30``

```blocks
game.onUpdate(function () {
    let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
})
```

## 第 5 步

回到``||sprites:精灵||``中找到``||sprites:设置 mySprite 的位置为||``程序块，拖拽到``||variables:将 projectile 设为||``下方，然后更改``||variables:mySprite||``为``||variables:projectile||``。

```blocks
game.onUpdate(function () {
    let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
    projectile.setPosition(0, 0)
})
```

## 第 6 步

再拖拽一个``||Math:选取随机数 范围为0 至 10||``放到``||sprites:设置 projectile 的位置为||`` 的 ``||sprites:x||``的值上面。在``||scene:场景||``中找到``||scene:屏幕宽度||``，替换掉``||Math:选取随机数 范围为0 至 10||``上的``10``。

```blocks
game.onUpdate(function () {
    let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
    projectile.setPosition(Math.randomRange(0, scene.screenWidth()), 0)
})
```

## 第 7 步 @fullscreen

此时，正在创建过多的星星。 通过将``||game:当游戏更新时||``内嵌入``||logic:如果为 则||``程序块可以解决此问题。

![Surround with if then](/static/concepts/star-field/surround-if-then.gif)

```blocks
game.onUpdate(function () {
    if (true) {
        let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
        projectile.setPosition(Math.randomRange(0, scene.screenWidth()), 0)
    }
})
```

## 第 8 步

从``||math:数学||``中找到``||Math:0 % 几率||``程序块替换掉``||logic:如果为 则||``的``true``条件。更改百分比``0``为``25``。
 
```blocks
game.onUpdate(function () {
    if (Math.percentChance(25)) {
        let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
        projectile.setPosition(Math.randomRange(0, scene.screenWidth()), 0)
    }
})
```

## 完成

恭喜你，你的星空已经完成了！在上面构建任何你想要的游戏，或者继续下一步的挑战，这将有助于优化代码。

## 拓展挑战 @fullscreen

实际上，外太空中的星星距离任何其他物体都有数百万光年的距离。所以，它们不应该与其他物体相互作用或碰撞。

在``||sprites:精灵||``中找到``||sprites:设置 mySprite 保持在屏幕中||``，放到``||variables:将 projectile 设为||``下方，修改``||variables:mySprite||``为``||variables:projectile||``,点击``||sprites:保持在屏幕中||``选择``||sprites:变为幽灵||``，点击``关``切换到``开``。

这对帧速率也有很大的影响，因为游戏可以跳过处理星星与游戏中任何其他精灵重叠的相关的动作。

```blocks
game.onUpdate(function () {
    if (Math.percentChance(25)) {
        let projectile = sprites.createProjectileFromSide(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . 1 . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, 0, Math.randomRange(20, 30))
        projectile.setPosition(Math.randomRange(0, scene.screenWidth()), 0)
        projectile.setFlag(SpriteFlag.Ghost, true)
    }
})
```
