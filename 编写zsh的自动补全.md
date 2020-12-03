# 编写zsh的自动补全
## 初始化
1. 在~/.zshrc文件中，增加`autoload -U compinit && compinit`。以便启用zsh的自动补全功能
2. 使用自动加载函数的约定，以下划线开头。将补全脚本放在$fpath的目录中。当compinit运行时，它会搜索所有这些文件通过访问fpath并读取他们的第一行。该行应包含以下描述的标签之一。第一行不以这些标签之一开头的文件不被视为完成系统的一部分，并且不会得到特别处理。
```bash
#compdef name
```
3. 编写脚本（以定制工具部分为例）
```bash
#compdef iso-tailor
function _iso-tailor {
    local line
    _arguments -C\
        '--help[iso-tailor information]' \
        '--version[iso-tailor version]' \
        '1: :(load save repo app  driver service autostart ui autoinstall autologin bootloader syslog \
	   hibernation usb serial netif vga shortcut firewall pam apt-show apt-policy developmode kernel)' \
        '*::arg:->args'

    case $line[1] in
          load | save | repo)
             _arguments '*:files:_files'
           ;;
          app)
            _iso-tailor_app
          ;;
          shortcut)
           _arguments '--list[列出所有快捷键]: : ' '--disable[禁用某快捷键]: : ' '--enable[启用某快捷键]: : '
          ;;
    esac
}
function _iso-tailor_app {
    _arguments \
      '--add[add package online or local]: :_files' \
      '--remove[remove package]: : '\
      '--certificate[upload certificate]: :_files'
}
```
其中_arguments为核心部分。使用形式'-name[description]:message:action '  
重点是actions部分，如 _files 代表所有文件 [actions详细信息](https://github.com/zsh-users/zsh-completions/blob/master/zsh-completions-howto.org#actions)



## 参考资料

[zsh自动补全官方文档](http://zsh.sourceforge.net/Doc/Release/Completion-System.html#Completion-Functions)
[zsh man手册](https://linux.die.net/man/1/zshcompsys)