### 实例方法
#### boolean hasRemaining()
如果当前的缓冲区位置没有到达尾部，返回`true`
#### int limit()
返回这个缓冲区的界限位置，即没有任何值可用的第一个位置。(C语言的EOF)。
#### Buffer clear()
将位置复位到0，并将界限设置到容量
#### Buffer flip()
将界限设置到当前位置，并把位置复位到零。
#### Buffer rewind()
将位置复位到零，并保持界限不变
#### Buffer mark()
将标记设置到当前位置。
#### Buffer reset()
将位置设置到标记
#### int remaining()
返回界限与位置之间的差值
#### int position()
##### void position(int newValue)
返回或设置位置
#### int capacity()
返回缓冲区的容量