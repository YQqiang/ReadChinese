# 正则表达式(适用于iOS):
* 查找所有中文中文字符串(`.h`, `.m`): 

```
NSRegularExpression *regular = [NSRegularExpression regularExpressionWithPattern:@"@\"+[^\"]*[\\u4E00-\\u9FA5]+[^\"\\n]*?\"" options:NSRegularExpressionCaseInsensitive error:nil];
```

* 查找所有中文中文字符串(`.Swift`):

```
[NSRegularExpression regularExpressionWithPattern:@"\"+[^\"]*[\\u4E00-\\u9FA5]+[^\"\\n]*?\"" options:NSRegularExpressionCaseInsensitive error:nil];
``` 

* 只匹配国际化的key字段(`.h`, `.m`):

```
NSRegularExpression *regular = [NSRegularExpression regularExpressionWithPattern:@"(?<=NSLocalizedString\\(@\").*?(?=\",)" options:NSRegularExpressionCaseInsensitive error:nil];
```

* 只匹配国际化的key字段(`.Swift`):

```
[NSRegularExpression regularExpressionWithPattern:@"(?<=NSLocalizedString\\(\").*?(?=\",)" options:NSRegularExpressionCaseInsensitive error:nil];
``` 

* 匹配`strings`文件中的key

```
@"\"+[^\"]+[^\"\\n]*?\" ="
```

* 匹配`strings`文件中的value

```
@"\"+[^\"]+[^\"\\n]*?\";"
```

# ReadChinese
读取某个目录中的所有中文，并且将这些中文按照多语言(.string)格式写入文件中，可以直接拿来实现国际化


###操作示例图如下
![操作示例图](https://github.com/Ashen-Zhao/ReadChinese/blob/master/ReadChinese/screenshot.png)  


###使用说明
&emsp;本项目中，只是识别了.m和.h文件中的中文字符串，如果想要识别.swift等，请在`ViewController.m` 中的 `- (void)readFiles:(NSString *)str ` 方法中的`extension` 数组中，加入相应的后缀名即可。  
&emsp;该导出的文件，默认以`chinese.txt` 的形式存在于你选择的导出路径，想要修改导出文件名，请进入`- (IBAction)OpenFile:(NSButton *)sender` 方法中进行修改即可。

