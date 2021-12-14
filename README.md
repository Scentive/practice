/*# COD
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    int length;
    char *ch = {"ASDFG\n"};
    printf("%d\n",strlen(ch));
    return 0;
}*/



#include <stdio.h>
struct student{       /*学生信息结构定义*/
  int num;            /* 学号 */
  char name[10];      /* 姓名 */
  int math, english, computer;   /* 三门课程成绩 */
};
int update_score(struct student *p, int n, int num, int course, int score); /*函数声明*/

int main(void)
{
  int i, pos, n, num, course, score;
  struct student students[50];   /* 定义结构数组 */
  scanf("%d", &n);
  for(i = 0; i < n; i++){
    scanf("%d", &students[i].num);
    scanf("%s", students[i].name);
    scanf("%d", &students[i].math);
    scanf("%d", &students[i].english);
    scanf("%d", &students[i].computer);
  }

  /* 输入待修改学生信息 */
  scanf("%d", &num);
  scanf("%d", &course);
  scanf("%d", &score);

  /*调用函数，修改学生成绩*/
  pos = update_score(students, n, num, course, score);

  /*输出修改后的学生信息*/
  if(pos == -1)
    printf("Not found!\n");
  else
  {
    printf("%d,%d,%d,%d\n", students[pos].num, students[pos].math, students[pos].english, students[pos].computer);
  }
  return 0;
}
/* 请在这里填写答案 */
int update_score(struct student *p, int n, int num, int course, int score)
{
    int i;
    for (i=0;i<n;i++)
    {
        if ((p+i)->num==num)
        {
            switch(course)
            {
                case 1:(p+i)->math=score;
                break;
                case 2:(p+i)->english=score;
                break;
                case 3:(p+i)->computer=score;
                break;
            }
            return 1;
        }
    }
    return -1;
}








#include <stdio.h>
#include <math.h>

#define epsilon 1e-8

int RealNe(double x, double y);

int main()
{
    double a, b;
    scanf("%lg%lg", &a, &b);
    if (RealNe(a, b))
    {
        puts("Yes");
    }
    else
    {
        puts("No");
    }
    return 0;
}
/* 请在这里填写答案 */
int RealNe(double x, double y)
{
    if (fabs(x-y)<epsilon)
        return 0;
    else
        return 1;
}








#include <stdio.h>
#define N 30
struct student                    
{
    int num;
    char name[10];
    float score[4];
    float sum;
};
void calc(struct student *p,int n);     
void sort(struct student *p,int n);
int main()
{
    struct student stu[N];
    int i,j,n;
    float f;
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        scanf("%d%s",&stu[i].num,stu[i].name);
        for(j=0;j<4;j++)
        { 
            scanf("%f",&f);
            stu[i].score[j]=f;
        }
    }
    calc(stu,n);
    sort(stu,n);
    for(i=0;i<n;i++)
    {
        printf("%5d%10s",stu[i].num,stu[i].name);
        printf("%5.1f%5.1f%5.1f%5.1f%7.1f\n",stu[i].score[0],stu[i].score[1],stu[i].score[2], stu[i].score[3],stu[i].sum);
    }
    return 0;
}
/* 请在这里填写答案 */
void calc(struct student *p,int n)
{
    int i,j;
    for (i=0; i<=n; i++)
    {
        for (j=0; j<4; j++)
        {
            p[i].sum+=p[i].score[j];
        }

    }
}

void sort(struct student *p,int n)
{
    int i,j;
    for (i=0; i<n-1; i++)
    {
        for (j=i+1; j<n; j++)
        {
            if (p[i].sum<p[j].sum)
            {
                struct student tmp=p[i];
                p[i]=p[j];
                p[j]=tmp;
            }
        }
    }
}


#include <stdio.h>
#include <math.h>

#define epsilon 1e-8

int RealGe(double x, double y);

int main()
{
    double a, b;
    scanf("%lg%lg", &a, &b);
    if (RealGe(a, b))
    {
        puts("Yes");
    }
    else
    {
        puts("No");
    }
    return 0;
}
/* 请在这里填写答案 */
/*请编写函数，判断一个实数大于等于另一个实数。*/
int RealGe(double x, double y)
{
    if(x>=y)
        return 1;
    else
        return 0;
}







#include <stdio.h>

void PrintTrg(char symbol,int height);

int main()
{
    int n;
    char s;
    scanf("%c %d", &s,&n);
    PrintTrg(s, n);
    return 0;
}
/* 请在这里填写答案 */
void PrintTrg(char symbol,int height)
{
    int i,j;
    if(height<=0)
        printf("Input Error!");
    for (i=0; i<height; i++)
    {
        for(j=0; j<i; j++)
        {
            printf(" ");
        }
        for (j=i; j<height; j++)
        {
            printf("%c",symbol);
        }
        if(i<height-1)
            printf("\n");
    }
}
