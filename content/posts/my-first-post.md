+++
date = '2024-11-03T23:37:49+08:00'
title = 'My First Post'
categories = ["通用技术"]
tags = ["博客搭建", "Bilibili"]
+++
 
这是第一篇文章

行内数学公式：$a^2 + b^2 = c^2$。

块公式，

$$
a^2 + b^2 = c^2
$$

<div>
$$
\boldsymbol{x}_{i+1}+\boldsymbol{x}_{i+2}=\boldsymbol{x}_{i+3}
$$
</div>

```cpp
#include <iostream>
using namespace std;
template <class T, int s>
class A
{
private:
    T a[s];
    int n;
public:
    A()
    {
        for (int i = 0; i < n; i++)
            cin >> a[i];
    }
    A(T b[], int m)
    {
        n = m;
        for (int i = 0; i < m; i++)
            a[i] = b[i];
    }
    T max()
    {
        T m = a[0];
        for (int i = 0; i < n; i++)
            if (m < a[i])
                m = a[i];
        return m;
    }
    void firstinsert() // 插入函数
    {
        int x = 0;
        cout << "输入在数组首位插入的值:";
        cin >>x;
        for (int i = n - 1; i >= 0; i--)
            a[i + 1] = a[i];
        a[0] = x;
        n++;
    }
    void output()
    {
        for (int i = 0; i < n; i++)
            cout << a[i] << " ";
        cout << endl;
    }
    void deletefirst()
    {
        n = n - 1;
        for (int i = 0; i < n; i++)
            a[i] = a[i + 1];
    }
    void insert()
    {
        int q;
        long r;
        cout << "请输入插入位置：";
        cin >> q;
        cout << "请输入插入数字：";
        cin >> r;
        n = n + 1;
        for (int i = n; i > (q - 1); i--)
            a[i] = a[i - 1];
        a[q - 1] = r;
    }
};
int main()
{
    int pos;
    cout << "输入数组长度:";
    cin >> pos;
    long* a = new long[pos];
   
    for (int i = 0; i < pos; i++)
    {
        cin >> a[i];
    }
    A<long, 5> T1(a, pos);
    T1.output();
    cout << "该数组的最大值为:" <<T1.max() << endl;
    T1.insert();
    T1.output();
    T1.deletefirst();
    cout << "删除首位后该数组为:";
    T1.output();
    delete[] a;
    return 0;
}


```




```css
.post-content pre,
code {
    font-family: "JetBrains Mono", monospace;
    font-size: 1rem;
    line-height: 1.2;
}
```



```yaml
baseURL: "https://izumi987.github.io/" # 主站的 URL
title: Izumi987's Blog # 站点标题
copyright: "[©2024 Izumi987's Blog](https://izumi987.github.io/)" # 网站的版权声明，通常显示在页脚
theme: PaperMod # 主题
languageCode: zh-cn # 语言

enableInlineShortcodes: true # shortcode，类似于模板变量，可以在写 markdown 的时候便捷地插入，官方文档中有一个视频讲的很通俗
hasCJKLanguage: true # 是否有 CJK 的字符
enableRobotsTXT: true # 允许生成 robots.txt
buildDrafts: false # 构建时是否包括草稿
buildFuture: false # 构建未来发布的内容
buildExpired: false # 构建过期的内容
enableEmoji: true # 允许 emoji
pygmentsUseClasses: true
defaultContentLanguage: zh # 顶部首先展示的语言界面
defaultContentLanguageInSubdir: false # 是否要在地址栏加上默认的语言代码

languages:
  zh:
    languageName: "中文" # 展示的语言名
    weight: 1 # 权重
    taxonomies: # 分类系统
      category: categories
      tag: tags
    # https://gohugo.io/content-management/menus/#define-in-site-configuration
    menus:
      main:
        - name: 首页
          pageRef: /
          weight: 4 # 控制在页面上展示的前后顺序
        - name: 归档
          pageRef: archives/
          weight: 5
        - name: 分类
          pageRef: categories/
          weight: 10
        - name: 标签
          pageRef: tags/
          weight: 10
        - name: 搜索
          pageRef: search/
          weight: 20
        - name: 关于
          pageRef: about/
          weight: 21

# ~~~~~~~~~
# 主题的配置(基本上是)
# ~~~~~~~~~
paginate: 8 # 每页展示的文章数量

params:
  env: production # to enable google analytics, opengraph, twitter-cards and schema.
  description: "Theme PaperMod - https://github.com/adityatelange/hugo-PaperMod"
  author: Sonny Calcr
  defaultTheme: dark # 默认是暗色背景
  ShowShareButtons: false # 关闭分享的按钮
  ShowReadingTime: true # 展示预估的阅读时长
  displayFullLangName: true # 展示全名
  ShowPostNavLinks: true # 展示文章导航链接，就是下一页上一页的那个
  ShowBreadCrumbs: false # 是否展示标题上方的面包屑
  ShowCodeCopyButtons: true # 是否展示复制代码的按钮
  ShowRssButtonInSectionTermList: true # RSS 相关
  ShowAllPagesInArchive: true # 在归档页面展示所有的页面
  ShowPageNums: true # 展示页面的页数
  ShowToc: true # 展示文章详情页的目录
  comments: true # 评论
  images: ["https://i.postimg.cc/7hwBy7VS/calcr.png"] # 缺省的图片，比如，博客的封面
  DateFormat: "2006-01-02" # 这个时间是作者自己写的，只能这样写

# 首页的文章上方的一些信息
  homeInfoParams:
    # 首页的 profile 内容
    Title: "こんにちは👋"
    # 首页的 profile 内容
    Content: >
      Welcome to my Blog! 挂上一个梯子可能会让访问更加顺畅。
      <div>
      ● 
      <br>
      ● 
      <br>

  # 搜索
  fuseOpts:
      isCaseSensitive: false # 是否大小写敏感
      shouldSort: true # 是否排序
      location: 0
      distance: 1000
      threshold: 0.4
      minMatchCharLength: 0
      # limit: 10 # refer: https://www.fusejs.io/api/methods.html#search
      keys: ["title", "permalink", "summary", "content"]
      includeMatches: true
# https://github.com/adityatelange/hugo-PaperMod/wiki/Features#search-page

  # 评论的设置
  giscus:
    repo: "izumi987/izumi987.github.io"
    repoId: "R_kgDONJ1RRg"
    category: "Announcements"
    categoryId: "DIC_kwDONJ1RRs4Cj8TA"
    mapping: "pathname"
    strict: "0"
    reactionsEnabled: "1"
    emitMetadata: "0"
    inputPosition: "bottom"
    lightTheme: "light"
    darkTheme: "dark"
    lang: "zh-CN"
    crossorigin: "anonymous"




markup:
  goldmark:
    renderer:
      unsafe: true # 可以 unsafe，有些 html 标签和样式可能需要
  highlight:
    anchorLineNos: false # 不要给行号设置锚标
    codeFences: true # 代码围栏
    noClasses: false # TODO: 不知道干啥的，暂时没必要了解，不影响展示
    lineNos: true # 代码行
    lineNumbersInTable: false # 不要设置成 true，否则如果文章开头是代码的话，摘要会由一大堆数字(即代码行号)开头文章
    # 这里设置 style 没用，得自己加 css
    # style: "github-dark"
    # style: monokai
outputs:
  home:
    - HTML # 生成的静态页面
    - RSS # 这个其实无所谓
    - JSON # necessary for search, 这里的配置修改好之后，一定要重新生成一下

```
