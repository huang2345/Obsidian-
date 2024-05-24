stdlib.h
//malloc(所需内存)
//calloc(存储单元数量,存储单元大小)

	int* ptr = malloc(sizeof(int) * 10);
	.....
	free(ptr);

	int* ptr = calloc(10,sizeof(int));
	.....
	free(ptr);