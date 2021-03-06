# pyspider

* PySpider：一个国人编写的强大的网络爬虫系统并带有强大的WebUI。采用Python语言编写，分布式架构，支持多种数据库后端，强大的WebUI支持脚本编辑器，任务监视器，项目管理器以及结果查看器。[在线示例](http://demo.pyspider.org/)

* pyspider是作者之前做的一个爬虫架构的开源化实现。主要的功能需求是：
    1. 抓取、更新调度多站点的特定的页面
    2. 需要对页面进行结构化信息提取
    3. 灵活可扩展，稳定可监控

* 而这也是绝大多数python爬虫的需求 —— 定向抓取，结构化化解析。但是面对结构迥异的各种网站，单一的抓取模式并不一定能满足，灵活的抓取控制是必须的。为了达到这个目的，单纯的配置文件往往不够灵活，于是，通过脚本去控制抓取是我最后的选择。
  而去重调度，队列，抓取，异常处理，监控等功能作为框架，提供给抓取脚本，并保证灵活性。最后加上web的编辑调试环境，以及web任务监控，即成为了这套框架。

* pyspider的设计基础是：以python脚本驱动的抓取环模型爬虫
    1. 通过python脚本进行结构化信息的提取，follow链接调度抓取控制，实现最大的灵活性
    2. 通过web化的脚本编写、调试环境。web展现调度状态
    3.  抓取环模型成熟稳定，模块间相互独立，通过消息队列连接，从单进程到多机分布式灵活拓展



* 目录
    * [01.基础](01.Basic)
    * [02.常用](02.Framework)
    * [03.项目](03.Project)
    * [04.总结](04.Summary)

* 相关资料
    * [官方文档](http://docs.pyspider.org/)
    * [最新版本](https://github.com/binux/pyspider/releases)
    * [简介](http://www.pyspider.cn/page/1.html)