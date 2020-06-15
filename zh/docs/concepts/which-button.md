# 哪个按钮?

[Open this tutorial in the editor!](/#tutorial:/concepts/which-button)

## Introduction @unplugged

``||info:游戏信息||``类别有许多属性可以帮助处理游戏中的常见行为。默认情况下，这些属性在设置后会立即显示在屏幕上，允许使用一种简单的方式向玩游戏的人提供有关他们的表现的信息。

## 第 1 步 @fullscreen

在``||info:游戏信息||``中找到``||info:将得分值设为 0||``，并嵌入到``||loops:当开机时||``。

这会将游戏的初始分数设置为0； 请注意，分数现在显示在屏幕的右上角。

```blocks
info.setScore(0)
```

## 第 2 步 @fullscreen

在``||info:游戏信息||``中找到``||info:将生命值设为 3||``，更改 3 为 5。

这设定了玩家的生命值。生命出现在屏幕的左上角，如果玩家耗尽生命，游戏将结束。

```blocks
info.setScore(0)
info.setLife(5)
```

## 第 3 步 @fullscreen

在``||info:游戏信息||``找到``||info:开始倒计时 10 (秒)||``，并嵌入到``||loops:当开机时||``。

这将开始倒计时10秒，然后游戏结束。这也会在屏幕顶部放置一个大计时器，以便玩家知道他们需要冲刺。

```blocks
info.setScore(0)
info.setLife(5)
info.startCountdown(10)
```

## 第 4 步 @fullscreen

在``||controller:控制器||``中找到``||controller:当按钮 A 按下||``，并拖拽到编程区。

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {

})
info.setScore(0)
info.setLife(5)
info.startCountdown(10)
```

## 第 5 步 @fullscreen

在``||info:游戏信息||``中找到``||info:将得分值增加 1||``，并拖拽到``||controller:当按钮 A 按下||``。

这样一来，只要按下``||controller:A||``按钮，玩家的分数就会增加1。试着多次按下按钮，看看你能得到多高的分数。

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeScoreBy(1)
})
info.setScore(0)
info.setLife(5)
info.startCountdown(10)
```

## 第 6 步 @fullscreen

再拖拽一个``||controller:当按钮 A 按下||``到编程区，修改``||controller:A||``为``||controller:B||``。

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeScoreBy(1)
})
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {

})
info.setScore(0)
info.setLife(5)
info.startCountdown(10)
```

## 第 7 步 @fullscreen

再``||info:游戏信息||``中找到``||info:将生命值增加 -1||``，并拖拽到``||controller:当按钮 B 按下||``内部。

这将使玩家在按下``||controller:B||``按钮时失去生命。试着多次按下它，看看当它降到0时，生命是如何显示的。

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeScoreBy(1)
})
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeLifeBy(-1)
})
info.setScore(0)
info.setLife(5)
info.startCountdown(10)
```

## 完成 @fullscreen

恭喜你，你已经完成了你的游戏！这一个可能很简单-唯一失去生命的方法是按下错误的按钮-但这些程序块可以与其他组合，如精灵重叠事件，玩家根据自己的表现得到奖励或惩罚的游戏。