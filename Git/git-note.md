###Git Sparse Checkout
    
    在Git 1.7.0以后加入了**Sparse Checkout**模式，这使得_Check Out_指定文件或者文件夹成为可能。
    实现为：
    ```
    $ mkdir _project_folder
    $ cd _project_folder
    $ git init
    $ git remote add -f origin <url>
    $ git config core.sparsecheckout true    //启用Sparse Checkout
    $ echo '_dir' >> .git/info/sparse-checkout    //添加文件夹
    $ echo '_doc' >> .git/info/sparse-checkout    //添加文件
    $ git pull origin master
    ```
