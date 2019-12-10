# 打印设计
## 打印设计工作区介绍
![打印设计工作区介绍](https://raw.githubusercontent.com/gscloudplugin/gscloudplugin/master/images/%E6%89%93%E5%8D%B0%E8%AE%BE%E8%AE%A1%E5%B7%A5%E4%BD%9C%E5%8C%BA%E4%BB%8B%E7%BB%8D.jpg)

## 使用说明
在js脚本中调用
```
GSCloudPlugin.PrintDraw({Title:"DRAW0001", "Width":210, "Height":297, "PrintMethod":"Design"})
```

## 文件保存机制
为了防止停电或电脑宕机等情况，加入了文件保存机制，会将打印设计的数据自动保存到安装目录下的PrintDesignData目录，文件按请求数据的Title自动命名，如果为传递这个参数，则生成一个GUID的文件名


