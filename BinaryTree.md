```c++
#include<stdio.h>
#include<iostream>
using namespace std;

//构建二叉树的数据结构
typedef struct BitNode {
	int data;
	struct BitNode *lchild;
	struct BitNode *rchild;
}BitNode,*BiTree;


//初始化二叉树
void BiTreeInit(BiTree &T){
	int key;
	printf("请输入关键字\n");
	scanf("%d",&key);
	if(key==0){//给关键字0说明是空 
		T = NULL;
	}
	else {
		T = (BiTree)malloc(sizeof(BitNode));
		if(!T){
			exit(OVERFLOW);
		}
		T->data = key;
		BiTreeInit(T->lchild);
		BiTreeInit(T->rchild);	
	}
} 


//实现前序遍历(递归)
void PreOrder_1(BiTree T){
	if(T!=NULL)
	{
		printf("%d ",T->data);
		PreOrder_1(T->lchild);//遍历左子树
		PreOrder_1(T->rchild);//遍历右子树 
	}
}

//实现前序遍历(非递归)
void PreOrder_2(BiTree T){
	//利用栈实现
	BitNode *p = T;
	BitNode *arr[100];//调用栈
	int top=-1;//栈顶指针
	while(p||top!=-1){//当树不为空或者栈里面还有结点时继续循环 
		while(p){
			//查找左子树
			printf("%d ",p->data);
			arr[++top] = p;
			p = p->lchild; 
		}
		//退出循环后说明该找右子树
		p = arr[top--];//原先的结点出栈
		p = p->rchild; //查看右子树 
	} 
}



//实现中序遍历(递归)
void MidOrder_1(BiTree T){
	if(T!= NULL){
		MidOrder_1(T->lchild);//先找左子树 
		printf("%d ",T->data);
		MidOrder_1(T->rchild);//后找右子树 
	}
} 

//实现中序遍历(非递归)
void MidOrder_2(BiTree T){
	//利用栈实现
	BitNode *p = T;
	BitNode *arr[100];//调用栈
	int top=-1;//栈顶指针
	while(p||top!=-1){//当树不为空或者栈里面还有结点时继续循环 
	    while(p){
			//查找左子树
			arr[++top] = p;
			p = p->lchild; 
		}
		//退出循环后说明该找右子树
		p = arr[top--];//原先的结点出栈
		printf("%d ",p->data);
		p = p->rchild; //查看右子树 
    }
}



//实现后序遍历(递归)
void InOrder_1(BiTree T){
	if(T!= NULL){
		MidOrder_1(T->lchild);//先找左子树 
		MidOrder_1(T->rchild);//后找右子树 
		printf("%d ",T->data);
	}
} 

//实现后序遍历(非递归)
void InOrder_2(BiTree T){
	//利用栈实现
	BitNode *p = T;
	BitNode *arr[100];//调用栈
	int top=-1;//栈顶指针
	BitNode *temp = NULL;//临时保存结点 
	while(p||top!=-1){//当树不为空或者栈里面还有结点时继续循环 
	    while(p){
			//查找左子树
			arr[++top] = p;
			p = p->lchild; 
		}
		//退出循环后说明该找右子树
		p = arr[top--];//原先的结点出栈
		if(p->rchild==NULL||p->rchild=temp)
		{
			printf("%d ",p->data);
			temp = p;
			p = NULL;//置空，防止再次查找p的左子树 
		}
		else {
			arr[++top] = p;
			p = p->rchild;
		}
    }
}


//实现层序遍历  
void LevelOrder(BiTree T)
{
	BiTree queue[100];//利用队列，先进先出。
    int i=0,j=0;//i为队尾，j为队尾 
    queue[i++]=T;
    while(i>j)
    {
        if(queue[j])
        {
            visit(queue[j]);
            queue[i++]=queue[j]->lchild;
            queue[i++]=queue[j]->rchild;
        }
        j++;
    }
}


//Morris 遍历(线索二叉树)
void InOrder_Morris(BiTree T){
	if(T == NULL)
	{
		return;
	}
	BitNode *mostRight;
	while(T!=NULL)
	{
		mostRight = T->lchild;
		if(mostRight != NULL){//当前结点存在左孩子 
			while(mostRight->rchild != NULL&&mostRight->rchild != T)//右孩子存在且不是后继 
			{
				mostRight = mostRight->rchild;
			}
	        if(mostRight->rchild = NULL)//未利用的空指针 
	        {
	        	mostRight->rchild = T;
	        	T = T->lchild;
	        	continue;
			}
			else {
				mostRight->rchild = NULL;//恢复 
				printf("%d ",T->data);
			}
		}
		else {//不存在左孩子，直接打印
			printf("%d ",T->data);
		}
		//走向右孩子
		T = T->rchild; 
	}
	//算法利用了空闲的右孩子指针，将空间复杂度降至O(1) 
}
```
