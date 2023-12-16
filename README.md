#include <stdio.h>
#include <math.h>
 
int prime( int p );
int PrimeSum( int m, int n );
    
int main()
{
    int m, n, p;
 
    scanf("%d %d", &amp;m, &amp;n);
    printf("Sum of ( ");
    for( p=m; p<=n; p++ ) {
        if( prime(p) != 0 )
            printf("%d ", p);
    }
    printf(") = %d\n", PrimeSum(m, n));
 
    return 0;
}

int prime( int p )
{
    int a=0;      
    if(p<2) return 0;                         // m<2时不是素数，直接返回0
    else if(p==2) return 1;                   //m=2时直接返回1
    else{
        for(int i=2;i<p;i++){                 // p 除以 2 ~ p-1 之间的所有整数，若能被整除，则 a+1
            if( p%i==0)
                a++;
        }
        //如果 a=0，说明在循环中没有任意一个整数能被 p 整除，即 p 是素数，返回 1
        if(a==0) return 1;
        //否则返回 0
        else return 0;
    }
 
}
 
int PrimeSum( int m, int n )
{
    int sum=0;
    if(m<0) m=2;
    for( m; m<=n; m++)
    {
        if(prime(m)==1)
            sum=sum+m;
    }
    return sum;
}
