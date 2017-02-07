#关于block使用的6点注意事项

##1、在使用block前需要对block指针做判空处理。

不判空直接使用，一旦指针为空直接产生崩溃。

if (XXXX) {
    XXXX(参数);
 }

##2、block如果作为成员参数要copy一下将栈上的block拷贝到堆上
即作为属性时，最好写成@property (nonatomac,copy)XXXXXXX;

##3、在block使用之后要对block指针做赋空值处理，如果是MRC的编译环境下，要先release掉block对象。
block作为类对象的成员变量，使用block的人有可能用类对象参与block中的运算而产生循环引用。

将block赋值为空，是解掉循环引用的重要方法。（不能只在dealloc里面做赋空值操作，这样已经产生的循环引用不会被破坏掉）
    if (data != nil && _sucBlock != NULL) {
        _sucBlock(data);
    }
    //MRC下：要先将[_sucBlock release];（之前copy过）
    _sucBlock = nil; //Importent: 在使用之后将Block赋空值，解引用 !!!
}

还有一种改法，在block接口设计时，将可能需要的变量作为形参传到block中，从设计上解决循环引用的问题。

##4、使用时将self或成员变量加入block之前要先将self变为__weak

##5、在多线程环境下（block中的weakSelf有可能被析构的情况下），需要先将self转为strong指针，避免在运行到某个关键步骤时self对象被析构。
第四、第五条合起来有个名词叫weak–strong dance

以下代码来自AFNetworking，堪称使用weak–strong dance的经典。

__weak typeof(self) weakSelf = self;
AFNetworkReachabilityStatusBlock callback = ^(AFNetworkReachabilityStatus status) {
    __strong typeof(weakSelf) strongSelf = weakSelf;
    strongSelf.networkReachabilityStatus = status;
    if (strongSelf.networkReachabilityStatusBlock) {
        strongSelf.networkReachabilityStatusBlock(status);
    }
};

第一行：__weak __typeof(self)weakSelf = self;
如之前第四条所说，为防止callback内部对self强引用，weak一下。
其中用到了__typeof(self)，这里涉及几个知识点：
a. __typeof、__typeof__、typeof的区别
没有区别
b.对于老的LLVM编译器上面这句话会编译报错，所以在很早的ARC使用者中流行__typeof(&*self)这种写法

第三行：__strong typeof(weakSelf) strongSelf = weakSelf;

按照之前第五条的说法给转回strong了，这里typeof()里面写的是weakSelf，里面写self也没有问题，因为typeof是编译时确定变量类型，所以这里写self 不会被循环引用。

第四、五、六行，如果不转成strongSelf而使用weakSelf，后面几句话中，有可能在第四句执行之后self的对象可能被析构掉，然后后面的StausBlock没有执行，导致逻辑错误。

最后第五行，使用前对block判空。

##6、使用block块，给block定义后，block回调不起作用，往往是block属性所述的类的实例对象已不是原来的对象。