# PAT-Basic-1009-
# 给定一句英语，要求你编写程序，将句中所有单词的顺序颠倒输出。

输入格式：测试输入包含一个测试用例，在一行内给出总长度不超过80的字符串。字符串由若干单词和若干空格组成，其中单词是由英文字母（大小写有区分）组成的字符串，单词之间用1个空格分开，输入保证句子末尾没有多余的空格。

输出格式：每个测试用例的输出占一行，输出倒序后的句子。

输入样例：

Hello World Here I Come
输出样例：

Come I Here World Hello

#include <stdio.h>
#include <ctype.h>/*包含isspace函数*/ 
int main()
{
    char line[81], *p = line, *i;
    fgets(line, 81, stdin);/* char *fgets(char *str, int n, FILE *stream) 
	                       从指定的流 stream 读取一行，并把它存储在 str 所指向的字符串内。 
						   当读取 (n-1) 个字符时，或者读取到换行符时，或者到达文件末尾时，
						   它会停止，具体视情况而定。 */ 
    //stdin指标准输入，从键盘输入到缓冲区的东西 
	while(*++p);                                        /* go to the end of the string */
    while(p > line)
    {
        while(isspace(*--p));                          /* find the end of a word */
        /*int isspace(int c)用于检查所传字符是否是空白字符，若是则返回非零值*/ 
		while(p > line && !isspace(*(p - 1))) p--;      /* find the start of the word */         
        for(i = p; *i && !isspace(*i); putchar(*i++));  /* print the word */
        putchar(p == line ? '\0' : ' ');
    }
    return 0;
}
