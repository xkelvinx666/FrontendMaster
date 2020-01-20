# 多项目公共代码管理
## 使用包管理 
包管理是其中一种解决思路，但包管理更适合存放业务无关，通用，不经常改动的代码。而且需要考虑代码public的问题
### 制作一个npm包 [健壮的npm包](https://juejin.im/post/5af7de01f265da0ba60fe37c) [简单npm包](https://juejin.im/post/5971aa866fb9a06bb5406c94)
## subtree
考虑到公共的业务代码会在不同项目中同时使用（手机端和pc端），对于开发过程更友好，更熟悉，所以使用subtree方案。
[subtree](https://tech.youzan.com/git-subtree/)
1. 将需要公共的代码放置于同一文件目录下
2. 新建远程项目用于存放subtree代码
3. 将目录作为subtree
    ```
    git subtree add --prefix=src/components http://github.com/xxx/xxxx.git master-2020-01-19
    ```
4. 推送代码，*建议每次推送新的分支*
    ```
    git subtree push --prefix=src/components http://github.com/xxx/xxxx.git master-2020-01-19
    ```
5. 删除原目录，从subtree仓库获取建立关系(第一次建subtree时)
    ```
    git rm src/components
    git subtree pull --prefix=src/components http://github.com/xxx/xxxx.git master-2020-01-19
    ```

*注意使用subtree可能会有特殊git异常，一定要按步骤进行操作*
