class Solution {
public:
    bool isSafe(int i,int j,vector<vector<int>>& grid,vector<vector<bool>>&visited,int x)
    {
       return (i>=0 && j>=0 && i<grid.size() && j<grid[0].size() && grid[i][j]==x && visited[i][j]==false);
    }
    void DFS(int i,int j,vector<vector<int>>& grid, vector<vector<bool>>&visited,int newColor,int x)
    {
        static int a[]={0,0,-1,1};
        static int b[]={-1,1,0,0};
        visited[i][j]=true;
        grid[i][j]=newColor;
        for(int k=0;k<4;++k)
        {  if(isSafe(i+a[k],j+b[k],grid,visited,x)==true)
              DFS(i+a[k],j+b[k],grid,visited,newColor,x);
        }
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor) {
         int m=image.size(),n=image[0].size();
         vector<vector<bool>>visited(m,vector<bool>(n,false));
        DFS(sr,sc,image,visited,newColor,image[sr][sc]);
        return image;
    }
};
