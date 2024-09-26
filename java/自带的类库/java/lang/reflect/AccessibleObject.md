### 实例方法
#### void setAccessible(boolean flag)
设置或取消这个对象的可访问标志，如果拒绝访问会抛出一个`IllegalAccessException`异常
#### boolean trySetAccessible()
为这个对象设置可访问标志，如果拒绝访问则返回false
#### boolean canAccess(Object obj)
检查能否通过这个字段、方法或构造器对象来访问obj对象中对应成员的具体值。
>即：在obj中有无这个字段的可访问标志

### 静态方法
#### void setAccessible(AccessibleObject\[] array,boolean flag)
用于批量设置可访问权限。