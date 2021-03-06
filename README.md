# prevent duplicate

## 介绍
在豆瓣图书页面使用图书标题在calibre中查找书目，如有匹配则在标题处增加calibre跳转连接。

![prevent duplicate example](/img/prevent_duplicate.png?raw=true)

## 安装

**前提** 需要有一个运行中的[calibre server](https://manual.calibre-ebook.com/server.html)

打开[prevent_duplicate.user.js](prevent_duplicate.user.js)，点击 `Raw`按钮进行安装。

安装后修改`calibre_server`地址为自己的calibre服务器地址。


# add2transmission

## 介绍

add2transmission 是一个 [Tampermonkey](https://www.tampermonkey.net/) 脚本。
作用是在magnet url超链接边上增加一个 [transmission](https://transmissionbt.com/) 按钮，一键将magnet url添加到 transmission 中。

### magnet url边上的 transmission按钮

![add2transmission button](/img/add2transmission_button.png?raw=true)

### 添加magnet url成功

![add2transmission success](/img/add2transmission_success.png?raw=true)


## 安装

打开 [add2transmission.user.js](add2transmission.user.js) 点击 `Raw` 按钮


## 配置

修改`transmission_rpc_url`成你自己的 transmission rpc 地址

## 支持的站点

该脚本遍历HTML DOM查找所有magnet url 的 a 标签。(`magnet:?` 开头的链接)。理论上可以支持所有站点。可以自行增加站点。

目前配置的站点如下：
```
// @match        https://btdig.com/*
// @match        https://1337x.to/*
// @match        https://www.torrentdownloads.me/*
// @match        https://thepiratebay.org/*
```


## 已知的问题

1 在yyets的资源分享站（例如：https://yyets.dmesg.app/resource.html?id=11010）无法在正常使用。
猜测应该是页面加载完之后，使用js重新渲染增加的magnet链接。
解决方案是将userscript run-at 修改为 context-menu，页面加载完出现magnet链接(按钮)后执行脚本。即可成功。

