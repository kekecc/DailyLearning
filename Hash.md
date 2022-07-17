```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
//采用链式法存储哈希表，防碰撞采用链地址法

typedef struct Hash_list{
	Hash_list *next;
	const char *key;//用于哈希函数获取位置 
	int value;//值 
}hash_list; 

//初始化哈希表
void Hash_Init(hash_list **HL, int len){
	for(int i=0;i<=len;i++)
	{
		HL[i] = (hash_list *)malloc(sizeof(hash_list));//分配空间
		HL[i]->next=NULL; //代表位置空闲 
	}
	HL[0]->value = len;//利用第一个结点存储长度 
}


int Hash(const char *str,hash_list **HL){//除留余数法 
	int ans=10,hash=0;
	while(*str!='\0')
	{
		hash=hash*ans+*str;
		str++;
	}
	return hash%(HL[0]->value)+1;
}


//向表中添加或者修改数据 
void HashSet(const char *str,int value,hash_list **HL){
	int i = Hash(str,HL);
	hash_list *p=HL[i];
	while(p->next)
	{
		if(strcmp(str,p->next->key)==0)//当前位置键值相同，则更新 
		{
			p->next->value = value;
			return;
		}
		else{//发生冲突则直接建立链表 
			p=p->next;
		}
	}
	//创建结点
	p->next = (hash_list *)malloc(sizeof(hash_list));
	p->next->value = value;
	p->next->key = str;
	p->next->next= NULL;
}

//删除数据
int HashDel(const char *str,hash_list **HL){
	int i = Hash(str,HL);
	hash_list *p=HL[i];
	hash_list *temp;
    while(p->next){
    	if(strcmp(str,p->next->key)==0)//找到位置 
    	{
    		temp = p->next;
    		p->next = temp->next;
    		free(temp);
    		return 0;
		}
		//当前位置不是
		p=p->next; 
	}
	return -1;
}

//查找数据
int HashSearch(const char *str,hash_list **HL){
	int i = Hash(str,HL);
	hash_list *p=HL[i];;
    while(p->next){
    	if(strcmp(str,p->next->key)==0)//找到位置 
    	{
    		return p->next->value;
		}
		//当前位置不是
		p=p->next; 
	}
	return -1;
}

//遍历哈希表
void HashTraverse(hash_list **HL){
	hash_list *p;
	for(int i=1;i<=HL[0]->value;i++)
	{
		printf("在位置%d的数据有: ",i);
		p=HL[i]->next;
		while(p){
			printf("%s %d ",p->key,p->value);
			p=p->next;
		}
		printf("\n");
	}
} 


int main(){
	//测试哈希功能
	int length;
	printf("请输入哈希表大小!\n");
	scanf("%d",&length);
	hash_list *HL[length+1];
	Hash_Init(HL,length);
	HashSet("hello",100,HL);
	HashSet("world",10,HL);
	HashSet("do",98,HL);
	HashSet("take",21,HL);
	HashSet("it",44,HL);
	HashSet("easy",33,HL);
	HashTraverse(HL);
	//HashDel("hello",HL);
	//HashTraverse(HL);
	return 0;
}

```
