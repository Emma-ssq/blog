# Vim

Vim 有多种模式。
normal: Esc
    - insert: i
    - command line: :
    - replace: R
    - visual: v
    - visual line: shift+v
    - visual block: ctrl+v

## 基本命令

1. 退出:quit
2. 写入：write
3. 帮助文档: help :write

### 光标

1. 光标左右移动：h,j,k,l
2. 行首0，行末$
3. 在buffer中上翻ctrl+u,下翻ctrl+d
4. G跳转到最底部，gg是顶部

### 查找

1. normal模式下输入/ ,输入enter， n寻找下一个

### 写入

1. normal模式下 o在光标下面新开一行，O在上面新开一行

### 删除

1. dd删除一行，dw表示删除一个单词

### 撤销与重做

1. u撤销
2. ctrl+r 重做

### 复制与粘贴

1. y表示复制，yy表示复制当前行, yw表示复制一个单词
2. p表示粘贴
3. 复制一段文字：先进入visual模式，按键v，光标会选中一段文字。
