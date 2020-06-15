# 塔拉贡的故事

![Scrolling story text](/static/concepts/talagron.jpg)

也许您想用一段文字来介绍您的游戏，慢慢滚动，以便玩家可以阅读你的游戏传奇。游戏对话框提供了一种显示短交互消息的方式，但对于带有效果的文本，您还需要其他东西。

通过创建一个图像或多个段落的图像，您可以创建一个文本对象，该对象将在屏幕上滚动。

本示例显示了游戏开始之前的故事文本。 文本从屏幕底部滚动到顶部。 按钮**A**可以暂停和恢复滚动。 向上和向下按钮将故事每次滚动一行。 当包含文本的精灵从屏幕上滚出时会被销毁，从而触发游戏的开始。


```typescript
namespace SpriteKind {
    export const Star = SpriteKind.create();
}

let ship: Sprite = null
let hyper = false
let star: Sprite = null
let scroll = false
let lineAdjust = 0
let sagaSprite: Sprite = null
let sagaImage: Image = null
let storyLines = [
    "塔拉贡的故事",
    "",
    "从前,",
    "就在很久以前,",
    "一群爱好和平的人",
    "幸福的生活在塔拉贡星球上。",
    "",
    "他们使用稀有矿物",
    "锡兰蒂姆来为其星球",
    "提供能量。",
    "",
    "多巴尼人突袭了塔拉贡",
    "并且从他们那里拿走了",
    "所有已知的锡兰蒂姆。 ",
    "不好! 啊！啊！",
    "",
    "你的任务是帮助保护",
    "塔拉贡不受贪心的",
    "多巴尼人的伤害",
    "所以，现在就走，祝你好运！"
]
scroll = true
sagaImage = image.create(scene.screenWidth(), 14 * storyLines.length)
for (let i = 0; i <= storyLines.length - 1; i++) {
    sagaImage.printCenter(storyLines[i], i * 14, i > 0 ? 7 : 4)
}
sagaSprite = sprites.create(sagaImage, 0)
sagaSprite.top = scene.screenHeight() - 1
sagaSprite.setFlag(SpriteFlag.AutoDestroy, true)
sagaSprite.vy = -10
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!hyper) {
        sagaSprite.vy = scroll ? 0 : -10
        scroll = !(scroll)
    }
})

controller.up.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!hyper) {
        sagaSprite.vy = 0
        scroll = false
        lineAdjust = (sagaSprite.bottom + 1) % 10
        sagaSprite.bottom -= (lineAdjust > 0) ? lineAdjust : 10
    }
})
controller.down.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!hyper) {
        sagaSprite.vy = 0
        scroll = false
        lineAdjust = (sagaSprite.top + 1) % 10
        sagaSprite.top += 10 - lineAdjust
    }
})
game.onUpdate(function () {
    if (sagaSprite.bottom < 0) {
        sagaSprite.destroy()
    }
    if (Math.percentChance(25) || hyper) {
        star = sprites.create(img`1`, SpriteKind.Star)
        star.setFlag(SpriteFlag.AutoDestroy, true)
        star.setFlag(SpriteFlag.Ghost, true)
        star.x = Math.randomRange(0, scene.screenWidth())
        star.y = Math.randomRange(0, scene.screenHeight())
        star.vx = (star.x < scene.screenWidth() / 2) ? -2 : 2
        star.vy = (star.y < scene.screenHeight() / 2) ? -1 : 1
        if (hyper) {
            star.ax = star.vx * 1000
            star.ay = star.vy * 1000
            if (Math.percentChance(15)) {
                ship.x = Math.randomRange(scene.screenWidth() / 2 - 5, scene.screenWidth() / 2 + 5)
                ship.y = Math.randomRange(scene.screenHeight() / 2 - 2, scene.screenHeight() / 2 + 2)
            }
        }
    }
})
sagaSprite.onDestroyed(function () {
    ship = sprites.create(img`
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . 7 4 . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . e e . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . e e . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . e e . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . e e . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . 4 e e 4 . . . . . . . . . . . . . .
    . . . . . . . . . . . . e e e e e e e e . . . . . . . . . . . .
    . . . . . . . . . . . e e e e e e e e e e . . . . . . . . . . .
    . . . . . . . . . . e e e e 5 3 3 5 e e e e . . . . . . . . . .
    . . . . . . . . . 4 e e e 5 3 5 2 2 5 e e e 4 . . . . . . . . .
    . . . . . . . 7 7 e e e e 5 2 2 5 5 2 e e e e 7 7 . . . . . . .
    . . . . . . 7 e e e e e e 2 2 5 2 3 3 e e e e e e 7 . . . . . .
    . . . . 7 e e e e e e e e 5 2 2 2 5 2 e e e e e e e e 7 . . . .
    . . e e e e e e e e e e e e 3 5 5 2 e e e e e e e e e e e e . .
    . e e e e e e . . . 7 e e e e e e e e e e 7 . . . e e e e e e .
    e e e e 7 . . . . . . . e e e e e e e e . . . . . . . 7 e e e e
    e 7 . . . . . . . . . . . e e e e e e . . . . . . . . . . . 7 e
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
    ship.startEffect(effects.warmRadial)
    hyper = true
    for (let slowStar of sprites.allOfKind(SpriteKind.Star)) {
        slowStar.ax = slowStar.vx * 1000
        slowStar.ay = slowStar.vy * 1000
    }
})
```