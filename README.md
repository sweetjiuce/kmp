## kmp
在简单匹配算法中，当主串和子串比较不相等时，子串的字符指针总是在回溯到第一个字符，这是完全没必要的

```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
void fail(char *b,char *f)
{
	int l = strlen(b);
	f[0] = -1;
	int j = 0;
	int k = -1;
	while(j<l)
	{
		if(k == -1 || b[j] == b[k])
		{
			k++;
			j++;
			if(b[j] == b[k])
				f[j] = f[k];
			else
				f[j] = k;

		}
		else
			k = f[k];

	}
}
void kmp(char *a, char *b)
{
	int k=-1;
	int i = 0, j = 0;
	int la = strlen(a);
	int lb = strlen(b);
	char f[20];
	fail(b,f);
	while(i < la && j < lb )
	{
		if( j==-1 || a[i] == b[j])
		{
			i++;
			j++;

		}
		else
			j = f[j];
	}
	if(j == lb)
		printf("true\n");
	else
		printf("false\n");

}
int main(int argc, char const *argv[])
{
	char a[10];
	char b[5];
	scanf ("%s",a);
	scanf("%s",b); 
	kmp(a,b);
	return 0;
}
```
