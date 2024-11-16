**想把本地的博客通过git上传到github的仓库中，如果没有代理的话，这个过程会很慢，所以今天学习了一下如何将git设置成全局代理模式。**
## 设置代理模式
我使用的是v2RayN代理，使用http方式设置(如果使用https的话，需要依赖openssl)
简单讲就一行命令：
```
git config --global http.proxy https://URL:port
```
也可以为单独的某个网站设置：
```
git config --global http.网站地址.proxy http://URL:port
```
*这里的URL就是代理的ip地址，port就是端口号。*
获取方式：
1、直接打开v2RayN查看
2、打开设置->网络和Internet->代理，选择编辑手动代理，就能查看到当前代理服务器的ip和端口号了。

## 验证是否成功
```
curl -x http://proxyserver:port -I https://www.example.com
```

## 取消代理设置
同样也只是一行命令：
```
git config --global --unset http.proxy
```

## 命令行将本地的md文件用git push到github仓库
为了方便起见，找到本地md的存放地址，直接在那里打开cmd；

```
git init                           //初始化仓库
git add .(文件name)                //添加文件到本地 
git commit -m “first commit”      //添加文件描述信息
git remote add origin  远程仓库地址 //链接远程仓库 

// 把本地仓库的变化连接到远程仓库master分支
git pull origin master --allow-unrelated-histories)//括号的内容可加可不加
//或者上一步不用这句也行，可以用这个,强制push：
git push --force origin master
git push -u origin master        //把本地仓库的文件推送到远程仓库master分支
```
