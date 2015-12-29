
#chisel的安装常用命令解释和安装常见问题解决



#### 安装 [chisel](https://github.com/facebook/chisel) 

##### 常见问题

> bash: brew: command not found(没有安装brew)


```
解决方法:
在Terminal中输入<br>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"安装brew
```


> NO developer tools installed.(没有安装Xcode Command Line Tools)

```
解决方法:
xcode-select --install  
```

> error: active developer path ("/Applications/Xcode 2.app/Contents/Developer") does not exist, use `xcode-select --switch path/to/Xcode.app` to specify the Xcode that you wish to use for command line developer tools (or see `man xcode-select`)(可能安装了多个Xcode)

```
解决方法:
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

> Error: Could not create /usr/local/Cellar(权限问题,无法创建Cellar文件夹,可以功过磁盘工具修复权限解决也可以手动解决)

```
解决方法:
1.cd /usr/local
2.sudo mkdir Cellar
3.cd ..
4.chmod 777 /Cellar
```



###pviews
>递归打印出所有view,并显示层级关系

sample: pviews 0x7fb8e2fa2e00

```
 Options:
  --up/-u ; Print only the hierarchy directly above the view, up to its window.
  --depth/-d <depth>; Type: int; Print only to a given depth. 0 indicates
  infinite depth.

Syntax: pviews [--up] [--depth=depth] <aView> 
```

###pvc

?递归打印出当前所在viewController的层级,可以用于查看viewController结构和定位当前所在的viewController

sample: pvc


```
 Syntax: pvc <aViewController>
```

### visualize
>在预览app中预览UIImageView,CGImageRef,UIView,或CALayer,可用于查看图片详情,大小分辨,文件大小,定位view具体内容等

sample:visualize 0x787b3f00

```
Arguments:
  <target>; Type: (id); The object to visualize.

Syntax: visualize <target>
```
### mask/unmask & border/unborder
>这两组命令用于标识view或layer的位置,mask用来在view上覆盖一个半透明的矩形,border用于给view添加边框,unxxxx是用于解除命令

sample: 

* mask 0x787b3f00
* border 0x787b3f00


##### mask
```
Options:
  --color/-c <color>; Type: string; A color name such as 'red', 'green',
  'magenta', etc.
  --alpha/-a <alpha>; Type: CGFloat; Desired alpha of mask.

Syntax: mask [--color=color] [--alpha=alpha] <viewOrLayer>
```
##### border

```
Options:
  --color/-c <color>; Type: string; A color name such as 'red', 'green',
  'magenta', etc.
  --width/-w <width>; Type: CGFloat; Desired width of border.

Syntax: border [--color=color] [--width=width] <viewOrLayer>
```
#### bmessage
>常规添加断点的方法是在xcode中点击添加,但这种添加方式仅限于已经实现的方法添加断点,如果没有实现我们就没法添加断点<br>
使用bmessage可以给没有实现的方法添加断点如:[viewController viewWillAppear:]

sample: bmessage [EmployeeViewController viewWillAppear:]

```
Arguments:
  <expression>; Type: string; Expression to set a breakpoint on, e.g. "-[MyView
  setFrame:]", "+[MyView awesomeClassMethod]" or "-[0xabcd1234 setFrame:]"

Syntax: bmessage <expression>
```

#### caflush
>调试时刷新UI布局,不用重新build代码

```
Syntax: caflush
```

#### fv & fvc
>通过类名搜送当前内存中的view和viewController实例(支持正则搜索)

sample:

- fv view
- fvc view

##### fv
```
Arguments:
  <classNameRegex>; Type: string; The view-class regex to search the view
  hierarchy for.

Syntax: fv <classNameRegex>
```

##### fvc
```
Options:
  --name/-n <classNameRegex>; Type: string; The view-controller-class regex to
  search the view controller hierarchy for.
  --view/-v <view>; Type: UIView; This function will print the View Controller
  that owns this view.

Syntax: fvc [--name=classNameRegex] [--view=view]
```

#### taplog
>点击屏幕,程序暂停,打印点击的view信息

sample:taplog

```
Syntax: taplog
```
  
#### presponder
>打印presponder响应连

sample:presponder self

```
Arguments:
  <startResponder>; Type: UIResponder *; The responder to use to start walking
  the chain.

Syntax: presponder <startResponder>
```

#### pclass
>打印class的父类层级

sample:pclass self
```
Arguments:
  <object>; Type: id; The instance to examine.

Syntax: pclass <object>
```

#### wivar
>设置对象的Watchpoint,类似KVO,监控是哪改变了对象属性

sample: wivar self testStr

```
Arguments:
  <object>; Type: id; Object expression to be evaluated.
  <ivarName>; Type: ; Name of the instance variable to watch.

Syntax: wivar <object> <ivarName>
```

### And more?


Follow [@Bindx](https://github.com/bindx) on github for the latest news.