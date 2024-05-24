以下两个函数的原型均来自与stdlib.h
	rand()根据种子生成一个0~RAND_MAX之间
	srand()用于设置种子

time.h
	可以使用time()来做种子
	用time()返回的类型名为time_t，需要强制类型转换