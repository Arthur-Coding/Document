#使用cocoaPods import导入时没有提示的解决办法
##1.选择target（就是左边你的工程target）—— BuildSettings —— search Paths 下的 User Header Search Paths（如图所示：）
<img src="http://image83.360doc.com/DownloadImg/2015/03/0215/50676036_1.jpg" width="600" height="300">
##2.双击后面的空白区域：（如图所示：）
<img src="http://image83.360doc.com/DownloadImg/2015/03/0215/50676036_2.jpg" width="600" height="200">
##3.出现下面的图，并且点击“+”号添加一项：并且输入：“$(PODS_ROOT)”（没有引号），选择：recursive（会在相应的目录递归搜索文件）：
<img src="http://image83.360doc.com/DownloadImg/2015/03/0215/50676036_3.jpg" width="600" height="300">