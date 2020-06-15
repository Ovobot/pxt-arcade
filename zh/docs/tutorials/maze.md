# 迷宫

### ~button /#tutorial:/tutorials/maze

试试这个教程！

### ~

## Introduction @unplugged

欢迎使用@boardname@!  让我们开始创建一个游戏，让您的玩家在有限的时间内尝试走出迷宫！

![Maze game playing](/static/tutorials/maze/maze-game.gif)

## 第 1 步

我们要做的第一件事就是创建我们玩家精灵。在``||sprites:精灵||``找到``||variables:将 mySprite 设为||``，拖拽到``||loops:当开机时||``程序块内部。

```blocks
let mySprite: Sprite = sprites.create(img`
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

## 第 2 步 @fullscreen

单击``||variables:将 mySprite 设为||``中的灰色框，然后绘制玩家精灵的图像。 它可以是任何东西，实心方块或图形。

![Draw a figure for the sprite](/static/tutorials/maze/draw-sprite-figure.gif)

```blocks
let mySprite: Sprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
```

## 第 3 步

现在，让我们用控制器的箭头键移动精灵。从``||controller:控制器||``中拖拽``||controller:使用按键移动 mySprite||``程序块放到``||variables:将 mySprite 设为||``下方。

```blocks
let mySprite: Sprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
```

## 第 4 步

接下来，创建一个将用作迷宫的地图。从``||scene:场景||``拖拽``||scene:设置图块地图为||``程序块并嵌入到 ``||loops:当开机时||``。
单击灰色框以打开图块地图，选择图块，然后使用工具绘制自己的迷宫。
一定要从开始到结束留下一条路径，这样用户就可以逃脱。
在开始和结束位置都留一个空白图块。

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
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
    hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17000b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b0004090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
    img`
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
    `,
    [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast],
    TileScale.Sixteen
))
```

## 第 5 步

使用两个新的图块填充上一步中剩下的图块地图中的两个空白区域：
看起来像是您可以逃脱的东西（例如，门或楼梯），
另一个带有标记起始位置的内容（例如，梯子）。
确保未在迷宫中的其他任何地方使用这些图块。

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
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
    hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
    img`
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
    `,
    [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
    TileScale.Sixteen
))
```

## 第 6 步

从``||scene:场景||``中找到``||scene:放置 mySprite 到随机位置的图块上面||``，并嵌入到`||loops:当开机时||`程序块。放在``||scene:设置图块地图为||``下方。
这会将您创建的角色移动到所选图块之一的顶部；
单击方格图块，然后选择玩家精灵起点的图块。

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
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
    hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
    img`
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
    `,
    [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
    TileScale.Sixteen
))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
```

## 第 7 步

玩家现在不在屏幕上，这使得游戏有些困难。
从``||scene:场景||``中找到``||scene:镜头跟随精灵 mySprite 移动||``，并嵌入到`||loops:当开机时||`程序块底部。
这将使相机跟随玩家角色在屏幕上移动。

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
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
            hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
            img`
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
            `,
            [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
            TileScale.Sixteen
        ))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## 第 8 步

从``||scene:场景||``找到``||scene: 当 sprite 类型 Player 与图块 在 location 重叠时||``程序块。
只要玩家在给定类型的图块上方，就会触发此事件；
单击方格框并将其更改为迷宫末端选择的图块。

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
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {

})
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
            hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
            img`
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
            `,
            [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
            TileScale.Sixteen
        ))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## 第 9 步

在``||game:游戏||``中找到``||game:游戏结束||``程序块，并拖拽到``||scene: 当 sprite 类型 Player 与图块 在 location 重叠时||``。
点击``输了``更改为``获胜``。
这样可以使玩家在到达出口时获胜。

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
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.over(true)
})
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
            hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
            img`
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
            `,
            [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
            TileScale.Sixteen
        ))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## 第 10 步

在``||info:游戏信息||``中找到``||info:开始倒计时 10 (秒)||`` ，并拖拽到`||loops:当开机时||`。

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
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.over(true)
})
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
            hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
            img`
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
            `,
            [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
            TileScale.Sixteen
        ))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
info.startCountdown(10)
```

## 第 11 步 @unplugged

现在您有了一个带有目标的游戏，而且时间紧迫……但是玩家可以在穿越墙壁移动！
重新打开图块地图编辑器，
使用``Draw walls``工具在所有应该阻止玩家穿越的图块上绘制墙，
这样玩家就不能够穿越它们了。

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
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.over(true)
})
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tiles.createTilemap(
            hex`100010000102020c0c1801020c0202180c0202030a0f0b0b0b0b090b0b0b0b0b0b0b0f17130b0b0b0b0b090b0b0b0b0f0b0b0b0d090b0b010c0c1b0f0b1a0707100b0b0d0a0b0b090b0b0b0b0b0d0f0b090b0b04090f0b0a0b0b0f0b0b0d0b0b0a0b0b04120b0b0a0b0b090f0b0d0b0f090f0b170a0b0b08100f090b0b0d0f0b120b0b0d090b0f0b0806090b0b0d0b0b0a0b0b040a0b0b0b0f0b090f0b0d0b0b090f0b0d0a0b0b0b0b0b090b0b0d0b0b090b0b04090b0b0c0c0c1b0b0f0b0b0f090b0b04120b0b0b0b0b0f0b0b0b0b0b090b0b170a0b0b0b0b0b090b0b0b0b0b0a0b1c04090f0b0b0b0f090b0b0f0b0b090f0b0408070719070608060719060608060705`,
            img`
                2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
                2 . . . . . 2 . . . . . . . . 2
                . . . . . . 2 . . . . . . . . 2
                2 . . 2 2 2 2 . . 2 2 2 2 . . 2
                2 . . 2 . . . . . 2 . . 2 . . 2
                2 . . 2 . . . . . 2 . . 2 . . 2
                2 . . 2 . . 2 . . 2 . . 2 . . 2
                2 . . 2 2 . 2 . . 2 . . 2 . . 2
                2 . . . 2 2 2 . . 2 . . 2 . . 2
                2 . . . . . 2 . . 2 . . 2 . . 2
                2 . . . . . 2 . . 2 . . 2 . . 2
                2 . . 2 2 2 2 . . . . . 2 . . 2
                2 . . . . . . . . . . . 2 . . 2
                2 . . . . . 2 . . . . . 2 . . 2
                2 . . . . . 2 . . . . . 2 . . 2
                2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
            `,
            [myTiles.tile0,sprites.dungeon.greenOuterNorthWest,sprites.dungeon.greenOuterNorth0,sprites.dungeon.greenOuterNorthEast,sprites.dungeon.greenOuterEast0,sprites.dungeon.greenOuterSouthWest,sprites.dungeon.greenOuterSouth0,sprites.dungeon.greenOuterSouth1,sprites.dungeon.greenOuterSouthEast,sprites.dungeon.greenOuterWest1,sprites.dungeon.greenOuterWest0,sprites.dungeon.floorDark2,sprites.dungeon.greenOuterNorth1,sprites.dungeon.greenOuterEast1,sprites.dungeon.floorDark1,sprites.dungeon.floorDark5,sprites.dungeon.greenInnerNorthEast,sprites.dungeon.purpleInnerNorthWest,sprites.dungeon.greenOuterWest2,sprites.dungeon.stairWest,sprites.dungeon.stairEast,sprites.dungeon.stairLarge,sprites.dungeon.greenInnerSouthWest,sprites.dungeon.greenOuterEast2,sprites.dungeon.greenOuterNorth2,sprites.dungeon.greenOuterSouth2,sprites.dungeon.greenInnerNorthWest,sprites.dungeon.greenInnerSouthEast,sprites.dungeon.stairLadder],
            TileScale.Sixteen
        ))
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
info.startCountdown(10)
```

## 完成

恭喜，你的迷宫游戏完成了！你现在可以玩你的第一个游戏了。看看你能不能逃离迷宫。
