---
title: sublime3-markdown插件
date: 2018-01-24
---

&nbsp;想着日后要常用markdown了，所以在sublime中添加了markdown的插件，果然，舒服多了，嘿嘿嘿

### MarkdownEditing

查了几个推荐，这个都在第一位，于是就选择了

系统：win10

版本：sublime3
+ 首先在sublime中安装[package control](https://packagecontrol.io/installation)
    - 菜单栏View->Show Console打开sublime的控制台
    - 在其中输入以下代码就能下载安装啦
    ```
    import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by) 
    ```
    - 重启sublime
+ 安装MarkdownEditing
    - 在sublime中快捷键"ctrl+shift+p"进入sublime命令面板
    - 在搜索框中输入"install package"，选择"package control: install package"
    - 耐性等待一会，获得远程插件仓库的索引目录
    - 在搜索框中输入"MarkdownEditing"，选择"MarkdownEditing"
    - 耐心等待安装好，重启就可以啦
+ 修改样式
    - 在菜单栏Preference->Package Setting->Markdown Editing中能修改其样式等属性

>安装参考 [介绍Sublime3下两款Markdown插件](https://www.jianshu.com/p/335b7d1be39e)