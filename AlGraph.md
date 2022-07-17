```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<malloc.h>


//有向图结构的定义 
	typedef struct ArcNode {         //表结点类型定义
   		 int adjvex;              //顶点位置编号 
    	 struct ArcNode  *nextarc;	   //下一个表结点指针
	} ArcNode;
	
	typedef struct VNode{				//头结点及其数组类型定义
   		 char data;       	//顶点信息
    	 ArcNode *firstarc;      	 //指向第一条弧
    	} VNode,AdjList[20];
    	
	typedef  struct {  //邻接表的类型定义
        AdjList vertices;     	 //头结点数组
        int vexnum,arcnum;   	  //顶点数、弧数  
       } ALGraph; 

bool visited[20];//保存顶点是否已读的信息 

void CreatG(ALGraph &G,char s[],int vn,int an){
	G.vexnum = vn;
	G.arcnum = an;
	for(int i=0;i<G.vexnum;i++)//输入边集数组 
	{
		G.vertices[i].data=s[i];
		G.vertices[i].firstarc=NULL;
	}
	for(int i=0;i<G.arcnum;i++)
	{
		int start,end;
		printf("请依次输入一条边的起点和终点!\n");
		scanf("%d %d",&start,&end);
		ArcNode *p= (ArcNode *)malloc(sizeof(ArcNode));
		p->adjvex = end;
		p->nextarc = G.vertices[start].firstarc;
		G.vertices[start].firstarc = p;
	}
}


void DFSTraverse(ALGraph G,int i)//遍历某个连通分量 
{
    ArcNode *p;
    visited[i]=true;
    printf("%d %c; ",i,G.vertices[i].data);
    p=G.vertices[i].firstarc;
    while(p)
    {
        if(!visited[p->adjvex])
        {
            DFSTraverse(G,p->adjvex);
        }
        p=p->nextarc;
    }
}

void DFS(ALGraph G){
    for(int i=0;i<G.vexnum;i++)//将所有边视为未读 
    {
        visited[i]=false;
    }
    for(int i=0;i<G.vexnum;i++)//对所有边进行遍历 
    {
        if(!visited[i])
        {
            DFSTraverse(G,i);
        }
    }
}


void BFS(ALGraph &G){//广度优先遍历 
	//利用队列
	int temp;
    ArcNode *p;
    int queue[20];//队列 
    int head=0,tail=0;//队首与队尾 
    for(int i=0;i<G.vexnum;i++)//视为未读 
    {
        visited[i]=false;
    }
    for(int i=0;i<G.vexnum;i++)
    {
        if(!visited[i])
        {
            visited[i]=true;
            printf("%d %c; ",i,G.vertices[i].data);
            queue[tail++]=i;//i对应的边进队
            while(head!=tail)
            {
                 temp=queue[head++];
                 p=G.vertices[temp].firstarc;
                 while(p)
                 {
                     if(!visited[p->adjvex])
                     {
                         visited[p->adjvex]=true;
                         printf("%d %c; ",p->adjvex,G.vertices[p->adjvex].data);
                         queue[tail++]=p->adjvex;//边进队 
                     }
                     p=p->nextarc;
                 }
            }

        }
    } 
}


int main(){
	char s[7]="ABCDEF";
	ALGraph G;
	printf("请输入边数!\n");
	int num;
	scanf("%d",&num);
	CreatG(G,s,6,num);
	//DFS(G);
	BFS(G);
	return 0;
}
```
