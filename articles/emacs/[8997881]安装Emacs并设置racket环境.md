最近在阅读[sicp](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%A8%8B%E5%BA%8F%E7%9A%84%E6%9E%84%E9%80%A0%E5%92%8C%E8%A7%A3%E9%87%8A)这本书，书中的代码是使用`scheme`实现的。之前阅读的时候是使用`Dr.Racket`来完成写练习的，可我觉得与其这样，不如一步到位，使用`emacs+lisp`解释器来的比较快。

## 安装emacs

直接点击官方教程[点我查看](http://ergoemacs.org/emacs/which_emacs.html)，上面讲解的十分清楚，基本上不同系统的安装方式大同小异，下载后点击运行，还是很简单的吧。

## 安装lisp解释器

直接点击官方教程[点我查看](http://ergoemacs.org/emacs/which_emacs.html)，上面讲解的十分清楚，基本上不同系统的安装方式大同小异，下载后点击运行，还是很简单的吧。

## 安装lisp解释器

lisp有无数种实现的版本，这里我使用的是`Racket`，因为我之前电脑上就有`Dr.Racket`所以不用下载，如果你没有的话，可以点击[Racket下载地址](https://download.racket-lang.org/)，选择合适系统的版本进行下载，当然你也可以选择其他lisp方言的实现版本，例如[Petite Chez Scheme下载地址](http://scheme.com/download)。下载完解压即可。

下载完毕后，你可以得到这样的一些程序

![Racket基本程序](https://images2018.cnblogs.com/blog/1132218/201805/1132218-20180506123221932-1773720532.png)

接着设置将上图解释器所在的文件夹路径设置到系统路径中(windows=环境变量,mac/linux=`$path`),接着在终端敲击`racket --version` 来检查是否设置成功。如果出现以下信息，你就成功了。

![检查Racket是否成功设置](https://images2018.cnblogs.com/blog/1132218/201805/1132218-20180506123313043-1408892483.png)

## 安装一些必要而有效的插件
我们需要安装简单的几个插件来帮助我们高效的编写和运行代码。

### 设置插件源

和linux安装软件类似，这里我们设置`MELPA`的安装源，这样我们就可以一键安装代码了，十分方便。
鉴于国外访问速度很慢，我们这里使用国内的[镜像源](https://github.com/emacs-china/elpa)，这里要感谢一直维护自由软件的人，否则这些工具的设置与配置哪里会有这么容易和便捷:)

`emacs`中所有的配置都在`~/.emacs`这个文件中，对于windows，就是在C盘的个人目录文件夹下。我们可以通过编辑这个文件来对emacs进行一些自定义的配置。打开.emacs文件，在文件的末尾加上以下配置，设置我们的插件安装源。

```scheme
 ;; melpa 安装源
(require 'package)
(add-to-list 'package-archives
             '("melpa" . "http://elpa.emacs-china.org/melpa/")
             t)
(package-initialize)
```

这样就可以方便的安装插件了。

### 安装Racket-mode

`Racket-mode`很好用，执行代码，高亮，提示，反正我觉得该有的都OK，下面就进行安装。
使用以下命令`M-x package-install <ret> racket-mode`,M代表`alt`组合键的意思，`ret`代表回车，所以该命令实际上就是
- `alt+x`打开命令模式 
- 输入`package-install` (可以用空格键/tab来提示)，回车
- 再输入要安装的插件名`racket-mode`,回车确认，等待安装完毕。

![插件安装](https://images2018.cnblogs.com/blog/1132218/201805/1132218-20180506123335258-2137710956.png)


怎么样，很简单吧。

安装完毕后，在配置文件`.emacs`配置文件中增加以下代码的配置

```scheme
;;racket配置,设置解释器,自动补全,代码执行等
(require 'racket-mode)
(setq racket-racket-program "racket")
(setq racket-raco-program "raco")
(add-hook 'racket-mode-hook
          (lambda ()
            (define-key racket-mode-map (kbd "C-x C-j") 'racket-run)))
(setq tab-always-indent 'complete) 
```

### 安装ParEdit

`ParEdit`是一款让你半结构化编辑lisp的插件，例如括号的自动补全，s-表达式的转移，提取等等，还是很方便的。
同样使用`M-x package-install <ret> paredit-mode` 进行安装即可。

具体的使用方法不是本篇文章的重点，可以参考以下几篇文章
- [Emacs Paredit插件](https://www.jianshu.com/p/9f09896ebc08)
- [scheme编程环境的设置](https://www.jianshu.com/p/8893ff7f80a4)
- [官方卡片指南](http://pub.gajendra.net/src/paredit-refcard.pdf)


## Hello World

全部设置完毕后，我们新建一个文件(`ctrl+x 回车 i 回车 输入文件名`),输入以下代码

```scheme
#! /usr/bin/env racket

#lang racket

(displayln "Hello World!")
```

接着使用`F5` 执行 S-表达式，成功的打印的出Hello World 

![Hello World](https://images2018.cnblogs.com/blog/1132218/201805/1132218-20180506123352042-50500396.png)


至此，安装`Emacs`并设置`racket`环境就完毕啦

## 参考资料

- [Emacs Quick Start](http://ergoemacs.org/emacs/which_emacs.html)
- [Emacs Paredit插件](https://www.jianshu.com/p/9f09896ebc08)
- [scheme编程环境的设置](https://www.jianshu.com/p/8893ff7f80a4)
- [Paredit 官方卡片指南](http://pub.gajendra.net/src/paredit-refcard.pdf)
- [Emacs简单教程系列](http://www.cnblogs.com/robertzml/archive/2010/03/31/1701374.html)
- [从零开始——Emacs 安装配置使用教程](https://www.jianshu.com/p/b4cf683c25f3)