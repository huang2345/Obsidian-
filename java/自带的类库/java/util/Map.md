# Map\<K,V>
接口
#### V get(Object key)
获取值。如果再映射中没有找到该key，返回null
#### default V getOrDefault(Object key,V defaultValue)
如果没有找到key，将会返回defaultValue。
#### V put(K key,V value)
设置键值对。如果该键已经存在，会更新value并返回旧value。如果该键不存在，返回null。
#### void putAll(Map\<? extends K,? extends V> entries)
将指定的映射中的所有键值对添加到当前Map中
#### boolean containsKey(Object key)
如果Map中有该键返回true
#### boolean containsValue(Object value)
如果Map中有该值，返回true
#### default void forEach(BiConsumer\<? super K,? super V> action)
对所有键值对使用该动作