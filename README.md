# web3
web3
int lca(int x, int y) {
     if (depth[x] > depth[y]) swap(x, y);
     for(int i = B; i >= 0; i --){
         //令x和y高度一致
         if (depth[prede[y][i]] >= depth[x]) y = prede[y][i];
     }
     //注意此时有可能出现x == y，那么LCA(x,y) == x，下方的for
     //就不起作用了。
     for(int i = B; i >= 0; i --){
        //如果prede[x][i]和prede[y][i]不相同，说明这两者的高度
        //都大于所求的LCA(x,y)，也就是在LCA(x,y)的下方，此时令
        //x和y一同往根部以2^(i)的步数爬升
        if (prede[x][i] != prede[y][i]) x = prede[x][i], y = prede[y][i];
     }
     if (x == y) return x;   //此时LCA（x,y) = x
     return prede[x][0];     //此时x和y有共同的父结点
}
