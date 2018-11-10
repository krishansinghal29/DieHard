/*
// Sample code to perform I/O:

#include <iostream>

using namespace std;

int main() {
	int num;
	cin >> num;										// Reading input from STDIN
	cout << "Input number is " << num << endl;		// Writing output to STDOUT
}

// Warning: Printing unwanted or ill-formatted data to output will cause the test cases to fail
*/

// Write your code here
#include <iostream>
#include <bits/stdc++.h>
using namespace std;
struct node;
struct state{
    int m;
    int n;
    int o;
    int color;
    int h;
};
state arr[101][101][101];

class stackk 
{
   public:
      int top=-1;   // Length of a box
      int bot=0;
      //vector<int> st;  // Breadth of a box
      state* st[1000000];
      int empty(){
         if((top-bot)==-1){
             return 1;
         }
         else{
             return 0;
         }
      }
      state* pop(){
          if((top-bot)==-1){
             printf("Error");
          }
          else{
              top=top-1;
              state* out=st[top+1];//check
              //st.resize(top+1);
              return out;
          }
      }
      state* popbot(){
          if((top-bot)==-1){
             printf("Error");
          }
          else{
              bot=bot+1;
              state* out=st[bot-1];//check
              return out;
          }
      }
      void push(state * u){
          top=top+1;
          st[top]=u;
          //st.push_back(i);
          return ;
      }
};
int main(){
	int numtest;
	scanf("%d\n",&numtest);	
	for(int i=0 ;i<numtest;i++){
	    int s1,s2,s3;
	    scanf("%d %d %d\n",&s1,&s2,&s3);
	    int su1,su2,su3;
	    scanf("%d %d %d\n",&su1,&su2,&su3);
	    int total=su1+su2+su3;
	    for(int i=0;i<101;i++){
	        for(int j=0;j<101;j++){
	            for(int k=0;k<101;k++){
	                arr[i][j][k].color=0;
	                arr[i][j][k].m=i;
	                arr[i][j][k].n=j;
	                arr[i][j][k].o=k;
	                arr[i][j][k].h=1;
	            }
	        }
	    }
	    int test;
	    scanf("%d\n",&test);
	    
        stackk A;
        arr[su1][su2][su3].color=1;
        A.push(&arr[su1][su2][su3]);
        while((A.empty()!=1)){
            state* u=A.popbot();
            int i=u->m;int j=u->n;int k=u->o;
            if(i<=(s2-j)){
                if(arr[0][i+j][k].color==0){
                    arr[0][i+j][k].color=1;
                    arr[0][i+j][k].h=arr[i][j][k].h+1;
                    A.push(&arr[0][i+j][k]);
                }
            }
            else{
                if(arr[i-(s2-j)][s2][k].color==0){
                    arr[i-(s2-j)][s2][k].color=1;
                    arr[i-(s2-j)][s2][k].h=arr[i][j][k].h+1;
                    A.push(&arr[i-(s2-j)][s2][k]);
                }
            }
            if(j<=s1-i){
                if(arr[i+j][0][k].color==0){
                    arr[i+j][0][k].color=1;
                    arr[i+j][0][k].h=arr[i][j][k].h+1;
                    A.push(&arr[i+j][0][k]);
                }
            }
            else{
                if(arr[s1][j-(s1-i)][k].color==0){
                    arr[s1][j-(s1-i)][k].color=1;
                    arr[s1][j-(s1-i)][k].h=arr[i][j][k].h+1;
                    A.push(&arr[s1][j-(s1-i)][k]);
                }
            }
            if(i<=s3-k){
                if(arr[0][j][k+i].color==0){
                    arr[0][j][k+i].color=1;
                    arr[0][j][k+i].h=arr[i][j][k].h+1;
                    A.push(&arr[0][j][k+i]);
                }
            }
            else{
                if(arr[i-(s3-k)][j][s3].color==0){
                    arr[i-(s3-k)][j][s3].color=1;
                    arr[i-(s3-k)][j][s3].h=arr[i][j][k].h+1;
                    A.push(&arr[i-(s3-k)][j][s3]);
                }
            }
            if(k<=s1-i){
                if(arr[k+i][j][0].color==0){
                    arr[k+i][j][0].color=1;
                    arr[k+i][j][0].h=arr[i][j][k].h+1;
                    A.push(&arr[k+i][j][0]);
                }
            }
            else{
                if(arr[s1][j][k-(s1-i)].color==0){
                    arr[s1][j][k-(s1-i)].color=1;
                    arr[s1][j][k-(s1-i)].h=arr[i][j][k].h+1;
                    A.push(&arr[s1][j][k-(s1-i)]);
                }
            }
            if(k<=s2-j){
                if(arr[i][j+k][0].color==0){
                    arr[i][j+k][0].color=1;
                    arr[i][j+k][0].h=arr[i][j][k].h+1;
                    A.push(&arr[i][j+k][0]);
                }
            }
            else{
                if(arr[i][s2][k-(s2-j)].color==0){
                    arr[i][s2][k-(s2-j)].color=1;
                    arr[i][s2][k-(s2-j)].h=arr[i][j][k].h+1;
                    A.push(&arr[i][s2][k-(s2-j)]);
                }
            }
            if(j<=s3-k){
                if(arr[i][0][j+k].color==0){
                    arr[i][0][j+k].color=1;
                    arr[i][0][j+k].h=arr[i][j][k].h+1;
                    A.push(&arr[i][0][j+k]);
                }
            }
            else{
                if(arr[i][j-(s3-k)][s3].color==0){
                    arr[i][j-(s3-k)][s3].color=1;
                    arr[i][j-(s3-k)][s3].h=arr[i][j][k].h+1;
                    A.push(&arr[i][j-(s3-k)][s3]);
                }
            }
            if(arr[0][j][k].color==0){
                arr[0][j][k].color=1;
                arr[0][j][k].h=arr[i][j][k].h+1;
                A.push(&arr[0][j][k]);
            }
            if(arr[i][0][k].color==0){
                arr[i][0][k].color=1;
                arr[i][0][k].h=arr[i][j][k].h+1;
                A.push(&arr[i][0][k]);
            }
            if(arr[i][j][0].color==0){
                arr[i][j][0].color=1;
                arr[i][j][0].h=arr[i][j][k].h+1;
                A.push(&arr[i][j][0]);
            }
        }
	        
	    for(int i=0 ;i<test;i++){

	        int st1,st2,st3;
	        scanf("%d %d %d\n",&st1,&st2,&st3);
	        if(arr[st1][st2][st3].h!=1){
	            printf("%d\n",arr[st1][st2][st3].h);
	        }
	        else if(st1==su1&&st2==su2&&st3==su3){
	            printf("%d\n",arr[st1][st2][st3].h);
	        }
	        else{
	            printf("IMPOSSIBLE\n");
	        }
	    }
	}
	return 0;
}
