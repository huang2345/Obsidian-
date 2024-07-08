该样式为综合样式，允许配置动画时间、时长以及其他动画细节。

- animation-delay
	- 延时
- animation-direction
	- 设置动画运行完毕之后，是重新从头播放还是逆向播放
		- normal：正向
		- reverse：反向
		- alternate：正反交替播放，第一次是正向
		- alternate-reverse：正反交替播放，第一次是反向
- animation-duration
	- 设置动画运行一次的时间
- animation-iteration-count
	- 设置动画重复次数，可以指定 infinite 无限次重复动画
- animation-name
	- 指定具体使用哪个由 `@keyframes` 描述的关键帧名称
- animation-play-state
	- 允许暂停和恢复动画
		- running运行
		- paused暂停
- animation-timing-function
	- 设置动画速度，即通过建立加速度曲线，设置动画在关键帧之间是如何变化。
- animation-fill-mode
	- 指定动画执行前后如何为目标元素应用样式。
		- none
		- forwards
			- 目标将保留由执行期间遇到的最后一个关键帧计算值。最后一个关键帧取决于animation-direction和animation-iteration-count的值
		- backwards
			- 动画将在应用于目标时立即应用第一个关键帧中定义的值，并在animation-delay期间保留此值。第一个关键帧取决于animation-direction的值
		- both
			- 动画将遵循forwards和backwards的规则，从而在两个方向上扩展动画属性。



