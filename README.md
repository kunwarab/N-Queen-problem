# N-Queen-problem
Backtracking problem-1
#include<bits/stdc++.h>
using namespace std;

int n;

vector<int> queens;

void printer(int level){
    cout<<"level : "<<level<<", queens : [";
    for(auto v:queens){
        cout<<v<<", ";
        }
    cout<<"]"<<endl;
}

bool check(int row,int col){
    for(int pr=0;pr<row;pr++){
        int pc = queens[pr];
        
        if(pc==col|| abs(pc-col)==abs(pr-row)){
            return false;
        }
    }
    return true;
}

int cnt = 0;

void rec(int level){ 
    if(level==n){
        cnt++;
        printer(level);
        return;
    }
    
    for(int col=0;col<n;col++){
        if(check(level,col)){ 
            queens.push_back(col);
            rec(level+1);
            queens.pop_back();
        }
    }
}

int main(){
    cin>>n;
    rec(0);
    cout<<cnt<<endl;
}
