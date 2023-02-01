### C - Path Graph?

[Problem Link:](https://atcoder.jp/contests/abc287/tasks/abc287_c)

Code:   
    
    #include <bits/stdc++.h>
    using namespace std;

    #define FastIO ios_base::sync_with_stdio(0), cin.tie(0)
    #define TxtIO  freopen("input.txt", "r", stdin); freopen("output.txt", "w", stdout);
    #define f0(i, n) for (int i = 0; i < n; i++)
    #define f1(i, n) for (int i = 1; i <= n; i++)
    #define f2(i, n) for (int i = 1; i < n; i++)
    #define endl "\n"
    #define pb push_back
    #define mp make_pair
    #define vi vector<int>
    #define pi pair<int, int>
    #define all(x) x.begin(), x.end()
    #define ff first
    #define ss second
    #define int long long
    #define INF 1000000000
    #define mod 1000000007
    int Ceil(int a, int b){return (a + b - 1) / b;}
    //_________________template______________

    template <typename T> // printByVectorName
    ostream& operator<<(ostream &os, const vector<T> &v) {for (auto e : v){os << e << " ";}return os;}


    vi vis;
    vector<vector<int>>adj;
    bool flag = false;

    void dfs(int node, int p){
        vis[node] = 1;
        for(int x:adj[node]){
            if(!vis[x]){
                vis[x] = 1;
                dfs(x, node);
            }else{
                if(p != x) flag = true;
            }
        }
    }

    void sol()
    {
        int node,edge;cin>>node>>edge;
        vis.clear();
        adj.clear();
        vis.resize(node+1,0);
        adj.resize(node+1);

        int u,v;
        f0(i,edge){
            cin>>u>>v;
            adj[u].pb(v);
            adj[v].pb(u);

        }
        if (edge != node - 1) {
            cout << "No\n";
            return;
        }
        for (int i = 1; i <= node; ++i) {
            if (adj[i].size() > 2) {
                cout << "No\n";
                return;
            }
        }
        int cnt = 0;
        f1(i,node){
            if(!vis[i]){
                dfs(i, -1);
                cnt++;
            }
        }   
        if(!flag && cnt == 1)cout<<"Yes"<<endl;
        else cout <<"No"<<endl;
    }


    int32_t main()
    {
        FastIO;
        //TxtIO;
        int tt;
        tt = 1;
        // cin >> tt;
        while (tt--)
        {
            sol();
        }
    }
