# 声明

本文档基于python PHIDL库绘制版图，适用于ZNGZ——TFLN芯片版图的绘制，仅限内部使用

本文档仅基于PHIDL官方文档做针对性说明，完整功能可查阅[PHIDL官方文档](https://phidl.readthedocs.io/en/latest/)

# 安装

由于依赖match-case功能，需使用python 3.10以上的版本进行安装，或使用最近版本的anaconda进行安装，安装代码为：

```
pip install -U phidl
```

如果没有安装gdspy库，则需要安装C++编译器，详细内容参见：[Installation — PHIDL documentation](https://phidl.readthedocs.io/en/latest/install.html)

建议使用pycharm社区版代码管理，后续示例均使用pycharm社区版进行演示。

# 版图定义

版图定义文件共有3个：

- 版图基本定义——basic_def
- 引用现成gds版图的结构定义——gds_def
- 使用PHIDL绘制的结构定义——struct_def

## 版图基本定义——basic_def

版图基本定义是指版图中的一般波导宽度、各层定义等，该文件一般不需要改动。

- 建立波导对象WgInit：波导对象是为了后续代码中更统一地使用一般波导的宽度，其中sm/mm表示单模/多模，c/o表示波段。

```python
class WgInit:
```

- 设置不同版本的波导宽度：可设置多个版图的版本以匹配多种不同的技术路径，引用该方法时会建立一个波导对象，并根据对应版本定义波导宽度

```python
def wg_def(version):
```

设置不同版本的层定义：可设置多个版图的版本以匹配多种不同的技术路径，引用该方法时会建立一个LayerSet，并根据对应版本定义层

```python
def layer_def(version):
```

## 引用现成gds版图的结构定义——gds_def

