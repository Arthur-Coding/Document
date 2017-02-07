#Prefix预编译文件添加
   在Xcode6之前，创建一个新工程xcode会在Supporting files文件夹下面自动创建一个“工程名-Prefix.pch”文件，也是一个头文件，pch头文件的内容能被项目中的其他所有源文件共享和访问。是一个预编译文件。
##pch的作用：
1.存放一些全局的宏(整个项目中都用得上的宏)
2.用来包含一些全部的头文件(整个项目中都用得上的头文件)
3.能自动打开或者关闭日志输出功能
  
##如何在Xcode中添加pch文件：
Command+N，打开新建文件窗口：iOS->other->PCH file，创建一个pch文件

2，在工程的TARGETS里边Building Setting中搜索Prefix Header，然后把Precompile Prefix Header右边的NO改为Yes：

3.然后在Precompile Prefix Header下边的Prefix Header右边双击，添加刚刚创建的pch文件的工程路径，添加格式：“$(SRCROOT)/项目名称/pch文件名” ，$(SRCROOT)的意思就是工程根目录的意思，例如$(SRCROOT)/test/Prefix.pch名。如果还不太清楚的话可以右键pch文件，然后show in finder：
  以上方式动态添加，也建议这样做，当然，也可以在双击后，直接将pch文件拖进来，会自动生成一个路径，这种方法在自己电脑上不会有问题，但一旦将工程复制到其他电脑上，工程路径发生改变就会发生变化，又需要重写设置一下pch路径。

添加完成后，他会自动帮你变成你工程所在的路径：
可以了，编译一下程序，如果有错误检查一下添加的路径是否正确。

4，将Precompile Prefix Header为YES，预编译后的pch文件会被缓存起来，可以提高编译速度
