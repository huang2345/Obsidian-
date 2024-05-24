	//strlen()，获取字符串长度，不包含结束字符'\0'
	
	//void strcat(str1,str2)在str1后添加str2,str1可能引发下标溢出错误
	
	//strncat(str1,str2,Str1Size)相比strcat在添加一个参数指定最大添加字符
	
	//strcmp比较字符串，相同返回0，反之为非0
	
	//strncmp与strcmp相比增加一个参数，用以指定在str1和str2之间一共只比较多少字符
	
	//strcpy(目标字符串，源字符串)
	
	//strncpy(目标字符串，源字符串，限制被拷贝字符数)防止下标溢出，但是可能造成char[]没有空字符
	//strncpy_s(目标字符串, 目标字符串大小, 源字符串, 限制字符);
	
	//sprintf(目标字符串，格式字符，待写入项列表)该函数将数据写入字符串
	
	//strchr(被查找字符串str，被查找字符ch)该函数返回查找str中第一个被找到的ch的地址
	
	//strpbrk(str1,str2),str1中是否包含str2,如果包含返回str1的指针，反之返回空指针
	
	//strrchr(str,ch)返回str中最后一个ch的地址
	
	//strstr(str1,str2)返回str1中第一个str2的地址