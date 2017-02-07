#iOS系统设置调用及指定选项设置方法

##1.调用系统设置
### NSURL *url = [NSURL URLWithString:UIApplicationOpenSettingsURLString];
###[[UIApplication sharedApplication] openURL:url];

##2.调用其他指定设置
###方法:[[UIApplicationsharedApplication] openURL:[NSURL URLWithString:@"代码字符串"]];
#####一些代码:
prefs:root=General//通用
prefs:root=General&path=About  //关于
prefs:root=General&path=ACCESSIBILITY//重力感应 
prefs:root=AIRPLANE_MODE//飞行模式
prefs:root=General&path=AUTOLOCK//自动锁定
prefs:root=General&path=USAGE/CELLULAR_USAGE//用量
prefs:root=Brightness//亮度调节
prefs:root=General&path=Bluetooth//蓝牙
prefs:root=General&path=DATE_AND_TIME//时间和日期
prefs:root=FACETIME//视频通话
prefs:root=General&path=Keyboard//键盘
prefs:root=CASTLE//存储空间
prefs:root=CASTLE&path=STORAGE_AND_BACKUP//存储与备份
prefs:root=General&path=INTERNATIONAL//
prefs:root=LOCATION_SERVICES//
prefs:root=ACCOUNT_SETTINGS//
prefs:root=MUSIC//
prefs:root=MUSIC&path=EQ//
prefs:root=MUSIC&path=VolumeLimit//
prefs:root=General&path=Network//
prefs:root=NIKE_PLUS_IPOD//
prefs:root=NOTES//
prefs:root=NOTIFICATIONS_ID//
prefs:root=Phone//
prefs:root=Photos//
prefs:root=General&path=ManagedConfigurationList//
prefs:root=General&path=Reset//
prefs:root=Sounds&path=Ringtone//
prefs:root=Safari//
prefs:root=General&path=Assistant//辅助功能
prefs:root=Sounds//
prefs:root=General&path=SOFTWARE_UPDATE_LINK//
prefs:root=STORE//
prefs:root=TWITTER//
prefs:root=General&path=USAGE//
prefs:root=VIDEO//
prefs:root=General&path=Network/VPN//
prefs:root=Wallpaper//
prefs:root=WIFI//
prefs:root=INTERNET_TETHERING//