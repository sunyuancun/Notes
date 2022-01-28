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

#### 插件化的优势

* 宿主和插件分开编译
* 是可以并发开发的。宿主和插件说白了就是apk，开发是互不影响的（只需要宿主给插件一个上下文）。
* <mark style="color:green;">动态更新插件，不需要安装，下载之后就接就可以打开</mark>
* <mark style="color:green;">按需下载模块</mark>
* 可以解决方法树的爆棚问题65535













