CocoaPods 安装 使用
1.开启 terminal
2.移除现有 Ruby 默认源
$ gem sources --remove https://rubygems.org/

3.使用新的源
$ gem sources -a https://ruby.taobao.org/

4.验证新源是否替换成功
$ gem sources -l

5.安装 CocoaPods
$ sudo gem install cocoapods

$ pod setup

备注：苹果系统升级 OS X EL Capitan 后安装改为:

$ sudo gem install -n /usr/local/bin cocoapods

$ pod setup

6.更新 gem
$ sudo gem update --system

7.新建工程，并在终端用 cd 指令到文件夹内
$ pod search 第三方

8.新建 Podfile 文件
$ touch Podfile

9.编辑 Podfile 文件，并写入要添加的第三方库
platform:ios, '8.0'

pod 'AFNetworking', '~> 2.3.1'<-------第三方

10.导入第三方库
$ pod install

11.退出终端



可能遇到的错误提示及解决方法：
Error 1：
Error fetching http://ruby.taobao.org/:

bad response Not Found 404 (http://ruby.taobao.org/specs.4.8.gz)

解决方案：把安装流程中 $ gem sources -a http://ruby.taobao.org/ 

改为：$ gem sources -a https://ruby.taobao.org/

Error 2：
ERROR:  While executing gem ... (Errno::EPERM)

Operation not permitted - /usr/bin/pod

解决方案：苹果系统升级 OS X EL Capitan 后会出现的插件错误，将安装流程 5.安装 CocoaPods 的 sudo gem install cocoapods

改为 sudo gem install -n /usr/local/bin cocoapods

Error 3：
[!] Unable to satisfy the following requirements:

- `AFNetworking (~> 2.3.1)` required by `Podfile`

Specs satisfying the `AFNetworking (~> 2.3.1)` dependency were found, but they required a higher minimum deployment target.

解决方案：Podfile 文件 中   platform:ios, ‘8.0’  后边的 8.0 是平台版本号 ，一定要加上

Error4:

―――――――――― MARKDOWN TEMPLATE ――――――――――

### Report

* What did you do?

* What did you expect to happen?

* What happened instead?

### Stack

```

CocoaPods : 0.29.0

Ruby : ruby 2.0.0p247 (2013-06-27 revision 41674) [universal.x86_64-darwin13]

RubyGems : 2.1.11

Host : Mac OS X 10.9.2 (13C64)

Xcode : 5.1 (5B130a)

Ruby lib dir : /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib

Repositories : master - https://github.com/CocoaPods/Specs.git @ bd6736d07b16c98ab7a1dae04697cae002f25a9b

```

### Podfile

```ruby

platform :ios,'8.0'

pod 'MBProgressHUD', '~> 0.8'

```

### Error

```

Psych::SyntaxError - (/Users/MAXJ/.cocoapods/repos/master/CocoaPods-version.yml): mapping values are not allowed in this context at line 3 column 4

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:205:in `parse'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:205:in `parse_stream'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:153:in `parse'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:129:in `load'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:299:in `block in load_file'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:299:in `open'

/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/psych.rb:299:in `load_file'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/sources_manager.rb:261:in `version_information'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/sources_manager.rb:222:in `repo_compatible?'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/sources_manager.rb:281:in `master_repo_functional?'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/command.rb:39:in `parse'

/Library/Ruby/Gems/2.0.0/gems/claide-0.4.0/lib/claide/command.rb:179:in `parse'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/command.rb:38:in `parse'

/Library/Ruby/Gems/2.0.0/gems/claide-0.4.0/lib/claide/command.rb:211:in `run'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/lib/cocoapods/command.rb:51:in `run'

/Library/Ruby/Gems/2.0.0/gems/cocoapods-0.29.0/bin/pod:24:in `'

/usr/bin/pod:23:in `load'

/usr/bin/pod:23:in `'

```

―――――――――― TEMPLATE END ――――――――――

[!] Oh no, an error occurred.

Search for existing github issues similar to yours:

https://github.com/CocoaPods/CocoaPods/search?q=%28%2FUsers%2FMAXJ%2F.cocoapods%2Frepos%2Fmaster%2FCocoaPods-version.yml%29%3A+mapping+values+are+not+allowed+in+this+context+at+line+3+column+4&type=Issues

If none exists, create a ticket, with the template displayed above, on:

https://github.com/CocoaPods/CocoaPods/issues/new

Don't forget to anonymize any private data!

解决方案：

$ sudo rm -rf ~/.cocoapods/repos/master

$ pod setup