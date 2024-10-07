# Properties 
类
### 构造器
#### Properties()
创建一个空的属性映射
#### Properties(Properties defaults)
用一个默认值映射创建一个空的属性映射
### 实例方法
#### String getProperty(String key,?Sting defaultValue)
获取value，如果键值对未在表中，则在默认表中查找。如果都没有，返回null
#### Object setProperty(String key,String value)
设置属性。返回key之前关联的值
#### Set\<String> stringPropertyNames()
返回所有键，包含默认映射
#### void load(Reader in) throws IOException
从in加载一个属性映射
#### void store(Write out,String header)
将属性映射保存到out中。header是所存储文件第一行的注释。