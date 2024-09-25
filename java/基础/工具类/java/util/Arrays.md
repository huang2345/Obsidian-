### 静态方法
#### String toString(xxx\[] a)
将数组转换为字符串
##### String deepToString(xxx\[] a)
多维数组专用版
#### xxx\[] copyOf(xxx\[] a,?int start,int end)
拷贝数组a中对应范围的元素
#### void sort(Object\[] a)
对数组a进行快排，要求数组元素的类型必须属于实现了`Comparable`接口的类
#### void sort(xxx\[] a)
对数组a进行快排
#### int binarySearch(xxx\[] a,?int start,?int end,xxx v)
使用二分法在有序数组a中查找值v。如果找到返回对应的index；否则，返回一个负数r。-r-1是v应插入的位置
#### void fill(xxx\[] a,xxx v)
将数组所有元素填充为v
#### boolean equals(xxx\[] a,xxx\[] b)
比较两个数组，如果相同返回true
#### equals(xxx\[] a)
检查对应的数组元素是否相同，相同返回true
#### deepEqualsK(xxx\[] a)
equals无法应对多维数组时每一层级的元素，该方法专对于多维数组使用。