动画时间由 `animation-duration` 样式定义，在 `@keyframes` 中使用 `<percentage>（百分比）`来定义关键帧。一个可用的动画序列至少有两个关键帧。
- from：0%
- to：100%

简单示例
```
p {
  animation-duration: 3s;
  animation-name: slidein;
}

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

### 使用动画事件
利用动画事件更好的控制动画，这些事件由 `AnimationEvent` 对象表示
- animationstart：开始
- animationend：结束
- animationiteration：动画循环