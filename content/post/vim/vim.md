---
title: vim常用快捷键
description:  
image: 
date: 2022-03-31
categories:
    - program
tags:
    - vim

---

## 光标的移动

### 1.1 基本移动

- `h` 左 `l`右 `j`下 `k`上 `space`右移 `backspace`左移
- `+`或者 `Enter` 移动到下一行的第一个非空白字符
- `w`下移一个单词，光标停留在下一个单词开头
- `W`下移一个单词，忽略标点，标点不被算为单词。例：a.b c，会直接跳到c
- `e`下移一个单词，光标停留在下一个单词末尾
- `E`下移一个单词，忽略标点，表点不被算为单词。如果词尾有标点的话，光标停留在词尾的标点
- `b`上移一个单词，光标停留在上一个单词开头
- `B` 上移一个单词，光标停留在上一个单词开头，忽略标点，标点不被算为单词
- `ge`上移一个单词，光标停留在上一个单词末尾
- `gE` 上移一个单词，光标停留在上一个单词末尾，忽略标点，单词挨着的标点不被视为单词
- `(` 前移一句
- `)` 后移一句
- `{` 前移一段
- `}` 后移一段
- `fc` 把光标移到同一行的下一个c字符处
- `Fc` 把光标移到同一行的上一个c字符处
- `tc` 把光标移到同一行的下一个c字符前
- `Tc` 把光标移到同一行的上一个c字符后
- `;` 配合f & t使用，重复一次
- `,` 配合f & t使用，反向重复一次

### 1.2翻屏

- `ctrl+f`下翻一屏
- `ctrl+b`上翻一屏
- `ctrl+d`下翻半屏
- `ctrl+u`上翻半屏
- `zz` 将当前行移动到屏幕中央
- `zt` 将当前行移动到屏幕顶端
- `zb` 将当前行移动到屏幕底端

### 1.3标记

使用标记在两点之间快速移动

- `m{a-z}` 标记光标位置，局部标记，退出文件后失效
- `m{A-Z}` 标记光标位置，全局标记，退出后重新进入仍然有效
- `` `{a-z}`` 移动到标记的位置
- `` `` `` 返回到上次编辑的地方。`''`也可以，前者精确到列，后者精确到行。跳转到更老的位置用`ctrl+o`跳转到更新的位置用`ctrl+i`
- `` `"` 移动到上次离开的地方
- `` `.` 移动到最后改动的地方
- `:marks` 显示所有的标记
- `:delmarks a b` 删除标记a和b
- `:delmarks a c-f` 删除标记a和b
- `:delmarks!` 删除当前缓冲区所有的标记

## 插入文本

### 2.1 基本插入

- `i` 在光标前插入。(8i=<esc>可以插入8个等号，也可以批量插入其他的字符)
- `I` 在当前行的第一个非空字符前插入
- `a` 在光标后插入
- `A` 在当前行的最后插入
- `o` 在下面新建一行插入
- `O` 在上面新建一行插入

### 2.2 改写插入

- `ciw` 删除光标当前单词并进入插入模式(change in word)
- `ci"` 删除光标引号内的内容并进入插入模式,"也可替换为括号大括号等，比较常用
- `ct,` 从当前光标删除到逗号之前的所有字符并进入插入模式，逗号可换为任何字符

## 剪切复制和寄存器

### 3.1复制粘贴剪切

- `[n]x` 剪切光标右边n个字符，相当与`d[n]l`
- `[n]X` 剪切光标左边n个字符，相当于`d[n]h`
- `y` 选中后复制文本
- `yy` 复制整行
- `yaw yas` 复制一个单词和一个句子，也可用`yiw``yis` 
- `d` 删除选中后的内容
- `dd` 删除整行
- `D` 从当前光标删除到行尾
- `daw das` 删除一个单词和一个句子，也可用`diw``dis` 

### 寄存器

- `a-z` 都可用作寄存器名字,`"ayy`把当前行的内容放在a寄存器
- `A-Z` 用大写字母作寄存器可以在寄存器追加内容而不会替换
- `reg` 显示寄存器的所有内容
- `"ap` 粘贴寄存器a里面的内容到当前光标所在处

## 查找替换

### 4.1 查找

- `/s` 在后面的文本中查找字符串s
- `?something` 在前面的文本中查找字符串s
- `n` 向后查找下一个
- `N` 向前查找下一个

### 4.2 替换

- `:s/old/new` 用new替换当前行的第一个old
- `:s/old/new/g` 用new替换当前行的所有old
- `:%s/old/new/g` 用new替换文件中所有的old
- `:%s/old/new/gc` 用new替换文件中所有的old,但每次替换用户都要确认

### 4.3窗口编辑

- `ctrl+w v` 垂直分隔当前窗口
- `ctrl+w s` 水平分隔当前窗口
- `ctrl+w w` 在分隔后的窗口之间切换
- `ctrl+w h/j/k/l` 在分隔后的窗口上下左右移动

## 快速编辑

### 5.1 normal模式替换

- `r` 替换光标处的字符，支持汉字

- `R` 从当前光标处逐字替换后面的所有字符
  
  ### 5.2 大小写切换

- `~` 反转光标处的大小写

- `u/U` 可视模式下，选中的文本变成大小写

- `gu/U+范围` 把范围内的文本变成大小写
  
  ### 5.3 撤销重做

- `u` 撤销上一步，前面可加n撤销上n步

- `U` 取消当前行的所有改动

- `ctrl+r` 重做最后的改动
  
  ### 5.4 宏

- `.` 重复上一个编辑动作

- `qa` 开始录制宏a

- `q` 停止录制

- `@a` 播放宏a