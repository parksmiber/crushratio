# crushratio

**算出提示词里冗余与有效信息的比例。**

`crushratio` —— 统计提示词各段的字符数占比，标出重复表达与可压缩部分，给出压缩比估算

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`crushratio.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install parksmiber-crushratio
```

装完直接用命令名调用：

```bash
crushratio --help
```

也可以不用安装，直接把 `crushratio.py` 拷走用——它只依赖标准库。

## 为什么需要它

区分「重复」与「必要冗余」——后者是刻意强调，不能算进冗余

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 提示词压缩比 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python crushratio.py --file input.txt
python crushratio.py --text "示例内容"
python crushratio.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 长度按字符与词统计，与具体 tokenizer 有偏差。
- 不判断长度是否「合理」，只报告分布。

## 跑测试

```bash
python test_crushratio.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/parksmiber/crushratio>

---

## 关于作者

parksmiber 做提示词压缩比相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://parksmiber.github.io>
- 仓库：<https://github.com/parksmiber/crushratio>

## 许可

MIT，见 [LICENSE](LICENSE)。
