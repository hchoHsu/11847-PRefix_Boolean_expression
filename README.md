```c
#include <stdio.h>

int pos = 0;
char expr[50];
int boolval[4] = {0};

int evalBoolExpr(){
    char c = expr[pos++];
    if(c >= 'A' && c <= 'D'){
        return boolval[(int)(c - 'A')];
    }
    else if(c == '&' || c == '|'){
        int op1 = evalBoolExpr();
        int op2 = evalBoolExpr();
        if(c == '&') return (op1 && op2);
        else if(c == '|') return (op1 || op2);
    }
}
int main()
{
    scanf("%s", expr);
    for(int i = 0; i < 4; i++) boolval[i] = 0;
    
    for(int i = 0; i < 16; i++){
        pos = 0;
        int n = i, k = 3;
        while(n != 0){
            boolval[k--] = n % 2;
            n /= 2;
        }
        for(int j = 0; j < 4; j++) printf("%d ", boolval[j]);
        printf("%d\n", evalBoolExpr());
    }

    return 0;
}
```
