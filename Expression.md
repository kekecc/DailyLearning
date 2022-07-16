```c++
//代码实现中缀表达式转后缀表达式
#include<cstdio>
#include<cstdlib>
#include<cstring>
#include<stack>
#include<iostream>
using namespace std;

int Isp(char ch){//栈内的优先级 
	switch(ch)
	{
		case '#': return 0;
		case '(': return 1;
		case '+': return 3;
		case '-': return 3;
		case '*': return 5;
		case '/': return 5;
		case ')': return 6;
	}
}

int Icp(char ch){//栈外的优先级 
	switch(ch)
	{
		case '#': return 0;
		case '(': return 6;
		case '+': return 2;
		case '-': return 2;
		case '*': return 4;
		case '/': return 4;
		case ')': return 1;
	}
}

int main(){
	string str;
	cin >> str ;// a+b*(c+d)
	stack<char> data;
	stack<char> expr;
	expr.push('#');//用于和其他符号比较
	str += '#';
	int ans=0;
	while(ans < str.size())
	{
		if(isalpha(str[ans]))//判断是否为字母，也可以改为数字 
		{
			data.push(str[ans]);
			cout<<data.top()<<" ";
			ans++;
		}
		else {//否则为运算符 
			if(Isp(expr.top())==Icp(str[ans]))//优先级相同 
			{
				expr.pop();//直接弹出
				ans++; 
			}
			else if(Isp(expr.top())<Icp(str[ans]))//栈外优先级高 
			{
				expr.push(str[ans]);//进栈  
				ans++; 
			}
			else {
				if(expr.top()==')')
				{
					expr.pop();//直接出栈 
				}
				else {
					cout<<expr.top()<<" ";//输出 
					expr.pop();
				}
			}
		}
	} 
}
```
