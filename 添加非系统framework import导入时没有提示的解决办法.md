#添加非系统framework import导入时没有提示的解决办法
##1.选择target（就是左边你的工程target）—— BuildSettings —— search Paths 下的 User Header Search Paths（如图所示：）
<img src="http://image83.360doc.com/DownloadImg/2015/03/0215/50676036_1.jpg" width="600" height="300">
##2.双击后面的空白区域：（如图所示：）
<img src="http://image83.360doc.com/DownloadImg/2015/03/0215/50676036_2.jpg" width="600" height="200">
##3.点击“+”号添加一项：并且输入：“$(SRCROOT)/framework文件路径/XXXXX.framework/Headers”（没有引号,Headers为存放.h头文件的文件夹）,在确定后会自动变成:工程路径/framework文件路径/XXXXX.framework/Headers，或者输入“$(SRCROOT)”,后面的选择“recursive”,Xcode同样会递归查找