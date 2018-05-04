# Python语言以太坊虚拟计算机的实现
[![Join the chat at https://gitter.im/ethereum/py-evm](https://badges.gitter.im/ethereum/py-evm.svg)](https://gitter.im/ethereum/py-evm)
[![Documentation Status](https://readthedocs.org/projects/py-evm/badge/?version=latest)](http://py-evm.readthedocs.io/en/latest/?badge=latest)

[Documentation hosted by ReadTheDocs](http://py-evm.readthedocs.io/en/latest/)

## Py-EVM介绍

Py-EVM是用python语言编写的新的以太坊虚拟计算机的简称；该项目当前处于积极发展阶段，通过ethereum/test提供的测试套件来快速发展。在设计决策方面所取得的快速进展、启发以及一些代码直接从PyEthereum代码库移植，多亏有Vitalik及现有的PyEthereum代码，对此我们要说一声感谢。

## 目标

Py-EVM最终的目标是实现完全的Python语言化的以太坊虚拟机，为公有链、私有链的使用场景提供各种各样的支持；我们聚焦于开发出具备良好定义的、友好的、易于理解的文件，同时也作为一个功能齐全的主网节点来运行。

Py-EVM的目标：
- 作为一个完全使用Python语言实现的并被广泛使用的以太坊虚拟机案例
- 为客户在顶部构建全节点或者轻量节点提供低级别的API（应用程式界面）
- 易于理解和修改
- 高度灵活性以支持研究和私有链等其他用例

### 三位一体
尽管Py-EVM提供了以太坊虚拟机（EVM）的低级别的APIs，但它的目标并不是直接实现一个全节点或者轻量级的节点。基于Py-EVM我们提供了一个完整节点的基本实现叫做“三位一体（Trinity）”,在未来基于Py-EVM应该会有一些替代客户。

### 第一步：阿尔法版本
该计划是从一个符合测试目的MVP，阿尔法级别版本开始；我们将要收集一些早期的试用者关于我们的架构和API的选择这方面的软件漏洞和一般用户反馈。
#### 博客文章
- https://medium.com/@pipermerriam/py-evm-part-1-origins-25d9ad390b
## 发展
Py-EVM依赖于一个所有客户端的通用测试子模块，所以你需要通过`--recursive`这个标签来克隆回购。例：
```st
git clone --recursive git@github.com:ethereum/py-evm.git
```
Py-EVM需要python 3.且最佳的保证python 3的干净的使用环境的方式是`virtualenv`。像：
```sh
# once
$ virtualenv -p python3 venv

# each session:
$ . venv/bin/activate
```
之后按照以下步骤安装python的包：
```sh
pip install -e .[dev]
```
### 运行测试
您可以运行测试：
```sh
pytest
```
或者您可以安装`tox`完整节点的测试套件。
### 版本发行
在这里需要通过Pandoc把markdown格式的README文件转换为合适的格式，一边可以在pypi上正确显示。对于类似Debian的系统：
```
apt install pandoc
```
或者在OSX系统上 ：
```
brew install pandoc
```
发布新版本：
```
bumpversion $$VERSION_PART_TO_BUMP$$
git push && git push --tags
make release
```
#### 如何颠覆
这个回购版本的格式`{major}.{minor}.{patch}`是稳固的，`{major}.{minor}.{patch}-{stage}.{devnum}`不稳固的（`stage`可能是阿尔法或者贝塔版本）

依序发行下一代版本，使用bumpcersion并确定哪一部分需要冲撞，例如`bumpversion minor`或者`bumpversion devnum`.

如果你是处于beta版本，`bumpversion stage`将是一个稳定的版本。

要在当前稳定版本发布一个不稳定的版本，需要明确指定新的版本，如`bumpversion --new-version 4.0.0-alpha.1 devnum` 
