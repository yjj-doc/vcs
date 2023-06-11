# git

: 2005년 Linus Torvalds 개발  
: 분산 시스템, 파일 스냅샷 기반  



- [git basic](./git-basic.md)
  - git concept
- git command 
- git hosting
  - GitHub
  - GitLab
  - BitBucket
  - SourceForge
  - RocketGit


**install**
```bash 
# linux 
sudo yum install git 
sudo install git

# windows 
choco install git.install


git --version
```


**git version**     
https://mirrors.edge.kernel.org/pub/software/scm/git/



**config** 
```bash 
# global 
git config --global user.name 이름
git config --global user.email 이메일

## linux
vi /etc/gitconfig 

## windows 
more 'C:\Program Files\Git\etc\gitconfig'


# local 
git config --local user.name 이름
git config --local user.email 이메일


git config --list
```



[top](#)