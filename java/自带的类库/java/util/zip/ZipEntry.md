### 构造器
#### ZipEntry(String name)
用name构建一个ZIP项
#### long getCrc()
返回用于这个`ZipEntry`的CRC32校验和的值。
#### String getName()
返回这一项的名字
#### long getSize()
返回这一项未压缩的尺寸，或者在未压缩尺寸不可知时返回-1
#### isDirectory()
当这一项是文件夹时返回`true`
#### void setMethod(int method)
设置用于这一项的压缩方法，必须是`DEFLATED`或`STORED`
#### void setSize(long size)
设置这一项的尺寸，只有在压缩方法是`STORED`时才必需的。
#### setCrc(long crc)
给这一项设置CRC32校验和，这个校验和是使用CRC32类计算的。只有在压缩方法为STORED时才是必需的。