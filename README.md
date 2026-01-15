# Helloworld Blog

基于 Quarto 构建的个人博客，自动部署到 GitHub Pages。

## 📁 目录结构

```
yjy12lcp.github.io/
├── index.qmd              # 首页
├── about.qmd              # 个人简介
├── _quarto.yml            # Quarto 配置
├── styles.css             # 自定义样式
│
├── papers/                # 论文阅读页面
│   └── index.qmd
│
├── projects/              # 项目实现页面
│   └── index.qmd
│
├── notes/                 # 学习笔记页面
│   └── index.qmd
│
├── novel/                 # 小说创作页面
│   └── index.qmd
│
└── posts/                 # 所有文章存放处
    ├── papers/            # 论文笔记
    ├── projects/          # 项目文档
    ├── notes/             # 学习笔记
    └── novel/             # 小说内容
        ├── worldview/     # 世界观设定
        ├── characters/    # 人物志
        ├── keyplots/      # 关键剧情
        └── chapters/      # 小说正文
```

---

## 📖 发布论文笔记

### 1. 创建文章目录

```bash
# 格式: posts/papers/YYYY-MM-DD-文章标识/
mkdir posts/papers/2026-01-10-bert-paper
```

### 2. 创建 `index.qmd` 文件

````markdown
---
title: "BERT: Pre-training of Deep Bidirectional Transformers"
description: "谷歌提出的预训练语言模型"
date: 2026-01-10
categories: ["NLP", "预训练", "Transformer"]
---

```{=html}
<div class="paper-meta">
  <div class="paper-info">
    <span class="paper-venue">📍 NAACL 2019</span>
    <span class="paper-authors">👥 Devlin, Chang, Lee, Toutanova</span>
    <a href="https://arxiv.org/abs/1810.04805" target="_blank" class="paper-link">📄 arXiv</a>
  </div>
  <div class="paper-tags">
    <span class="tag">bert</span>
    <span class="tag">language-model</span>
    <span class="tag">fine-tuning</span>
  </div>
</div>
```

## 一句话总结

使用 Masked LM 和 Next Sentence Prediction 进行双向预训练。

## 核心贡献

1. **Masked Language Model**: 随机遮盖 15% 的 token 进行预测
2. **双向编码**: 同时利用左右上下文信息

## 关键公式

$$
\mathcal{L} = \mathcal{L}_{MLM} + \mathcal{L}_{NSP}
$$

## 复现笔记

- 在我的数据集上的表现：...
- 遇到的坑：...
````

### 3. 添加图片（可选）

将图片放在同一目录下：

```
posts/papers/2026-01-10-bert-paper/
├── index.qmd
├── bert-architecture.png
└── results.png
```

在文章中引用：

```markdown
![BERT 架构](bert-architecture.png)
```

---

## 🛠️ 发布项目文档

### 1. 创建文章目录

```bash
mkdir posts/projects/2026-01-10-llm-inference
```

### 2. 创建 `index.qmd` 文件

```markdown
---
title: "LLM 推理优化实战"
description: "从 PyTorch 到 TensorRT 的性能优化之路"
date: 2026-01-10
categories: ["推理优化", "TensorRT", "部署"]
tags: ["llm", "optimization", "quantization"]
---

## 项目目标

将 7B 参数的 LLM 部署到单卡 A100，实现 50 tokens/s 的推理速度。

## 技术栈

- **框架**: PyTorch → ONNX → TensorRT
- **量化**: INT8 动态量化
- **优化**: KV Cache, Flash Attention

## 开发流程

### 1. 模型导出

\`\`\`python
import torch

model = load_model("llama-7b")
torch.onnx.export(model, dummy_input, "model.onnx")
\`\`\`

### 2. TensorRT 转换

\`\`\`bash
trtexec --onnx=model.onnx --saveEngine=model.trt --int8
\`\`\`

## 性能对比

| 方案 | 速度 (tokens/s) | 显存 (GB) |
|------|-----------------|-----------|
| PyTorch FP16 | 15 | 28 |
| TensorRT INT8 | 52 | 12 |

## 踩坑记录

1. ONNX 导出时的 dynamic axes 设置...
2. TensorRT 不支持的算子替换...
```

---

## 📝 发布学习笔记

### 1. 创建文章目录

```bash
mkdir posts/notes/2026-01-15-ml-course-day-01
```

### 2. 创建 `index.qmd` 文件

```markdown
---
title: "机器学习课程 Day 01"
description: "线性回归与梯度下降的核心要点"
date: 2026-01-15
categories: ["机器学习", "课程笔记"]
tags: ["linear-regression", "gradient-descent"]
---

## 今日主题

线性回归的目标函数与梯度下降更新公式。

## 核心概念

- 目标函数：均方误差
- 梯度更新：$w := w - \alpha \nabla J(w)$

## 练习复盘

1. 手推导梯度过程，注意矩阵维度
2. 学习率调参：0.01 比 0.1 更稳定
```

---

## 📚 发布小说内容

小说分为四个部分，每个部分有独立的分类：

### 🌍 世界观设定

```bash
mkdir posts/novel/worldview/2026-01-10-magic-system
```

```markdown
---
title: "魔法体系设定"
description: "五大元素与魔法等级划分"
date: 2026-01-10
---

## 元素体系

世界存在五种基础元素：火、水、土、风、雷。

## 魔法等级

1. **学徒级**: 能操控单一元素的基础形态
2. **大师级**: 可以组合两种元素
3. **传奇级**: 领悟元素本源

## 禁忌魔法

...
```

### 👤 人物志

```bash
mkdir posts/novel/characters/2026-01-10-hero-profile
```

```markdown
---
title: "人物：艾伦·沃克"
description: "故事主角的完整设定"
date: 2026-01-10
---

## 基本信息

- **姓名**: 艾伦·沃克
- **年龄**: 22
- **职业**: 魔法学徒

## 性格特点

- 表面冷漠，内心热情
- 对朋友极度忠诚
- 有严重的选择困难症

## 能力成长线

| 章节 | 等级 | 新技能 |
|------|------|--------|
| 第1章 | 学徒 | 火球术 |
| 第10章 | 进阶 | 火焰风暴 |

## 关键关系

- **导师**: 老魔法师梅林
- **挚友**: 剑士洛基
- **宿敌**: 暗影法师
```

### ⚡ 关键剧情

```bash
mkdir posts/novel/keyplots/2026-01-10-first-battle
```

```markdown
---
title: "剧情节点：首战"
description: "主角第一次面对真正的敌人"
date: 2026-01-10
---

## 场景

废弃的魔法塔顶层

## 参与人物

- 艾伦（主角）
- 暗影刺客（敌方）
- 梅林（导师，远程支援）

## 事件概要

艾伦独自追踪线索来到废塔，却发现这是一个陷阱...

## 转折点

1. 艾伦首次觉醒隐藏的雷元素天赋
2. 导师梅林的真实身份暴露

## 后续影响

- 艾伦开始修炼双元素
- 与暗影组织的正式对抗开始
```

### 📜 小说正文

```bash
mkdir posts/novel/chapters/2026-01-10-chapter-05
```

```markdown
---
title: "第五章：觉醒"
description: "艾伦在生死关头觉醒了隐藏的力量"
date: 2026-01-10
---

夜幕降临，废弃的魔法塔在月光下投下诡异的影子。

艾伦紧握着手中的法杖，额头上渗出细密的汗珠。他能感觉到，某种不属于这个世界的存在正在塔顶等待着他。

"你终于来了。"

一个沙哑的声音从黑暗中传来。

艾伦猛地转身，只见一道黑影从阴影中缓缓凝聚成形。那是一个身披黑袍的男人，面容隐藏在兜帽之下，只有一双猩红的眼睛在黑暗中闪烁。

"你是谁？"艾伦强压下心中的恐惧，尽量让自己的声音保持平稳。

"我？"黑袍人发出一阵低沉的笑声，"我是来送你上路的人。"

---

*（待续...）*
```

---

## 🚀 发布流程

### 本地预览

```bash
quarto preview
```

### 提交发布

```bash
git add .
git commit -m "add: rebuild"
git push origin main
```

GitHub Actions 会自动构建并部署到 `https://yjy12lcp.cn`

---

## 📝 Front Matter 速查

### 论文笔记

```yaml
---
title: "论文标题"
description: "一句话描述"
date: YYYY-MM-DD
categories: ["领域1", "领域2"]
---
```

然后在正文开头添加论文信息卡：

```html
<div class="paper-meta">
  <div class="paper-info">
    <span class="paper-venue">📍 会议名称</span>
    <span class="paper-authors">👥 作者1, 作者2</span>
    <a href="论文链接" target="_blank" class="paper-link">📄 arXiv</a>
  </div>
  <div class="paper-tags">
    <span class="tag">标签1</span>
    <span class="tag">标签2</span>
  </div>
</div>
```

### 项目文档

```yaml
---
title: "项目名称"
description: "项目简介"
date: YYYY-MM-DD
categories: ["技术栈1", "技术栈2"]
tags: ["标签1", "标签2"]
---
```

### 小说内容

```yaml
---
title: "章节/设定标题"
description: "简短描述"
date: YYYY-MM-DD
---
```

---

## 🎨 Markdown 增强语法

### 代码块（带语法高亮）

````markdown
```python
def hello():
    print("Hello, World!")
```
````

### 数学公式

```markdown
行内公式：$E = mc^2$

独立公式：
$$
\nabla \cdot \mathbf{E} = \frac{\rho}{\varepsilon_0}
$$
```

### 提示框

```markdown
::: {.callout-note}
这是一个提示
:::

::: {.callout-warning}
这是一个警告
:::

::: {.callout-tip}
这是一个技巧
:::
```

### 折叠内容

```markdown
::: {.callout-note collapse="true"}
## 点击展开详情

隐藏的内容...
:::
```

---

## 📞 联系

- GitHub: [github.com/yjy12lcp](https://github.com/yjy12lcp)
- Email: helloworld12yjy@gmail.com
