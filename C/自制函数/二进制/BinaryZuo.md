该函数将数字x移动location个位，并将移动导致溢出的位重新在右边按顺序重新打开
但由于位溢出后没有遗失，而是增加了位数，暂时想不到限制位数的方法。
由于上述原因，输入00010000，移动4位，设想应该是00000001,
但实际是000100000001
```
unsigned int BinaryZuo(unsigned int x, int location)
{
	unsigned int mark = 00000000;

	if (location)
	{
		for (int i = location; i > 0; i--)
		{
			switch (i-1)
			{
			case 0:
				mark |= 128;
				break;
			case 1:
				mark |= 64;
				break;
			case 2:
				mark |= 32;
				break;
			case 3:
				mark |= 16;
				break;
			case 4:
				mark |= 8;
				break;
			case 5:
				mark |= 4;
				break;
			case 6:
				mark |= 2;
				break;
			case 7:
				mark |= 1;
				break;
			}
		}
		//获取x中要被移动位导致值被丢弃的值
		mark &= x;
		//移动位
		x <<= location;
		//将mark中获取的被丢弃的值向x移动的反方向移动相同的位数，以实现将被丢弃的位值重新在x中打开
		mark >>= location;
		//在右边打开被丢弃的位值
		x |= mark;
	}
	return x;
}
```