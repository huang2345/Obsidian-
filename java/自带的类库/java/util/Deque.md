# Deque\<E>
接口，表示双端队列
#### void addFirst(E element)
#### void addLast(E element)
#### boolean offerFirst(E element)
#### boolean offerLast(E element)
将element添加到队头或队尾。如果队列已满，`addFirst`和`addLast`方法将抛出一个`IllegalStateException`，`offerFirst`和`offerLast`方法将返回false

#### E removeFirst()
#### E removeLast()
#### E pollFirst()
#### E pollLast()
删除并返回队头或队尾的元素。如果队列为空，`removeFirst`和`removeLast`将抛出一个`NoSuchElementException`，`pollFirst`和`pollLast`方法返回null

#### E getFirst()
#### E getLast()
#### E peekFirst()
#### E peekLast()
返回队头或队尾的元素。如果队列为空，`getFirst/Last`抛出一个`NoSuchElementException`，`peekFirst/Last`返回null
