# 使用Hugo+LoveIt主题+Github Pages搭建博客（1）本地运行


## 安装Hugo

可参考[Hugo官方的Quick Start](https://gohugo.io/getting-started/quick-start/)

### 安装二进制（Mac）

```bash
# 使用brew安装hugo
brew install hugo

# 创建新项目（网站）
hugo new site my_website

# 生成用于发布的静态文件（不包含草稿）
hugo

# 生成用于发布的静态文件（包括草稿）
hugo -D

# 本地运行网站
hugo server
```



### 直接使用Docker

```bash
# 创建新项目（网站）
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo \
  new site my_website

# 生成用于发布的静态文件（不包含草稿）
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo

# 生成用于发布的静态文件（包括草稿）
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo -D
  
# 本地运行网站
docker run --rm -it \
  -v $(pwd):/src \
  -p 1313:1313 \
  klakegg/hugo \
  server
  
```

{{< admonition type=notice title="可以在镜像后面增加版本号，指定使用的hugo版本" open=true >}}

```bash
# 比如
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo:0.82.0
```

{{< /admonition >}}

## 安装LoveIt主题

```bash
# 位于你的博客项目根目录
git clone https://github.com/dillonzq/LoveIt.git themes/LoveIt
```

代码克隆成功后在`./themes`文件夹下应出现`LoveIt`文件夹。

{{< admonition type=quote open=true >}}

详细可参考[LoveIt官方文档](https://hugoloveit.com/zh-cn/theme-documentation-basics/)

{{< /admonition >}}

## 项目文件树结构

```bash
.
├── archetypes # markdown文章的模版
├── config.toml # 配置文件
├── content # 网站内容，主要保存文章
├── data # 生成网站可用的数据文件，可用在模版中
├── layouts # 生成网站时可用的模版
├── public # 通过hugo命令生成的静态文件，主要发布这个
├── resources # 通过hugo命令一起生成的资源文件，暂时不知道什么用
├── static # 静态文件，比如文章中的图片/视频文件、缩略图等
└── themes # 保存可用的hugo主题

```

通常，我们只会用到以下几个文件夹的东西

- `config.toml` ：保存hugo的配置，包括主题的配置等。详细设置见下方 #网站配置
- `content`：保存网站的各种内容，比如文章。
- `archetypes`： 保存文章的markdown模版，通常包括文章的前缀注释，是一些在创建新文章时会被用到。
- `static` ：保存文章中用到的静态文件，比如图片、网站缩略图等。
- `public` ：通过`hugo`命令生成的静态html文件、css、js等。在服务器上发布时主要发布这个文件夹。



## 配置网站设置

配置文件位置：`./config.toml`

{{< admonition type=quote open=true >}}

具体的配置条目参考[LoveIt官方文档](https://hugoloveit.com/zh-cn/theme-documentation-basics/#site-configuration)

{{< /admonition >}}

## 配置缩略图

1. 使用的网站：https://realfavicongenerator.net/ 获取缩略图的各种格式

   {{< image src="https://gitee.com/JellyZhang_55ee/blogpic/raw/master/img/image-20210420215752393.png" caption="下载到的全部内容">}}

2. 将整个压缩包的文件（包括图片之外的文件）放到`./static`下

## 开始写第一篇文章

### 文章前缀注释

###  本地调试

### Chrome禁用缓存
