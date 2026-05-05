## 一、模块简介

Layout Inspect 是一款逆向必备的工具：它具备以下功能：应用进程、捕获布局（兼容
SystemUI、各种窗口类型、临时上帝模式）、活动记录、类加载器（枚举内存中的类加载器）、搜索类名（支持动态加载类）、Inject
So（注入 so 文件）、Dump So（与 Frida 枚举 so 类似）、Dump Dex（支持愛加蜜、愛加蜜企业、dpt-shell等方案脱壳）、Dump
Maps（/proc/self/maps，支持快速 dump）、Dump Xml（支持Epic、DexProtect等）、Dump
Asset（支持Epic、纸片、木华、NP管理器等）、移除安全限制（去除截屏限制）、调试浏览器等等。

<img src="https://icdn.binmt.cc/2605/69f991816414d.jpg" alt="">

## 二、如何激活并使用模块？

1.首先先下载并安装 Layout Inspect，然后到 LSPosed 勾选您的目标软件（不需要勾选“系统框架”）

2.本模块已经兼容API 89、100、101，Layout Inspect支持动态请求作用域！

[温馨提示：](#)自 1.1.5 起，首次打开 Layout Inspect 需要选择 Xposed Service（选择不当会导致部分功能异常，如：动态作用域）。

## 三、模块环境？

1.Root设备：毫无疑问，毋庸置疑，强烈推荐 LSPosed

2.非Root设备（亲测可用）：

- 1.LSPatch（系列）：两种模式(Shizuku 和 内置模块)均支持，选其中一种模式都可以
- 2.FPA
- 3.团团分身
- 4.虚拟机：光速虚拟机、虚拟大师等（不推荐 VMOS）

## 四、功能说明

### 1.应用进程

该功能有“当前进程”和“更多进程”两个窗口，展示所有正在运行的进程的信息，具备以下几大功能：

- 1.预览对象
- 2.杀死进程

<img src="https://icdn.binmt.cc/2605/69f9782262b02.jpg" alt="">

### 2.捕获布局（兼容SystemUI、兼容各种窗口类型、临时上帝模式）

该功能用于快速定位 View 控件，支持捕获任何窗口（PopupWindow、Dialog、Menu、悬浮窗等），具备以下几大功能：

<img src="https://icdn.binmt.cc/2605/69f97830e8ff6.jpg" alt="">

控件信息：

- View（常规）：
-
    - class（类名）
-
    - width（宽）
-
    - height（高）
-
    - id
-
    - tag（标签）
-
    - contentDescription（内容描述）
-
    - foreground（前景）
-
    - background（背景）
-
    - listenInfo（事件信息）：快速定位单击事件，长按事件等事件
-
    - padding（内边距）
-
    - margin（外边距）
- TextView（文本）：
-
    - text（文本内容）
-
    - textSize（文本大小）
-
    - textColor（文本颜色）
-
    - hintColor（提示颜色）
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
    - url（链接）
-
    - cookie
-
    - UserAgent
-
    - javascriptInterfaces（Java 与 WebView 的沟通桥）
- ImageView（图像）：
-
    - src（图像）

---

控件功能：

- 移除控件（removeView）
- 隐藏控件 ⇆ 显示控件（setVisibility）
- 控件转图片 (新)：兼容性拉满，比下面的那个强
- 控件转图片
- [调用堆栈：](#)用于快速定位 View 的构造堆栈，以达到快速反编译修改

---

[上帝模式（临时）：](#)

- View（常规），支持修改：
-
    - width（宽）
-
    - height（高）
-
    - foreground（前景）
-
    - background（背景）
-
    - padding（内边距）
-
    - margin（外边距）
- TextView（文本），支持修改：
-
    - text（文本内容）
-
    - textSize（文本大小）
-
    - textColor（文本颜色）
-
    - hintColor（提示颜色）
- WebView（浏览器），支持：
-
    - url（链接）
-
    - Inject javascript（向浏览器注入 javascript 代码）
-
    - UserAgent（用户代理）
- ImageView（图像）：支持：
-
    - src（图像）

---

### 3.活动记录

该功能枚举APP正在运行中的 activity

相应信息：

- 1.class
- 2.application
- 3.intent

<img src="https://icdn.binmt.cc/2605/69f98ded91f43.jpg" alt="">

### 4.活动管理

该功能枚举APP所有申明的 activity，具备以下功能：

- 1.预览类：直接预览该 activity 类名的结构（字段，构造，方法，父类，内部类等）
- 2.启动活动：直接跳转该 activity

<img src="https://icdn.binmt.cc/2605/69f98eb29e010.jpg" alt="">

### 5.类加载器（枚举内存中的加载器）

该功能枚举内存中的类加载器，具备以下功能：

- 1.预览对象：用于查看类结构（字段，构造，方法，父类，内部类等）
- 2.Dump Dex：具体请参考下面的 Dump Dex

<img src="https://icdn.binmt.cc/2605/69f995724af64.jpg" alt="">

### 6.搜索类名（支持动态加载类）

该功能对比于“反射大师”来说，考虑的更周到。

- 原因：通过枚举类加载器从而进行搜索类名，即使是动态加载的 dex，也插翅难逃
- 功能：“预览类”，用于查看类结构（字段，构造，方法，父类，内部类等）

<img src="https://icdn.binmt.cc/2605/69f9784743d69.jpg" alt="">

### 7.Inject So（注入 so 文件）

该功能用于向 APP 注入 so 文件，懂的都懂。

<img src="https://icdn.binmt.cc/2605/69f97848b41d2.jpg" alt="">

### 8.Dump So（与 Frida 枚举 so 类似）

该功能用于枚举内存中的所有 so 文件，其枚举数量与 Frida 一致，具备以下功能：

- 1.查看基本信息（pathname、base、size）
- 2.Dump So

<img src="https://icdn.binmt.cc/2605/69f9784ce6c9a.jpg" alt="">

### 9.Dump Dex（支持愛加蜜、愛加蜜企业、dpt-shell等方案脱壳）

该功能相对于其他模块来说算是比较全面的，理由如下：

- 您可以对 任何一个类加载器 进行脱壳
- 您可以选择 mCookie、mInternalCookie、Dexcaches 其中一种方案 获取列表，对抗抹字段形式
- 您可以前往 高级设置 -> DexFileSize 进行脱壳，用于对抗抹掉 DexHeader 的保护形式
- 您可以前往 高级设置 -> 主动加载类 进行脱壳，用于对抗愛加蜜、愛加蜜企业、dpt-shell
- 您可以前往 高级设置 -> 主动加载类 -> 自定义 进行脱壳，支持R8基础规则 或 正则表达式 进行主动加载类并脱壳（常见于修复 nop
  问题）

<img src="https://icdn.binmt.cc/2605/69f97850cd320.jpg" alt="">

### 10.Dump Xml（支持Epic、DexProtect等）

该功能可以解密常见的 Axml 加密，如Epic、DexProtect等。原理是通过解析 xmlBlock 的内存进行还原（虽然罕见，但不能没有）。

<img src="https://icdn.binmt.cc/2605/69f98f63dc3ba.jpg" alt="">

### 11.Dump Maps

该功能通过解析/proc/self/maps，具备以下功能：

- 1.详细数据：用于查看 map 的详细信息（base、size、start、end、offset、permissions、device、inode、pathname）
- 2.Dump This Memory：用于 Dump 单段内存，即当前 map 的内存（从 start 至 end 的内存区域）
- 3.Dump All Memory：用于 Dump 连续内存，基于当前 map，如果其他 map 的 start/end 与 当前 map 的 start/end 相连，将会被一起
  Dump

Ps：该功能也可以用于 Dump So，若您想 Dump So，请使用“Dump All Memory”功能（注意：极端情况下，可能出现 Dump 的比实际更多）。

<img src="https://icdn.binmt.cc/2605/69f97862dff7e.jpg" alt="">

### 12.Dump Assets（支持Epic、纸片、木华、NP管理器等）

该功能可以解密常见的 Assets 资源加密，如NP管理器、Epic、木华、纸片等资源加密。

<img src="https://icdn.binmt.cc/2605/69f9786d3bb7e.jpg" alt="">

### 13.移除安全限制（截屏限制）

该功能与其他模块的原理不同，其他模块的原理是 Hook 拦截，而本模块通过主动调用使其强制关闭限制（若您不使用该功能，即宿主不受影响），并详细地列举出“凶手”。

### 14.调试浏览器

该功能主要用于逆向 Web 型软件，与谷歌浏览器配合使用，动态调试快速定位 Html 元素，网络请求，算法还原等，减少逆向时间的成本。

<img src="https://icdn.binmt.cc/2605/69f97866dc551.jpg" alt="">

## 五、常见问题

### 模块的悬浮窗被挡住？

虽然开发者对悬浮窗的优先度进行了优化，但也不可能百分百保证悬浮窗一直不被遮挡，遇到这种情况，请[1秒内连续双击音量键+/-即可召唤悬浮窗](#)。
