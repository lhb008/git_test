# **切记，Kubebuilder的 **zh** 分支用来存放中文翻译文档，所有翻译都应该基于 **zh** 分支进行。**


# Kubebuilder 官方文档翻译指导手册

## 概要

云原生已经毫无争议的成了云计算发展的下一段旅程，而Kubernetes又毫无疑问的是云原生的重要技术之一。越来越多的企业借助于Kubernetes的强扩展能力来构建稳定高、伸缩性强的企业应用，在这个过程中CRD、Operator等成为了关键技术。基于此，[云原生社区](https://cloudnative.to/)决定将大家常用的 [kubebuilder](https://book.kubebuilder.io/) 的官方文档进行翻译，便于国内云原生爱好者能够快速的学习与Operator相关的技术。

## 翻译计划

Kubebuiler 官方文档总共4大章，28小节。计划每周翻译7小节，一个月内结束翻译工作。每周末，会提前创建好下一周需要翻译章节的issue(一个小节对应一个issue)，然后大家以认领[issue](https://github.com/cloudnativeto/kubebuilder/issues)的方式进行翻译。会每天统计并公布 `issue` 的认领情况。

## 翻译负责人
| 责任范围 | 人员 |GitHub 账号 |
| :---: | :---: |:---: |
| 翻译跟踪、文档更新 | 马景贺 | lhb008|
| 翻译跟踪、文档更新 | 梁斌 | zhliangbin|
| 翻译跟踪、文档更新 | 申红磊 | shenhonglei|

## 翻译志愿者信息登记

请翻译志愿者在此地址先进行信息登记：[翻译志愿者信息登记](https://docs.google.com/spreadsheets/d/1fHwilU5NttQgCg-o8p2aK1GOWxVZsX2GBzTwm0YrwgE/edit?usp=sharing)

## 基本流程

整个翻译的基本流程包括下面几个步骤：

- 任务领取：在本仓库的 Issue 页面领取待翻译的任务；
- 翻译：根据任务提示进行翻译工作；
- 提交：翻译人员提交 PR 等待 review；
- 校对：其他翻译人员对当前任务进行 review；
- 终审：管理员团队对翻译内容进行最后确认；
- 预览：和源文档进行比对，查看显示效果；
- 合并：merge 进入官方仓库，任务结束。

我们通过校对、终审两轮 review 保证翻译的质量；通过预览保证显示的准确性。翻译人员在整个流程中需要做的是领取任务，翻译，提交 PR，预览自查这几步。

## 翻译指南

下面具体介绍一下如何进行翻译工作。

### 准备工作

- 账号：微信账号和 GitHub 账号。微信用来沟通协作，Github 进行任务认领和翻译提交。

- 申请加入：请添加微信号(**majinghe11**)，并注明 **Kubebuilder 翻译加群**，通过审批后您需要登记一下基本信息，之后maintainer会将您添加到 cloudnativeto 的 GitHub 组织和翻译微信群。即可正式参与翻译。

- 为保证翻译的统一性和准确性，请在翻译前仔细阅读[术语表](https://github.com/servicemesher/istio-official-translation/blob/master/term.md)
  - 常用词汇：对常见的技术词汇给出统一的翻译；
  - 术语：文档中出现的专有技术名词，关键词，**保持原文不翻译；**

- 仓库和分支管理
  - fork [官网](https://github.com/cloudnativeto/kubebuilder)的仓库，并作为自己仓库的上游：`git remote add upstream https://github.com/cloudnativeto/kubebuilder` ；
  - 已创建 名为`zh`的branch来存放中文翻译。大家翻译的时候，可以基于 `zh` 分支进行翻译。

### 翻译流程
#### Step1：任务浏览

访问[任务列表](https://github.com/cloudnativeto/kubebuilder/issues/issues)，会看到待领取任务。领取自己感兴趣的issue时，请注意看issue的注释，如果没有被assign给别人就可以领取。

#### Step2：任务领取

找到未经认领的任务（issue 注释里面没有认领内容），在issue中(或者在微信群里)@负责人，负责人会手动把issue assign给个人。

> 注意：由于 Kubebuilder 内容不是很多，原则上，每个人每个翻译周期(一周)内只能领取一个任务，待翻译任务被成功merge到master分钟，方可领取下一个任务。

#### Step3：本地构建和预览

翻译结束后可以先在本地构建进行预览。有两种方式可以完成构建：

**用mdbook二进制包进行预览调试**

在mdbook [官网](https://github.com/rust-lang/mdBook/releases)上下载对应系统(Ubuntu, macOS)所需版本的二进制压缩包，解压后将二进制文件 `mdbook`放置到 `PATH` 路径下即可。本文以最新版本 `v0.4.1` 为例，在`Ubuntu`上进行安装示范。

```
$ wget https://github.com/rust-lang/mdBook/releases/download/v0.4.1/mdbook-v0.4.1-x86_64-unknown-linux-gnu.tar.gz
$ tar -zxvf mdbook-v0.4.1-x86_64-unknown-linux-gnu.tar.gz
$ chmod +x mdbook
$ mv mdbook /usr/local/bin
```

确认`mdbook`是否安装成功

```
mdbook v0.4.1
Mathieu David <mathieudavid@mathieudavid.org>
Creates a book from markdown files

USAGE:
    mdbook [SUBCOMMAND]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    build    Builds a book from its markdown files
    clean    Deletes a built book
    help     Prints this message or the help of the given subcommand(s)
    init     Creates the boilerplate structure and files for a new book
    serve    Serves a book at http://localhost:3000, and rebuilds it on changes
    test     Tests that a book's Rust code samples compile
    watch    Watches a book's files and rebuilds it on changes

For more information about a specific command, try `mdbook <command> --help`
The source code for mdBook is available at: https://github.com/rust-lang/mdBook
```

将fork的Kubebuilder的库中代码`clone` 至本地，并进至 `docs/book/` 目录下，然后运行 `mdbook server` 启动本地调试。

```
$ mdbook serve -p 8000 -n 0.0.0.0
2020-07-22 05:04:12 [INFO] (mdbook::book): Book building has started
+ ../../bin/literate-go supports html
+ ../../bin/literate-go
+ ../../bin/marker-docs supports html
+ ../../bin/marker-docs
2020-07-22 05:04:13 [INFO] (mdbook::book): Running the html backend
2020-07-22 05:04:14 [INFO] (mdbook::cmd::serve): Serving on: http://0.0.0.0:8000
2020-07-22 05:04:14 [INFO] (warp::server): listening on http://0.0.0.0:8000
2020-07-22 05:04:14 [INFO] (mdbook::cmd::watch): Listening for changes...
```
然后在浏览器中访问 `http://localhost:8000`(如果mdbook安装在本地，就用localhost，如果是远端服务器，则直接用远端服务器IP地址）,可以看到如下内容

![kubebuilder-debug](https://github.com/lhb008/kubebuilder/blob/zh/docs/gif/kubebuilder-debug.png?raw=true)

**以docker方式运行mdbook进行预览调试**

将fork的Kubebuilder的库中代码`clone` 至本地，并进至 `docs/book/` 目录下，然后运行以下命令来启动 `mdbook` 的docker容器

```
$ docker run --rm --name book -v $PWD:/opt -p 8000:8000 cloudnativeto/kubebuilder-book serve . -p 8000 -n 0.0.0.0
2020-07-22 05:07:39 [INFO] (mdbook::book): Book building has started
2020-07-22 05:07:39 [WARN] (mdbook::preprocess::cmd): The command wasn't found, is the "literatego" preprocessor installed?
2020-07-22 05:07:39 [WARN] (mdbook::preprocess::cmd): 	Command: ./litgo.sh
2020-07-22 05:07:39 [WARN] (mdbook::preprocess::cmd): The command wasn't found, is the "markerdocs" preprocessor installed?
2020-07-22 05:07:39 [WARN] (mdbook::preprocess::cmd): 	Command: ./markerdocs.sh
2020-07-22 05:07:39 [INFO] (mdbook::book): Running the html backend
2020-07-22 05:07:40 [INFO] (mdbook::cmd::serve): Serving on: http://0.0.0.0:8000
2020-07-22 05:07:40 [INFO] (ws): Listening for new connections on 0.0.0.0:3001.
2020-07-22 05:07:40 [INFO] (mdbook::cmd::watch): Listening for changes...
```

同样地，运行`http://locahost:8000` (如果mdbook安装在本地，就用localhost，如果是远端服务器，则直接用远端服务器IP地址)，即可看到调试界面。

#### Step4：提交 PR

如果本地调试预览没有问题，以提PR的方式将将所修改的内容进行提交(中文翻译对应的分支是`zh` 所以对应的PR也须对应`zh`分支)，我们已选择`GitHub Action` 为持续集成的构建工具，在提交完PR以后，请及时关注`GitHub Action`的构建结果。

> 将[Kubebuilder库](https://github.com/cloudnativeto/kubebuilder.git) fork至个人仓库时，`GitHub Action` 的相关配置文件也已经fork过去，自己也可以利用自己仓库的`GitHub Action`功能进行构建检查。

**提交 PR**

如果检查通过，就可以向 [Kubebuiler 官方网站提交 PR](https://github.com/cloudnativeto/kubebuilder/pulls)，PR 被合并后就可以通过 [Kubebuiler 网站预览页面](https://cloudnative.to/kubebuilder/)看到被合并后的页面。为方便管理和辨识，请遵守下面的模板定义您的 PR：

```text
标题：
zh-translation:<file_full_path>
内容：
ref: https://github.com/cloudnativeto/kubebuilder/issues/<issueID>
[ ] Configuration Infrastructure
[x] Docs
[ ] Installation
[ ] Networking
[ ] Performance and Scalability
[ ] Policies and Telemetry
[ ] Security
[ ] Test and Release
[ ] User Experience
[ ] Developer Infrastructure
```

其中，标题中的<file_full_path>是翻译的源文件路径；内容中的 ref 是当前翻译任务的 issue 链接。

#### Step5：校对（review）

校对工作由没有翻译过当前文档的其他翻译人员执行，即翻译人员互为校对人员。为保证质量，我们设置了两轮 Review：

所有翻译人员互为校对人员，分配一个翻译任务同时要确定校对任务；

- 初审：负责对翻译的内容和原文较为精细的进行对比，保证语句通顺，无明显翻译错误；
- 终审：负责对翻译的文档做概要性的检查，聚焦在行文的通顺性、一致性、符合中文语言习惯，词汇、术语准确。终审通过后由管理员 approve 当前 PR，就可以进行合并了。

**参与 Review**：所有 Kubebuilder 的 PR 都会通过 Github 机器人同步在钉钉群里，如果看到感兴趣的 PR 就在[本项目](https://github.com/servicemesher/istio-official-translation)中对应的 issue 回复一下，我们社区的 maintainer 会通过 `/assign`命令手动将 Review 工作指派给您。

**Review 的基本流程**

- 认领 Review：
  - 新提交的 PR 每天会在微信群发布，供大家认领；
  - 进入要认领的 PR，回复/review，maintainer 会将 reviewer 指派给您；
- Review 重点：
  - 打开 PR 提交的中文翻译，并找到对应 issue 中指定的源文件，逐段进行走查；
  - 词汇检查：检查译文中出现的术语、常用词汇是否遵照了术语表的要求进行翻译；
  - 格式检查：对照原文，检查译文中的标题和层次是否对应；代码块是否指定了语言；标点符号是否正确且无英文标点；超链接、图片链接是否可达；是否有错别字；
  - 语句检查：分段落通读一遍，检查是否有不通顺、语病、或者不符合中文习惯的译文（啰嗦、重复、过多的助词等）
- 提交 comment：
  - 根据发现的问题，在 PR 提交文件的对应行添加 comment，格式为`原译文=>修改后译文`；不确定的地方可加建议或询问，或发到协作群求助。

#### Step7：任务完成

通过终审后的任务会被管理员 approve，并合并到 Kubebuilder 的官方仓库中。需要您在对应的 Issue 中输入指令 `/merged`，Bot 会设置 Issue 的状态为 `finished`，并关闭 Issue。整个翻译任务就算正式完成了。您可以继续领取新的任务进行翻译，或参与校对工作。
