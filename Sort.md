```c++
#include<stdio.h>
#include<iostream>
using namespace std;
//实现插入排序
void InsertSort(int *a,int len)
{
	//基本思路，先将数组看成一个已排序好的元素和剩余元素，再将余下元素一个个的插入到排好的元素中
	int i,j;
	int temp; // 保存待插入的元素
	for(i=1;i<len;i++)
	{//将第一个元素看作有序 
		temp = a[i];//存入待插入元素
		j = i-1;
		while(j>=0&&a[j]>temp)
		{
			a[j+1]=a[j];
			j--;
		 } 
		a[j+1]=temp;//插入元素 
	} 
 } 
 //时间复杂度o(n^2) 是一种稳定的排序算法
 
 
 
 
//实现堆排序
//首先写一个构造大根堆的函数
void HeapCreate(int *arr,int l,int r)
{
	//将arr[l..r] 变成大根堆
	int temp = arr[l];
	for(int i=2*l+1;i<=r;i*=2)//数组下标从0开始，故左孩子为2*l+1 
	{
		if (i<r&&arr[i+1]>arr[i])//右孩子更大 
		{
			i++;
		}
		if(temp>arr[i])
		{
			break;
		}
		arr[l] = arr[i];
		l = i;
	 } 
	arr[l] = temp;
} 

void HeapSort(int *arr,int len)
{
	for(int i=len/2;i>=0;i--)
	{
	    HeapCreate(arr,i,len-1);//只需利用有孩子的结点构建大根堆 
	}
	for(int i=len-1;i>0;i--)
	{
		swap(arr[0],arr[i]);
		HeapCreate(arr,0,i-1);//其余的继续构成大根堆 
	}
}
//时间复杂度 o(nlogn) 是一种不稳定的算法 


//实现快速排序 
//先编写一个获取排序后轴枢位置的函数
int Partition(int *a,int l,int r)
{
	int key = a[l];//轴枢选为第一个元素
	while(l<r)
	{
		while(l<r&&a[r]>key)
		{
			r--;
		}
		swap(a[l],a[r]);
		while(l<r&&a[l]<key)
		{
			l++;
		}
		swap(a[l],a[r]);
	 }//循环结束时轴枢已经处在适当位置 
	return l;
 } 

void QuickSort(int *a,int start,int end)
{
	int key;
	//采用递归函数，终止条件时start>end
	if(start<end)
	{
		key = Partition(a,start,end);
		QuickSort(a,start,key-1);//排左边 
		QuickSort(a,key+1,end);//排右边 
	 } 
}
//时间复杂度o(nlogn) 一般轴枢位置能够处在数组中间附近能达到较低的时间复杂度 是一种不稳定的排序算法


//实现归并排序(非递归)
void Merge(int *s,int *f,int l,int m,int n)
{
	//函数作用：将s[l..m]和s[m+1..n]归并为f[l..n] 
	int i,j,k=l;
	for(i=l,j=m+1;i<=m&&j<=n;k++)
	{
		if(s[i]<s[j])
		{
			f[k]=s[i++];
		}
		else{
			f[k]=s[j++];
		}
	}
	int p;
	if(i<=m){//左边数更多则执行 
		for(p=0;p<=m-i;p++)
		{
			f[k+p]=s[i+p];
		}
	}
	if(j<=n){//右边数更多则执行 
		for(p=0;p<=n-j;p++)
		{
			f[k+p]=s[j+p];
		}
	}
}

void MergeSort(int *a,int *b,int start,int end)
{
	int mid;
	int t[end+2];
	if(start==end)
	{
		b[start]=a[start];
	}
	else {
		mid = (start+end)/2;
		MergeSort(a,t,start,mid);
		MergeSort(a,t,mid+1,end);
		Merge(t,b,start,mid,end);
	}
}
//时间复杂度 o(nlogn) 但会占用较多空间 o(n+logn) 是一种稳定的排序算法 

int main(){
    int a[10]={7,1,9,4,3,5,6,0,8,2};
	//MergeSort(a,a,0,9);
	QuickSort(a,0,9);
	//HeapSort(a,10);
	//InsertSort(a,10);
	for(int i =0;i<10;i++)
	{
		printf("%d",a[i]);
	}
	return 0;
}
```
