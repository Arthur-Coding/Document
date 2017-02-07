#JSON格式字符串、字典或数组互转
##其实就是字符串转字典或数组，字典或数组转字符串
###字符串转字典或数组
1.先将字符串转为NSData类型数据
NSData *jsonData = [jsonString dataUsingEncoding:NSUTF8StringEncoding];
2.将NSData类型数据转为JSON数据
id JSON = [NSJSONSerialization JSONObjectWithData:jsonData options:NSJSONReadingAllowFragments error:nil];
###字典或数组转字符串
1.先将字典或数组转为NSData数据
NSData *jsonData = [NSJSONSerialization dataWithJSONObject:dic options:NSJSONReadingAllowFragments error:nil];
2.将NSData类型数据转为字符串
NSString *str = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];