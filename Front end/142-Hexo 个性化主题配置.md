---
title: Hexo 个性化主题配置
tags: [博客]
categories: 前端
---
>接上文：[基于 Hexo + GitHub 的个人博客搭建](https://wonz5130.github.io/2018/07/30/2.Hexo+GitHub/)，这篇是写配置 next 个性化主题的。
>
>只记录自己使用的一些配置，不定期更新。
>
>有两个 _config.yml 文件，根目录的是站点配置文件，`\themes\next\`中的是主题配置文件，注意区分。

<!--more-->

# 一、基本信息配置

打开 **站点配置文件** ，找到 Site 模块。

![](142-Hexo 个性化主题配置\0.png)

# 二、主题配置

### 1.菜单设置

我们刚开始默认的菜单只有首页和归档两个，不能够满足我们的要求，所以需要添加菜单，打开 **主题配置文件** 找到`Menu Settings` 

![](142-Hexo 个性化主题配置\10.png)

看看你需要哪个菜单就把哪个取消注释打开就行了； 关于后面的格式，以`archives: /archives/ || archive`为例： `||` 之前的`/archives/`表示标题 “归档”，关于标题的格式可以去`themes/next/languages/zh-Hans.yml`中参考或修改 `||`之后的`archive`表示图标，可以去 [Font Awesome](https://link.jianshu.com/?t=http%3A%2F%2Ffontawesome.io%2Ficons%2F) 中查看或修改，Next 主题所有的图标都来自 Font Awesome。 

### 2.Next 主题样式设置

Next 主题还有 4 种风格供我们选择，打开 **主题配置文件** 找到`Scheme Settings` ，选择其一即可。

![](142-Hexo 个性化主题配置\11.png)

### 3.侧栏设置

![](142-Hexo 个性化主题配置\12.png)

### 4.侧边栏推荐阅读

打开 **主题配置文件** 修改成这样就行了 (links 里面写你想要的链接): 

![](142-Hexo 个性化主题配置\9.png)

### 5.头像设置

![](142-Hexo 个性化主题配置\13.png)

这是头像的路径，只需把你的头像命名为`XXX.jpg`（随便命名）放入`themes\next\source\images`中，将`avatar`的路径名改成你的头像名就 OK 啦！ 

### 6.侧边栏社交小图标设置

打开 **主题配置文件** ，搜索`social_icons:`, 在[图标库](http://fontawesome.io/icons/)找自己喜欢的小图标，并将名字复制在如下位置，保存即可。![](142-Hexo 个性化主题配置\1.png) 

### 7.添加分类模块

* 新建一个分类页面

  ```bash
  $ hexo new page categories
  ```

* 你会发现你的`source`文件夹下有了`categories\index.md`，打开`index.md`文件将 title 设置为`title: 分类` 

* 打开 **主题配置文件** 找到`menu`，将 categories 取消注释 

* 把文章归入分类只需在文章的顶部标题下方添加`categories`字段，即可自动创建分类名并加入对应的分类中

### 8.添加标签模块

* 新建一个标签页面 

```bash
$ hexo new page tags
```

* 你会发现你的`source`文件夹下有了`tags\index.md`，打开`index.md`文件将 title 设置为`title: 标签` 
* 打开 **主题配置文件** 找到`menu`，将 tags 取消注释
* 把文章添加标签只需在文章的顶部标题下方添加`tags`字段，即可自动创建标签名并归入对应的标签中 

### 9.添加搜索功能

* 安装 [hexo-generator-searchdb](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2Fflashlab%2Fhexo-generator-search) 插件

```bash
$ npm install hexo-generator-searchdb --save
```

* 打开 **站点配置文件** 找到`Extensions`在下面添加 

![](142-Hexo 个性化主题配置\14.png)

* 打开 **主题配置文件** 找到`Local search`，将`enable`设置为`true` 

![](142-Hexo 个性化主题配置\15.png)

### 10.添加阅读全文按钮

因为在你的博客主页会有多篇文章，如果你想让你的文章只显示一部分，多余的可以点击阅读全文来查看，那么你需要在你的文章中添加

```markdown
<!--more-->
```

其后面的部分就不会显示了，只能点击阅读全文才能看。

例如

![](142-Hexo 个性化主题配置\16.png)

### 11.去掉文章目录标题的自动编号

我们自己写文章的时候一般都会自己带上标题编号，但是默认的主题会给我们带上编号，很是别扭，如何去掉呢？ 打开**主题配置文件**，找到

![](142-Hexo 个性化主题配置\17.png)

### 12.代码高亮主题

打开**主题配置文件**，找到 `highlight_theme`，可以设置五种形式。

![](142-Hexo 个性化主题配置\18.png)

# 三、其它个性化设置

### 1.添加动态背景

如果 next 主题在 5.1.1 以上的话，直接在主题配置文件中找到 canvas_nest: false，把它改为 canvas_nest: true 就行了（注意分号后面要加一个空格）。

可以参考[这篇博客](http://shenzekun.cn/hexo%E5%A6%82%E4%BD%95%E6%B7%BB%E5%8A%A0%E5%8A%A8%E6%80%81%E8%83%8C%E6%99%AF.html)。

### 2.实现点击出现爱心效果

```javascript
!function(e,t,a){function n(){c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),o(),r()}function r(){for(var e=0;e<d.length;e++)d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");requestAnimationFrame(r)}function o(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),i(e)}}function i(e){var a=t.createElement("div");a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)}function c(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function s(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var d=[];e.requestAnimationFrame=function(){return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)}}(),n()}(window,document);
```

将上面的代码 copy 一下，新建`love.js`文件并且将代码复制进去，然后保存。将`love.js`文件放到路径`\themes\next\source\js\src`里面，然后打开`\themes\next\layout\_layout.swig`文件, 在末尾（在前面引用会出现找不到的 bug）添加以下代码： 

```html
<!-- 页面点击小红心 -->
<script type="text/javascript" src="/js/src/love.js"></script>
```

### 3.修改文章内链接文本样式

修改文件 `\themes\next\source\css\_common\components\post\post.styl `，在末尾添加如下 css 样式，： 

```css
// 文章内链接文本样式
.post-body p a{
  color: #0593d3;
  border-bottom: none;
  border-bottom: 1px solid #0593d3;
  &:hover {
    color: #fc6423;
    border-bottom: none;
    border-bottom: 1px solid #fc6423;
  }
}
```

其中选择` .post-body` 是为了不影响标题，选择 `p` 是为了不影响首页 “阅读全文” 的显示样式, 颜色可以自己定义。 

### 4.修改文章底部的那个带 # 号的标签

修改模板`\themes\next\layout\_macro\post.swig`，搜索 `rel="tag">#`，将 # 换成` <i class="fa fa-tag"></i>` 

### 5.主页文章添加阴影效果

打开`\themes\next\source\css\_custom\custom.styl`, 向里面加入： 

```css
// 主页文章添加阴影效果
 .post {
   margin-top: 60px;
   margin-bottom: 60px;
   padding: 25px;
   -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
   -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
  }
```

### 6.在网站底部加上访问量

打开`\themes\next\layout\_partials\footer.swig`文件, 在 copyright 前加上红线这句话：

![](142-Hexo 个性化主题配置\2.png) 

代码如下：

```html
<script async src="https://dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js"></script>
```

然后再合适的位置添加显示统计的代码，如图： 

![](142-Hexo 个性化主题配置\3.png)

代码如下：

```css
<div class="powered-by">
<i class="fa fa-user-md"></i><span id="busuanzi_container_site_uv">
  本站访客数:<span id="busuanzi_value_site_uv"></span>
</span>
</div>
```

在这里有两中不同计算方式的统计代码：

* **pv** 的方式，单个用户连续点击 n 篇文章，记录 n 次访问量

```css
<span id="busuanzi_container_site_pv">
    本站总访问量<span id="busuanzi_value_site_pv"></span>次
</span>
```

* **uv** 的方式，单个用户连续点击 n 篇文章，只记录 1 次访客 

```css
<span id="busuanzi_container_site_uv">
  本站总访问量<span id="busuanzi_value_site_uv"></span>次
</span>
```

这里，选择 uv 的方式。

### 7.网站底部字数统计

切换到根目录下，然后运行如下代码 

```bash
$ npm install hexo-wordcount --save
```

然后在`\themes\next\layout\_partials\footer.swig`文件尾部加上： 

```css
<div class="theme-info">
  <div class="powered-by"></div>
  <span class="post-count">博客全站共{{ totalcount(site) }}字</span>
</div>
```

### 8.隐藏网页底部 powered By Hexo / 强力驱动

打开`\themes\next\layout\_partials\footer.swig`, 使用”<!-- -->” 隐藏之间的代码即可，或者直接删除。位置如图 ：

![](142-Hexo 个性化主题配置\6.png)

### 9.修改网页底部的桃心

还是打开`themes/next/layout/_partials/footer.swig`，找到：

![](142-Hexo 个性化主题配置\7.png)

然后还是在[图标库](http://fontawesome.io/icons/)中找到你自己喜欢的图标，然后修改画红线的部分就可以了。 上图是我已经改成爱心之后的版本。

### 10.添加 README.md 文件

每个项目下一般都有一个 `README.md` 文件，但是使用 hexo 部署到仓库后，项目下是没有 `README.md` 文件的。

在 Hexo 目录下的 `source` 根目录下添加一个 `README.md` 文件，修改站点配置文件 _`config.yml `，将 `skip_render` 参数的值设置为

```yaml
skip_render: README.md
```

保存退出即可。再次使用 `hexo d` 命令部署博客的时候就不会在渲染 README.md 这个文件了。 

### 11.设置网站的图标 Favicon

网上看到的设置方法是说把 favicon.ico 放到站点目录的 source 目录下就可以了，但是我试了好多遍，并不行， 后来发现一种方法不错。

把你的图片（png 或 jpg 格式，不是 favicon.ico）放在`themes\next\source\images`里，然后打开 **主题配置文件** 找到`favicon`，将`small、medium、apple_touch_icon`三个字段的值都设置成`\images\图片名.jpg`就可以了，其他字段都注释掉。 

下面这是我自己的图标样式：

![](142-Hexo 个性化主题配置\4.png)

**注意：**要想透明，可以用 PS 做个背景透明化，找到一份[教程](https://wenda.so.com/q/1462901765722849)，亲测可用，这样图标就能透明化了。

### 12.实现统计功能

在根目录下安装 `hexo-wordcount`, 运行： 

```bash
$ npm install hexo-wordcount --save
```

然后在主题的配置文件中，配置如下： 

```yaml
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
```

![](142-Hexo 个性化主题配置\5.png)

### 13.博文置顶

修改 `hero-generator-index` 插件，把文件：`node_modules\hexo-generator-index\lib\generator.js` 内的代码替换为： 

```javascript
'use strict';
var pagination = require('hexo-pagination');
module.exports = function(locals){
  var config = this.config;
  var posts = locals.posts;
    posts.data = posts.data.sort(function(a, b) {
        if(a.top && b.top) { // 两篇文章top都有定义
            if(a.top == b.top) return b.date - a.date; // 若top值一样则按照文章日期降序排
            else return b.top - a.top; // 否则按照top值降序排
        }
        else if(a.top && !b.top) { // 以下是只有一篇文章top有定义，那么将有top的排在前面（这里用异或操作居然不行233）
            return -1;
        }
        else if(!a.top && b.top) {
            return 1;
        }
        else return b.date - a.date; // 都没定义按照文章日期降序排
    });
  var paginationDir = config.pagination_dir || 'page';
  return pagination('', posts, {
    perPage: config.index_generator.per_page,
    layout: ['index', 'archive'],
    format: paginationDir + '/%d/',
    data: {
      __index: true
    }
  });
};
```

在文章中添加 `top` 值，数值越大文章越靠前，如：

![](142-Hexo 个性化主题配置\8.png)

# 致谢

[hexo 的 next 主题个性化配置教程](https://segmentfault.com/a/1190000009544924)

[Hexo 的 Next 主题详细配置](https://www.jianshu.com/p/3a05351a37dc)