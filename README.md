## 一、如何激活并使用模块？

1.首先需要下载并安装“Layout Inspect”，然后去“Lsposed”勾选你需要Hook的软件。

2.本模块也兼容了Api 100，支持前往“Layout Inspect”动态请求作用域！

[温馨提示：]()本模块不需要勾选“系统”作用域（即使勾选也没问题）

## 二、功能说明

### 1.当前活动

该功能用于查看当前的Activty活动，同时可以查看相应的Application、Intent

### 2.捕获布局（招牌功能）

该功能用于快速定位View控件，支持捕获任何窗口（PopupWindow、Dialog、Menu、悬浮窗等），具备以下几大功能：

控件信息：

- View（常规）：
-
    - 类名（class）
-
    - 宽（width）
-
    - 高（height）
-
    - id
-
    - tag（标签）
-
    - contentDescription（内容描述）
-
    - 前景（foreground）
-
    - 背景（background）
-
    - 事件信息（listenInfo）：可快速定位单击事件，长按事件等事件
-
    - 内边距（padding）
-
    - 外边距（margin）
- TextView（文本）：
-
    - 文本内容（text）
-
    - 文字大小（textSize）
-
    - 文本颜色（textColor）
-
    - 提示颜色（hintColor）
- AdapterView（大部分列表）：
-
    - adapter（适配器）
- VideoView（视频）：
-
    - uri（链接）
-
    - headers（请求头）
- WebView（浏览器）：
-
    - 链接（url）
-
    - cookie
-
    - UserAgent
-
    - javascriptInterfaces（Java与WebView的沟通桥）
- ImageView（图像）：
-
    - 支持替换图像（src）

---

控件功能：

- 控件转图片（支持任意控件）
- [调用堆栈：]()可用于定位View是如何被创建的，以达到快速反编译修改

---

[上帝模式（临时）：]()

- View（常规），支持修改：
-
    - 宽（width）
-
    - 高（height）
-
    - 前景（foreground）
-
    - 背景（background）
-
    - 内边距（padding）
-
    - 外边距（margin）
-
    - 移除控件
-
    - 隐藏控件 ⇆ 显示控件
- TextView（文本），支持修改：
-
    - 文本内容（text）
-
    - 文字大小（textSize）
-
    - 文本颜色（textColor）
-
    - 提示颜色（hintColor）
- WebView（浏览器），支持：
-
    - 修改链接（url）
-
    - Inject Javascript（注入js）
-
    - 修改用户代理（UserAgent）
- ImageView（图像）：支持：
-
    - 替换图像（src）

---

### 3.应用进程

该功能有“当前进程”和“更多进程”两个窗口，主要展示宿主的所有运行中的进程信息

### 4.活动管理

该功能列举宿主的所有Activity活动，可以跳转到选定的Activity活动

### 5.类加载器

该功能枚举所有类加载器，可以对它进行“预览对象”和“脱壳”等

### 6.搜索类名

该功能对比于“反射大师”来说，考虑的更周到，原因：通过枚举类加载器进行类名搜索，即使是外部加载的Dex，也可以被搜索到。

### 7.Inject So（注入So）

该功能可以向宿主注入So文件，解锁更牛逼的功能。

### 8.Dump Dex（脱壳）

该功能相对于其他模块来说算是比较全面的，理由如下：

- 您可以对 任何一个类加载器 进行脱壳
- 您可以对 某一个加载器的某个mCookie 进行脱壳
- 您可以通过 R8基础规则或者正则表达式 进行主动加载类并脱壳（解决 nop 问题）

### 9.Dump Xml（独家功能）

该功能可以解密常见的Axml加密，如Epic等。原理是通过解析xmlBlock的底层内存进行还原，虽然罕见，但不能没有。

### 10.Dump Assets（解密）

该功能可以解密常见的Assets资源加密，如NP管理器、Epic、木华、纸片等资源加密。

### 11.移除截屏限制

该功能与其他模块的原理不同，其他模块的原理是Hook拦截，而本模块通过主动调用进行强制关闭。意思是，你不使用该功能，即宿主不受影响。

### 12.调试浏览器

该功能主要逆向Web型软件，与谷歌浏览器共同使用，动态调试快速定位html元素，网络请求，算法还原等，减少逆向时间的成本。

## 三、常见问题

### 模块的悬浮窗被挡住？

虽然开发者对悬浮窗的优先度进行了优化，但也不可能百分白保证悬浮窗一直不被遮挡，遇到这种情况，[1秒内连续双击音量键即可召唤悬浮窗]()。