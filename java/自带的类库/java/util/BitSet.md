# BitSet
Java的BitSet类会存储一个位序列。BitSet类提供了一个用于读取、设置或重置位的很方便的接口。通过这个接口可以避免掩码和其他调整位的操作，如果将位存储在整形中就必须做这些繁琐的操作
### 构造器
#### BitSet(int initialCapacity)
构造一个位集。
### 实例方法
#### int cardinality()
返回设置的位数
#### int length()
返回位集的“逻辑长度”
#### int size()
返回当前可用的位数

#### boolean get(int bit)
获取位
#### boolean set(int bit)
设置位为1
#### boolean clear(int bit)
设置位为0

#### void and(BitSet set)
#### void or(BitSet set)
#### void xor(BitSet set)
与另一个位集进行逻辑“与”、“或”、“异或”
#### void andNot(BitSet set)
对应set位集中设置为1的位，清除为0
#### IntStream stream()
