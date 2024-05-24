
| src      |                                                  |
| -------- | ------------------------------------------------ |
| control  | 该属性启用浏览器自带的视频控制界面，提供暂停、进度调节等功能                   |
| autoplay | 自动播放                                             |
| loop     | 单曲循环                                             |
| muted    | 默认静音                                             |
| poster   | 在视频播放前的预览图片（视频封面）                                |
| preload  | 缓冲，“none"：不缓冲，"auto"页面加载后缓冲，"metadata"：仅缓冲文件的元数据 |
|          |                                                  |


\<source\>该单标签为一个视频/图片提供不同的格式，使使用不同设备不同浏览器的用户可以正常播放，
	source有两个常用属性，src和type，通过在type中指明类型快速让浏览器过滤掉无法使用的格式

- [`<audio>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/audio) 元素不支持 `width`/`heigth` 属性——由于其并没有视觉部件，也就没有内容要设置 `width`/`height`。
- 它同时也不支持 `poster` 属性——同样，因为没有视觉部件。

# 字幕
	使用WebVTT文件格式和<track>元素

WebVTT 是一个格式，用来编写文本文件，这个文本文件包含了众多的字符串，这些字符串会带有一些元数据，它们可以用来描述这个字符串将会在视频中显示的时间，甚至可以用来描述这些字符串的样式以及定位信息（尽管有限制）。这些字符串叫做 **cue** ，你可以根据不同的需求来显示不同类型的 cue，最常见的如下：

| [subtitles](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content#subtitles)                       | 外语材料的翻译字幕，来帮助那些听不懂音频中说的什么的人理解音频当中的内容。       |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [captions](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content#captions)                         | 同步翻译对白，或是描述一些有重要信息的声音，来帮助那些不能听音频的人理解音频中的内容。 |
| [定时描述](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content#%E5%AE%9A%E6%97%B6%E6%8F%8F%E8%BF%B0) | 由媒体播放器朗读的文本，其向盲人或其他视力受损用户描述重要的视觉内容。         |

1. src属性指定链接的.vtt文件
2. \<track\>标签位于 `<audio>` 或 `<video>` 标签当中，在所有`<source>`之后
3. 用`kind`属性来指明是声明类型的`cue`,然后用`srclang`告诉浏览器该字幕是什么语言，添加`label`帮助读者在查找时识别语言