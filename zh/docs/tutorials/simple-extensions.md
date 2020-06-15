# 简单扩展

## Introduction @unplugged

@boardname@可以让用户轻松开发，并与他人共享其部分代码。在本教程中，您可以使用扩展名为``||corgio:corgio||``来创建一个简单的平台程序。在此示例中，扩展将自动加载，在其他项目中，您可以如下所示加载扩展名
![Adding Corgio Extension](/static/tutorials/simple-extensions/add-corgio.gif)

## 第 1 步

第一步我们要创建我们的柯基犬。在``||corgio:小狗||``里面找到``||variables:将 myCorg 设为||``程序块，并将其嵌入到 `||loops:当开机时||`程序块。柯基犬应该出现在屏幕的左侧。

```blocks
let myCorg: Corgio = corgio.create(SpriteKind.Player)
```

## 第 2 步

现在，让我们使用控制器的箭头键左右移动此精灵。从``||corgio:小狗||``里面找到``||corgio:用方向键让 myCorg 左右移动||``和``||corgio:让 myCorg 跳跃当向上箭头按下||``程序块并放在``||variables:将 myCorg 设为||``下方。

```blocks
let myCorg: Corgio = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
```

## 第 3 步

当图像不变时，柯基有点无聊。为了解决这个问题，从``||corgio:小狗||``找到``||corgio:改变背景当 when myCorg 正在移动||``程序块放在底部。

```blocks
let myCorg: Corgio = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
myCorg.updateSprite()
```

## 第 4 步 @fullscreen

从``||scene:场景||``中找到``||scene:设置图块地图为||``并嵌入到``||loops:当开机时||``。
将图块的尺寸设置为 ``20x8``，
画出一些平台让柯基犬站立,
并将它们设置为``墙``。

![Animation showing completion of this step](/static/tutorials/simple-extensions/drawing-tilemap.gif)

```blocks
namespace myTiles {
    //% blockIdentity=images._tile
    export const tile0 = img`
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
    `
}
let myCorg = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
myCorg.updateSprite()
tiles.setTilemap(tiles.createTilemap(
    hex`1400080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001010101010100000000000000000000000000000000000000000001010101000000000000000000000000000000000000000000000000000000000101010101010101010101000000000000000000`,
    img`
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . 2 2 2 2 2 2 . . . . . . . . . . . . .
        . . . . . . . . 2 2 2 2 . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        2 2 2 2 2 2 2 2 2 2 2 . . . . . . . . .
    `,
    [myTiles.tile0,sprites.builtin.oceanDepths4,sprites.builtin.oceanDepths0],
    TileScale.Sixteen
))
```

## 第 5 步

为了使相机在离开屏幕时跟随柯基，从``||corgio:小狗||``中找到``||corgio:使镜头跟随 myCorg 左右||``并放在``||corgio:改变背景当 when myCorg 正在移动||``下方。

```blocks
namespace myTiles {
    //% blockIdentity=images._tile
    export const tile0 = img`
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
    `
}
let myCorg = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
myCorg.updateSprite()
myCorg.follow()
tiles.setTilemap(tiles.createTilemap(
    hex`1400080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001010101010100000000000000000000000000000000000000000001010101000000000000000000000000000000000000000000000000000000000101010101010101010101000000000000000000`,
    img`
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . 2 2 2 2 2 2 . . . . . . . . . . . . .
        . . . . . . . . 2 2 2 2 . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        2 2 2 2 2 2 2 2 2 2 2 . . . . . . . . .
    `,
    [myTiles.tile0,sprites.builtin.oceanDepths4,sprites.builtin.oceanDepths0],
    TileScale.Sixteen
))
```

## 第 6 步

在地图的末尾，绘制一列图块，该列是与地图中其他图块不同。

这将代表玩家的目标。

```blocks
namespace myTiles {
    //% blockIdentity=images._tile
    export const tile0 = img`
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
    `
}
let myCorg = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
myCorg.updateSprite()
myCorg.follow()
tiles.setTilemap(tiles.createTilemap(
    hex`1400080000000000000000000000000000000000000000030000000000000000000000000000000000000003000000000000000000000000000000000000000300000000000000000000000000000202020200030001010101010100000000000000000200000003000000000000000001010101020202020000000300000000000000000000000002000000000000030101010101010101010101020000000000000003`,
    img`
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . 2 2 2 2 . .
        . 2 2 2 2 2 2 . . . . . . . . 2 . . . .
        . . . . . . . . 2 2 2 2 2 2 2 2 . . . .
        . . . . . . . . . . . . 2 . . . . . . .
        2 2 2 2 2 2 2 2 2 2 2 2 . . . . . . . .
    `,
    [myTiles.tile0,sprites.builtin.oceanDepths4,sprites.builtin.oceanDepths0,sprites.builtin.coral0],
    TileScale.Sixteen
))

```

## 第 7 步

从``||scene:场景||``拖拽``||scene: 当 sprite 类型 Player 与图块 在 location 重叠时||``到编程区,然后单击方格图块以查找用作目标的图块。在此事件的内部，添加``||game:游戏结束||``程序块，点击``输了``改变成``获胜``。

```blocks
namespace myTiles {
    //% blockIdentity=images._tile
    export const tile0 = img`
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
    `
}
scene.onOverlapTile(SpriteKind.Player, sprites.builtin.coral0, function (sprite, location) {
    game.over(false)
})
let myCorg = corgio.create(SpriteKind.Player)
myCorg.horizontalMovement()
myCorg.verticalMovement()
myCorg.updateSprite()
myCorg.follow()
tiles.setTilemap(tiles.createTilemap(
            hex`1400080000000000000000000000000000000000000000030000000000000000000000000000000000000003000000000000000000000000000000000000000300000000000000000000000000000202020200030001010101010100000000000000000200000003000000000000000001010101020202020000000300000000000000000000000002000000000000030101010101010101010101020000000000000003`,
            img`
                . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . 2 2 2 2 . .
                . 2 2 2 2 2 2 . . . . . . . . 2 . . . .
                . . . . . . . . 2 2 2 2 2 2 2 2 . . . .
                . . . . . . . . . . . . 2 . . . . . . .
                2 2 2 2 2 2 2 2 2 2 2 2 . . . . . . . .
            `,
            [myTiles.tile0,sprites.builtin.oceanDepths4,sprites.builtin.oceanDepths0,sprites.builtin.coral0],
            TileScale.Sixteen
        ))

```

## 完成

恭喜，您的平台游戏已完成！ 看看您是否可以走到关卡的尽头。

```package
corgio
```
