# 第一课 简介
## Anaconda
- 设置镜像
>conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
conda config --set show_channel_urls yes

- 更新
>conda update anaconda-navigator

- 重新初始化
> anaconda-navigator --reset
> conda update anaconda-client   or
> conda update -f anaconda-client
>
- 重启
>anaconda-navigator

