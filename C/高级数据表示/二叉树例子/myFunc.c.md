```
#include "myFunc.h"

//增删改查

//初始化tree
void InitiallzationTree(Tree* tree)
{
	tree->root = NULL;
}
//检查队列有没有到达设置的上限，或者到达栈的大小
bool TreeIsFull(const Tree* tree, int size)
{
	if (tree->Count >= size)
		return true;

	Tree* temp = (Tree*)malloc(sizeof(Tree));
	if (temp == NULL)
	{
		fprintf(stderr, "栈满");
		return true;
	}
	free(temp);
	return false;
}

//检查树是否为空
bool TreeIsEmpty(const Tree* tree)
{
	if (tree->root == NULL)
		return true;
	return false;
}
//返回节点数量
int TreeCount(const Tree* tree)
{
	return tree->Count;
}
static void CopyToTrnode(Message m, TrNode* node)
{
	node->m = m;
}
static void CopyToMessage(Message* m, TrNode* node)
{
	*m = node->m;
}
bool TreeAdd(Message m, Tree* tree)
{
	//为节点分配空间
	TrNode* node = (TrNode*)malloc(sizeof(TrNode));
	
	//将临时指针指向树的根节点
	TrNode* temp = tree->root;
	//父节点
	TrNode* parent = NULL;
	//检查分配空间是否成功
	if (!node)
	{
		fprintf(stderr, "栈满");
		return false;
	}

	//初始化节点
	CopyToTrnode(m, node);
	node->left = NULL;
	node->right = NULL;

	while (temp)
	{
		if (node->m.value > temp->m.value)
		{
			parent = temp;
			temp = temp->right;
		}
		else if (node->m.value < temp->m.value)
		{
			parent = temp;
			temp = temp->left;
		}
		else
		{
			if (node->m.value == temp->m.value)
			{
				fprintf(stderr, "此值已存在，无法重复储存！\n");
				return false;
			}
		}
	}
	if (DetermineRootNode(node, temp, parent, tree))
		;
	else
	{
		fprintf(stderr, "添加失败！\n");
	}
	return true;
}
bool DetermineRootNode(TrNode* node, TrNode* temp, TrNode* parent, Tree* tree)
{
	if (!temp)
	{
		//当二叉树为空时
		if (TreeIsEmpty(tree))
		{
			tree->root = node;
			parent = tree->root;
		}
		//根节点的子节点都为NULL时
		if ((!parent->left) && (!parent->right))
		{
			if (node->m.value > parent->m.value)
				parent->right = node;
			else if (node->m.value < parent->m.value)
				parent->left = node;
		}
		//根节点的左右节点都不为NULL时
		else if (parent->left && parent->right)
		{
			if (parent->left == temp)
				parent->left = node;
			else if (parent->right == temp)
				parent->right = node;
		}
		//根节点的子节点只有一个为NULL时
		else if (parent->left)
			parent->right = node;
		else if (parent->right)
			parent->left = node;
		return true;
	}
	return false;
}
bool TreeDel(Message message, Tree* tree)
{
	TrNode* temp, * parent;
	temp = tree->root;
	parent = NULL;

	while (temp)
	{
		if (message.value > temp->m.value)
		{
			parent = temp;
			temp = temp->right;
		}
		else if (message.value < temp->m.value)
		{
			parent = temp;
			temp = temp->left;
		}
		//找到需要删除的值
		else
			break;
	}
	if (temp)
	{
		//获取目标节点的左右节点
		TrNode* left, * right;
		left = temp->left;
		right = temp->right;

		//检测目标节点是父节点的左右节点
		if (temp == parent->left)
		{
			//释放目标节点
			free(temp);
			//必须重新初始化，不然下面的while语句无法检测出temp是否因left为NULL而无法获取最右节点
			temp = NULL;
			

			//遍历以左节点为根的所有右节点，让temp抵达最右节点
			//left不能为NULL
			if (left != NULL)
			{
				//让原目标节点的地址指向原目标的左节点
				parent->left = left;
				//遍历以左节点为根的所有右节点，让temp抵达最右节点
				temp = left->right;
			}
			//如果left为NULL且right不为NULL时，将原目标节点指向right
			else if(right != NULL)
			{
				parent->left = right;
				temp = right->right;
			}
			while (temp)
			{
				temp = temp->right;
			}
			//将最右节点指向原目标的右节点
			temp = right;
		}
		else if (temp == parent->right)
		{
			//释放目标节点
			free(temp);
			temp = NULL;
		

			if (left)
			{
				//让原目标节点的地址指向原目标的左节点
				parent->left = left;
				// 遍历以左节点为根的所有右节点，让temp抵达最右节点
				temp = left->right;
			}
			//如果left为NULL且right不为NULL时，将原目标节点指向right
			else if(right)
			{
				parent->right = right;
				temp = right->right;
			}
			while (temp)
			{
				temp = temp->right;
			}
			//右手树的左节点需要不为NULL才可以执行以下代码
			if (left)
			{
				//将最右节点指向原目标的右节点
				temp = right;
			}
		}
	}
	else
	{
		fprintf(stderr, "要删除的节点不存在！\n");
		return false;
	}
	return true;
}

void DisplayTree(Tree* tree)
{
	DisplayTrNode(tree->root);
}
void DisplayTrNode(TrNode* node)
{
	printf("Node:\t%d\n", node->m.value);
	//先进入该节点的左节点
	if (node->left)
	{
		DisplayTrNode(node->left);
	}
	if (node->right)
	{
		DisplayTrNode(node->right);
	}
}

```