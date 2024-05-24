fopen()在vs默认无法使用
fopen_s(存储文件信息的指针的地址，文件名，打开模式)

	例子：
	FILE* fp;
	fopen_s(&fp,"test.txt","r");

	fopen_s成功返回0，失败非0

getc(获取的流) putc(输出字符，被输入的流)

rewind(指针)
重置文件指针位置，
fclose()关闭流，成功返回0，否则返回EOF

	stdin    stdout    stderr

fprintf(输出流，被输出的字符串)
fscanf(获取流，转义字符，被输入的流)

fgets(存储数据的char数组，char数组大小，获取的流)

	成功：返回指向该串的指针，
	失败或读到文件结尾返回空指针
fputs(被输入的字符串，被输入的文件)

	//fgets保留了换行符，fputs不会加换行符

fread(被输入的数组，数据块大小，数据块数量，文件流)
fwrite(被输出的数组，数据块大小，数据块数量，文件流)

	这两个函数的返回值相似，正常情况下返回数据块数量，错误时返回的数据小于数据块数量

fseek(被使用的文件流，从起始点开始移动的距离，设置起始点)
	
	//SEEK_SET开始    SEEK_CUR现在    SEEK_END结尾
	如果正常，fseek()的返回值为0，如果bug，返回值-1

ftell(文件)

	//返回距文件开始处到当前位置的字节数，以此确定文件的位置
	//如果失败返回-1，大概率为文件超过2GB
	//在二进制模式下，换行为\r\n

	//（fgetpos和fsetpos）与（fseek和ftell）之间的差别是前者能对更大的文件使用，而后者最多只能对2GB左右的文件使用

fgetpos(代查找的文件，fpos_t * pos)
	该函数会将fpos_t类型的值指向第二个参数
	成功返回0，失败非0
fsetpos(被使用的文件流，fpos_t * pos)
	使用指针pos指向的fpos_t类型数值来设置文件指针指向偏移该值后的位置
	成功返回0，失败返回非0

ungetc(int数据，流)
	//将指定的字符放回流
	//只能放回一个字符，直到下次读取
	//如果错误返回EOF

fflush(文件流fp)
	将输出缓冲区中所有未写入数据写入被fp指定的输出文件
	如果fp == NULL，可以起到刷新缓冲区的作用

setvbuf(要使用缓冲区的文件流fp，char数组缓冲区buf，缓冲模式mode，缓冲区buf大小)

	如果buf == NULL，该函数会自动分配一个缓冲区

mode：
	_IOFBF 完全缓冲
	_IOLBF 行缓冲
	_IONBF 无缓冲

	成功返回0，失败非0

size_t    fwrite(被输出的数据，数据块大小，数据块数量，被输入流)
	正常返回值是数据块的数量，如果写入错误会小于该值

size_t    fread(存放数据的地址，数据块大小，数据块数量，输出流)
	与fwrite相同
	
	//fwrite和fread的返回值均为size_t，通常是unsigned int

feof(被检查的流)
ferror(被检查的流)

	feof ：如果上一次该文件流输入调用检测到文件结尾时，返回非0，否则返回0
	ferror：如果文件流输入调用时出现读或写错误，返回非0，否则0

