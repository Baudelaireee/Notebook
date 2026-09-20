# M1 上下册合并版

入口为 main.tex；已通过本机 TeX Live 2026 的 pdfLaTeX + Biber 编译，最终 PDF 共 214 页。

## 编译

在本目录运行：

```sh
latexmk -pdf main.tex
```

或将整个项目上传 Overleaf，主文档选择 main.tex，编译器使用 pdfLaTeX。

## 合并方式

- 上册正文放入 chapters/upper.tex；下册保留原有四个章节文件及顺序。
- 共用一个 setup.tex、封面、目录和参考文献表；章节、页码、公式连续编号。
- 全书使用下册的一套环境定义。上册 upper 前缀和 plain 后缀已移除，统一使用 theorem、lemma、definition 等普通环境；下册已有 color... 彩框环境保留。
- theorem、proposition、corollary、lemma、claim 及其彩框版本共用 theorem 计数器；definition、example、problem 各自与对应彩框版本共享计数器，均按节重置。
- 定理超链接目标加入章节信息，避免重置编号后跳转错误；封面禁用页码锚点，避免与目录第一页冲突。
- 全书采用下册的段落设置：不缩进，段间距 12pt。
- 保留正文需要的 ann、mm 命令；移除未使用的上册 note、solution 环境及其专用样式。
- 图片按 assets/upper、assets/lower 分开存放，避免同名文件冲突。
- 原始两个项目未修改；正文未作数学内容校订。

## 已知问题

- 上册原稿引用 analytic continuity series，但没有对应 label；合并版第 43 页仍显示未解析引用。未猜测其目标。
- 编译日志有 8 处 overfull hbox 警告，最大约 24.35pt；未改写正文公式来消除这些警告。
- 部分数学标题产生 PDF 书签字符串警告，不影响正文公式。
- 章节采用连续编号，因此下册章节编号会随上册长度变化；原稿中手工写出的编号不自动更新。

已检查标签无重名、参考文献全部解析，并抽查目录、上下册正文与分部页。

## 本次验证

重新完整编译成功；没有环境冲突、重复 PDF 目标或未解析文献。仅保留原稿的一处缺失引用。对照原始项目确认，正文仅更改环境名称和图片路径，数学内容未改写。已抽查统一后的上册定理排版。
