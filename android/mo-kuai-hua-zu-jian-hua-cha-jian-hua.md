# 模块化&组件化&插件化

### 模块化

#### 什么是模块化



### **组件化**

#### 什么是组件化

组件化是将一个<mark style="color:orange;">app分成多个模块，每个模块都是一个组件(module)</mark>，开发的过程中我们<mark style="color:orange;">可以让这些组件相互依赖或者单独调试部分组件</mark>，但是<mark style="color:green;">最终发布的时候将这些组件合并成一个统一的apk</mark>，这就是组件化开发。

#### 组件化优点和方案

#### 组件如何独立调试

#### 组件间通信

#### ARouter原理

#### Aplication动态加载



#### 插件化

#### 插件化的定义

插件化开发就是将整个app拆分成很多模块，<mark style="color:orange;">每个模块都是一个apk</mark>(组件化的每个模块是一个lib),最<mark style="color:orange;">终打包的时候将宿主apk和插件apk分开打包，插件apk通过动态下发到宿主apk</mark>，这就是插件化。

插件可以提供一种<mark style="color:orange;">动态扩展能力</mark>，使得应用程序在运行时加载原本不属于该应用的功能，并且做到<mark style="color:orange;">动态更新和替换</mark>。

#### 宿主

所谓宿主，就是需要<mark style="color:red;">能提供运行环境，给资源调用提供上下文环境，一般也就是我们主 APK</mark> ，要运行的应用，它作为应用的主工程所在，<mark style="color:green;">实现了一套插件的加载和管理的框架</mark>，<mark style="color:red;">插件都是依托于宿主的APK而存在的</mark>。

#### 插件

插件可以想象成每个<mark style="color:red;">独立的功能模块封装为一个小的 APK</mark> ，可以<mark style="color:red;">通过在线配置和更新实现插件 APK 在宿主 APK 中的上线和下线，以及动态更新等功能。</mark>

#### 插件化的优势

* 宿主和插件分开编译
* 是可以并发开发的。宿主和插件说白了就是apk，开发是互不影响的（只需要宿主给插件一个上下文）。
* <mark style="color:green;">动态更新插件，不需要安装，下载之后就接就可以打开</mark>
* <mark style="color:green;">按需下载模块，实现灵活的功能配置</mark>
* 提供一种<mark style="color:green;">快速修复线上 BUG 和更新</mark>的能力
* 可以解决方法树的爆棚问题65535

#### 插件化流程（动态加载的过程）

1. 把可执行文件（ <mark style="color:red;">.so/dex/jar/apk</mark> 等）拷贝到应用 APP 内部
2. 加载可执行文件，更换静态资源
3. 调用具体的方法执行业务逻辑

#### 插件化原理

基于 ClassLoader动态加载 dex/jar/apk 文件，在 Android 中的 ClassLoader 机制主要用来<mark style="color:red;">加载 dex 文件。</mark>

<mark style="color:red;">DexClassLoader</mark>：<mark style="color:red;">支持加载外部的 APK、Jar 或者 dex 文件</mark>，正好符合文件化的需求，<mark style="color:red;">所有的插件化方案都是使用 DexClassloader 来加载插件 APK 中的 .class文件的。</mark>

PathClassLoader：只能加载已经安装到 Android 系统中的 APK 文件。因此不符合插件化的需求，不作考虑

#### 插件化框架

实现插件化框架，需要解决的问题主要有

1. 资源和代码的加载
2. Android 生命周期的管理和组件的注册
3. 宿主 APK 和插件 APK 资源引用的冲突解决

#### 框架一： **DL 动态加载框架**

{% embed url="https://blog.csdn.net/singwhatiwanna/article/details/39937639" %}

#### [https://github.com/singwhatiwanna/dynamic-load-apk](mo-kuai-hua-zu-jian-hua-cha-jian-hua.md#kuang-jia-yi-dl-dong-tai-jia-zai-kuang-jia)

####

基于<mark style="color:blue;">代理的方式</mark>实现插件框架，对 App 的表层做了处理，<mark style="color:red;">通过在 Manifest 中注册代理组件，当启动插件组件时，首先启动一个代理组件，然后通过这个代理组件来构建，启动插件组件</mark>。 需要按照一定的规则来开发插件 APK，<mark style="color:blue;">插件中的组件需要实现经过改造后的 Activity、FragmentActivity、Service 等的子类。</mark>&#x20;

<mark style="color:red;">优点</mark>：

插件需要<mark style="color:blue;">遵循一定的规则，因此安全方面可控制</mark>。 方案简单，适用于自身少量代码的插件化改造。&#x20;

<mark style="color:red;">缺点</mark>：

<mark style="color:red;">不支持通过 This 调用组件的方法，需要通过 that 去调用</mark>。 由于 APK 中<mark style="color:red;">的 Activity 没有注册，不支持隐式调用 APK 内部的 Activity</mark>。 插件编写和改造过程中，需要考虑兼容性问题比较多，联调起来会比较费时费力。





****

<mark style="color:red;"></mark>

<mark style="color:red;"></mark>

<mark style="color:red;"></mark>













