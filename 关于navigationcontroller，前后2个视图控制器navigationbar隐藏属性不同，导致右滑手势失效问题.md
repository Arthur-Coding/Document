#关于navigationController，前后2个视图控制器navigationBar隐藏属性不同，导致右滑手势失效问题
###1.问题描述：如A是navigationController的rootViewController，在这个页面navigationBar是显示的（隐藏属性为NO），它push出B视图控制器，B页面navigationBar是不显示的（隐藏属性为YES），有一定几率会出现，B要右滑pop自己，返回到A时，手势会失效，即使 self.navigationController.interactivePopGestureRecognizer.enabled = YES也不起作用
###2.问题分析：其实是右滑手势被阻断导致，手势仍然存在，需要重写其代理方法，使手势不被阻断
###3.解决步骤：
	####1.在B页面写下此行代码：self.navigationController.interactivePopGestureRecognizer.delegate = self;//主要是防止navigationBar隐藏后,右滑手势失效问题
	####2.让B页面遵守UIGestureRecognizerDelegate协议
	####3.重写GestureRecognizerDelegate方法：
	- (BOOL)gestureRecognizerShouldBegin:(UIGestureRecognizer *)gestureRecognizer{
    if (self.navigationController.viewControllers.count <= 1) {
        return NO;//防止B页面不存在，只有一个页面，此时也用不到右滑手势
    }
    return YES;
}