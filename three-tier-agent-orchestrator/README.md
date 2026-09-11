# 律师三层代理编排

这是面向律师工作的 Codex skill。它将文件处理、法律分析和复杂复核分给不同模型：

| 模型 | 工作 |
| --- | --- |
| GPT-5.6 Luna Max | 文件盘点与读取、OCR、客观提取、版本差异、Word/PDF/Excel 创建编辑、Track Changes、输出与渲染验证 |
| GPT-5.6 Sol Medium | 边界明确的合同审阅、法律分析、风险说明、Request List、审阅意见和专业中文起草 |
| GPT-6 Astra Low | 跨文件或跨来源冲突、复杂交易结构、重大性排序、高风险结论和最终实质复核 |

文件型法律任务默认采用：

`Luna 提取材料 → Sol/Astra 分析和定稿 → Luna 制作输出文件 → Sol/Astra 复核实质内容`

Luna 只执行可追溯、可机械验证的文件任务，不决定法律适用、风险等级、条款效力或最终措辞。OCR 结果必须保留页码和不确定项，关键内容应回看原始页面。Sol 和 Astra 必须区分文件原文、管理层陈述、公开信息、投诉或指控、代理推断与已核实事实。

## 使用

在 Codex 中输入：

```text
$three-tier-agent-orchestrator
```

然后描述律师工作、材料范围、审阅立场和希望得到的交付物。例如：

```text
使用 $three-tier-agent-orchestrator 审阅这组融资文件：Luna 读取并整理全文和版本差异，Sol 从贷款人立场形成逐条审阅意见，Astra 处理跨文件冲突和重大风险；如需 Word，由 Luna 按定稿文字制作并渲染检查。
```

## 安装

```bash
git clone https://github.com/irons163/three-tier-agent-orchestrator.git "${CODEX_HOME:-$HOME/.codex}/skills/three-tier-agent-orchestrator"
```

安装或更新后，如当前任务未重新加载该 skill，请新建任务；仍未出现时重启 Codex App。
