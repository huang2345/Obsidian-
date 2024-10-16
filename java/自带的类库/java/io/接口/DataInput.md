#### boolean readBoolean()
#### byte readByte()
#### char readChar()
#### double readDouble()
#### float readFloat()
#### int readInt()
#### long readLong()
#### short readShort()
读取一个给定类型的值

#### void readFully(byte\[] b)
将字节读取到数组`b`中，期间阻塞直到所有字节都读入。
#### void readFully(byte\[] b,int off,int len)
将`len`大小的字节放置在数组`b`的`off`索引开始的位置，期间阻塞直到所有字节都读入。
#### String readUTF()
读入由“Java修订过的UTF-8”格式的字符构成的字符串
#### int skipBytes(int n)
跳过`n`个字节，期间阻塞直到所有字节都被跳过。