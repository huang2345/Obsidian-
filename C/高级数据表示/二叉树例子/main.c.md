```
#include "myFunc.h"
int main()
{
	Tree tree;
	InitiallzationTree(&tree);

	for (int i = 0; i < 10; i++)
	{
		Message message = MessageCreate(i);

		TreeAdd(message, &tree);
	}
	TreeAdd(MessageCreate(-1), &tree);
	TreeAdd(MessageCreate(-2), &tree);
	DisplayTree(&tree);
}

```