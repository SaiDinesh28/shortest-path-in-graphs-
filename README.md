//# shortest-path-in-graphs-
//shortest path in undircted graph with unit weights
#include<bits/stdc++.h>
using namespace std;
int shortdist(int node1,int node2,vector<int>adj[],int n){
    vector<int>dist(n,INT_MAX);
    dist[node1]=0;
    queue<int>q;
    q.push(node1);
while(!q.empty()){
    int x=q.front();
    q.pop();
    int d=dist[x];
    for(auto it:adj[x]){
        q.push(it);
        dist[it]=min(dist[it],1+dist[x]);
        
    }
}
    return dist[node2];
}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<int>adj[n];
        for(int i=0;i<m;i++){
            int u,v;
            cin>>u>>v;
            adj[u].push_back(v);
          //  adj[v].push_back(u);
        }
        int a,b;
        cin>>a>>b;
       // vector<int>v=toposort(n,adj);
        //for(auto i:v) cout<<i<<" ";
        cout<<shortdist(a,b,adj,n)<<endl;
    }
}
