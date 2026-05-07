# `life_history.pdf` 复现执行清单

## 0. 复现目标

基于当前文件夹中的下列作者材料，尽可能复现 `life_history.pdf` 的主要结果、表格与结论：

- 论文：`life_history.pdf`
- 原始数据：`Dataset.csv`
- 编码册：`codeBook.xlsx`

目标不是“重新跑一遍相关分析”这么笼统，而是按论文结构逐项确认：

1. 样本是否与论文一致（最终 `N = 138`）
2. 量表得分是否能从原始题项重建
3. Table 1–6 是否能复现或近似复现
4. 主结论是否成立：
   - 更快的 life history strategy 与更多 psychopathology symptoms 相关
   - 更快的 life history strategy 与更高 aggression 相关
   - 更差 attachment 与更快 life history strategy 相关
   - self-harm 与 sex moderation 结果不显著

---

## 1. 先建立复现工作目录

建议在当前目录新建如下结构：

```text
replication/
  01_raw/
  02_clean/
  03_derived/
  04_output/
  05_logs/
  06_scripts/
```

### 本步产出
- `replication/` 目录结构

### 完成标准
- 后续所有中间文件、结果表、日志都有固定落点，不混在根目录

---

## 2. 固定一份“变量字典”

先把 `codeBook.xlsx` 转成可读的 CSV 或 markdown 表，后面所有计分都以它为准，不要直接凭论文描述猜题项。

### 已确认的变量组
- 人口学/家庭结构：`Age`, `Sex`, `Bio_Sib`, `Half_Sib`, `Step_Sib`, `Live_Parents`, `StepM`, `StepF`, `Parent_Partner`
- Attachment 题项：`AAQ_01`–`AAQ_09`
- DSM-5 症状题项：`DSM5_01`–`DSM5_23`
- Aggression 题项：`BPAS_01`–`BPAS_29`
- Mini-K 题项：`MiniK_01`–`MiniK_20`
- HKSS 题项：`HKSS_01`–`HKSS_22`
- Self-harm 原始题项：`SH_01`–`SH_17f`
- 数据中现成总分/派生变量：
  - `AAQ_Angry`, `AAQ_Avail`, `AAQ_Goal`, `Attach_Total`
  - `AQ_Physical`, `AQ_Verbal`, `AQ_Anger`, `AQ_Hostility`, `Aggresion_Total`
  - `DSM5_Total`, `MiniK_Total`, `HKSS_Total`, `SH_Total`
  - `Stepparent`, `Stepparent_N`

### 特别注意
`codeBook.xlsx` 已标明至少这些 reversed items：
- `AAQ_04`
- `AAQ_05`
- `AAQ_06`
- `AAQ_07`
- `AAQ_08`
- `AAQ_09`

先不要假设别的量表没有反向计分；要继续逐行核对 codebook 或论文原始量表说明。

### 本步产出
- `replication/01_raw/codebook_export.csv`
- `replication/05_logs/variable_map.md`

### 完成标准
- 你能明确说出每个论文结果变量对应哪些原始列

---

## 3. 读入数据并核对样本量

先读取 `Dataset.csv`，确认：

1. 原始行数是多少
2. 最终有效样本是否就是论文摘要中的 `N = 138`
3. 是否存在需要排除的记录
4. 是否有明显非法值、空字符串、文本污染、重复 ID

### 必做检查
- 行数、列数
- `SMID` 是否唯一
- `Age` 范围是否与论文一致（论文提到年龄范围大约 16–69 岁）
- `Sex` 编码是否为 `1=Male, 2=Female`
- 缺失值如何表示：空白、空格、`NA`、异常数字
- 各总分变量是否已经由作者预先算好

### 建议输出
- `n_raw`
- `n_unique_smid`
- `n_after_exclusion`
- 各主要变量缺失数

### 本步产出
- `replication/02_clean/01_imported.rds` 或 `01_imported.csv`
- `replication/05_logs/sample_audit.md`

### 完成标准
- 你能解释为什么分析样本是 138，或者明确指出目前还不能解释

---

## 4. 明确缺失值与异常值规则

这一步必须先定规则，再跑分析。否则后面任何相关系数都不可信。

### 至少要回答
- 论文是否使用 listwise deletion？还是每个分析按 pairwise complete observations？
- `SH_**` 中空白是“未发生”还是“缺失”？
- Mini-K 的 `-2` 到 `2` 是否全都合法
- HKSS 的 `1` 到 `5` 是否全都合法
- DSM-5 的 `0` 到 `4` 是否全都合法
- `SH_01b` 这类频数变量中的 `1000`, `38657` 等极端值是否按原样保留

### 原则
- 不要主观清洗极端 self-harm 频数，除非论文或 codebook 明确要求
- 所有清洗动作都要写进日志

### 本步产出
- `replication/05_logs/cleaning_rules.md`
- `replication/02_clean/02_cleaned.csv`

### 完成标准
- 任一条数据被修改/转码/排除时，都能追溯原因

---

## 5. 重建作者的派生变量，而不是直接盲信现成总分

数据里已经有 `MiniK_Total`, `HKSS_Total`, `DSM5_Total`, `SH_Total`, `Attach_Total` 等变量，但复现时要做两件事：

1. 用原始题项自行重算一遍
2. 与作者现成总分逐列比对

如果完全一致，后面可直接使用作者总分；如果不一致，必须先定位差异来源。

### 5.1 Attachment
根据现有数据，应至少核对：
- `AAQ_Angry`
- `AAQ_Avail`
- `AAQ_Goal`
- `Attach_Total`

### 5.2 Aggression
核对：
- `AQ_Physical`
- `AQ_Verbal`
- `AQ_Anger`
- `AQ_Hostility`
- `Aggresion_Total`

### 5.3 Life history strategy
核对：
- `MiniK_Total`
- `HKSS_Total`

论文写明：
- Mini-K：20 题，Likert `-2` 到 `+2`，总分越高表示越慢的 life history strategy
- HKSS：22 题，Likert `1` 到 `5`

### 5.4 Psychopathology
核对：
- `DSM5_Total`

论文写明：
- `DSM5_01`–`DSM5_23` 求和形成总 psychopathology severity index

### 5.5 Self-harm
核对：
- `SH_Total`

论文写明：
- `SH_Total` 是 17 种 self-harm 方法发生频数之和，不是简单 yes/no 计数

### 本步产出
- `replication/03_derived/recomputed_scores.csv`
- `replication/05_logs/score_validation.md`

### 完成标准
- 每个总分都能报告“与作者原始总分一致/不一致，以及差几行、差多少”

---

## 6. 先复现描述统计，再碰主分析

论文的逻辑顺序很清楚：先 preliminary analyses，再 main analyses。不要一上来就跑 partial correlations。

### 6.1 基本描述统计
对以下变量计算：
- `Age`
- `MiniK_Total`
- `HKSS_Total`
- `DSM5_Total`
- `SH_Total`
- `Attach_Total`
- `AQ_Physical`
- `AQ_Verbal`
- `AQ_Anger`
- `AQ_Hostility`
- `Aggresion_Total`

输出：
- `N`
- `Mean`
- `SD`
- `Min`
- `Max`

### 6.2 量表内部一致性
论文提到 Mini-K 和 HKSS 在样本中有较好 internal consistency，还提到二者相关约 `r = .71`。

因此至少要算：
- Mini-K 的 Cronbach's alpha
- HKSS 的 Cronbach's alpha
- Mini-K 与 HKSS 的 Pearson correlation

### 本步产出
- `replication/04_output/table1_descriptives.csv`
- `replication/04_output/table1_reliability.csv`

### 完成标准
- Table 1 核心统计量大体可对上论文数量级

---

## 7. 复现论文的 Table 2：DSM-5 各条目阈值比例

论文 Table 2 不是总分，而是“达到进一步评估阈值的参与者百分比”。

### 规则
按论文写法：
- 大多数 DSM-5 条目：评分 `>= 2` 记为达到阈值
- suicidal ideation、psychosis、substance use：评分 `>= 1` 即可能 warrant further inquiry

### 你要做的
1. 给 `DSM5_01`–`DSM5_23` 逐题设阈值
2. 计算每题达到阈值的人数与百分比
3. 与论文 Table 2 对照

### 本步产出
- `replication/04_output/table2_dsm_thresholds.csv`
- `replication/05_logs/table2_comparison.md`

### 完成标准
- 你能逐题指出哪些比例完全一致，哪些有偏差

---

## 8. 复现论文的 Table 3：self-harm 各类型频数

论文 Table 3 汇报的是 women / men 在各类 self-harm 行为上的频数与百分比。

### 你要做的
1. 明确 `SH_01`–`SH_17` 每个主变量对应哪一种 self-harm 行为
2. 按 `Sex` 分组（1=Male, 2=Female）
3. 对每类行为统计：
   - 发生人数
   - 组内百分比
4. 输出与论文相同结构的表

### 注意
- Table 3 看的是各方法是否发生过，不是频次总和
- 因此这里大概率要把 `SH_01`–`SH_17` 主变量转成 yes/no 指标

### 本步产出
- `replication/04_output/table3_selfharm_by_sex.csv`

### 完成标准
- 女性/男性各方法分布与论文方向一致

---

## 9. 复现 Table 4：subject variables 与主要变量的相关

论文结果部分写明，先做一组相关分析检查 age 和 sex 对主要变量的影响；并据此把 age 作为后续主分析协变量。

### 你要做的
计算 `Age`、`Sex` 与下列变量的关系：
- attachment 指标
- aggression 指标
- `DSM5_Total`
- `SH_Total`
- `MiniK_Total`
- `HKSS_Total`

### 重点核对论文结论
- 年龄更大者：attachment 更安全、aggression 更低、psychopathology 更低
- sex 基本无显著关系，除了 anger 上 men 更高

### 本步产出
- `replication/04_output/table4_subject_correlations.csv`

### 完成标准
- 能解释为什么主分析要控制年龄

---

## 10. 复现 Table 5：主相关分析（核心）

这是整篇文章的中心。

论文明确说明：
- 使用 **partial correlations**
- 控制变量：`Age`
- 做了多重比较后采用 **Bonferroni correction**
- 显著性阈值设为 `p < .002`（文中写为 `.05 / 30 = .001666` 近似）

### 10.1 Life history × family structure
自变量：
- `MiniK_Total`
- `HKSS_Total`

因变量：
- `Bio_Sib`
- `Half_Sib`
- `Step_Sib`
- `Stepparent` 或与之等价的 step-parent 指示变量

### 10.2 Life history × psychopathology
自变量：
- `MiniK_Total`
- `HKSS_Total`

因变量：
- `DSM5_Total`
- `SH_Total`

### 10.3 Life history × attachment
因变量：
- `AAQ_Angry`
- `AAQ_Avail`
- `AAQ_Goal`
- `Attach_Total`（若论文表中用了总分，也一起列）

### 10.4 Life history × aggression
因变量：
- `AQ_Physical`
- `AQ_Verbal`
- `AQ_Anger`
- `AQ_Hostility`
- `Aggresion_Total`

### 论文关键预期
- faster life strategy ↔ more psychopathology
- faster life strategy ↔ more aggression
- faster life strategy ↔ poorer attachment
- family structure 部分大多不显著，最多只有趋势
- verbal aggression 可能是不显著例外

### 本步产出
- `replication/04_output/table5_partial_correlations.csv`
- `replication/05_logs/table5_interpretation.md`

### 完成标准
- 能逐条对应论文 3.2.1–3.2.4 的结论

---

## 11. 复现 moderation analyses

论文写明用 Hayes (2013) 的 moderation procedure，`Sex` 为 moderator，`Age` 为 covariate。

### 需要复现的两个调节分析

#### 11.1 Sex 是否调节 life history → self-harm
模型形式可写为：

```text
SH_Total ~ LifeHistory + Sex + LifeHistory*Sex + Age
```

其中 LifeHistory 分别用：
- `MiniK_Total`
- `HKSS_Total`

#### 11.2 Sex 是否调节 life history → aggression
模型形式可写为：

```text
Aggresion_Total ~ LifeHistory + Sex + LifeHistory*Sex + Age
```

同样分别用：
- `MiniK_Total`
- `HKSS_Total`

### 论文结论
- 没有显著 sex main effect 或 sex × life history interaction 支持这些调节假设

### 本步产出
- `replication/04_output/moderation_selfharm.csv`
- `replication/04_output/moderation_aggression.csv`

### 完成标准
- 至少能明确交互项是否显著，以及方向是否与论文一致

---

## 12. 复现 Table 6：回归分析

论文写得很清楚：

> 分别以 Mini-K 与 HKSS 为因变量回归到 attachment，上述回归同时控制 age、以及 half/step/full siblings 数量。

### 模型 1
```text
MiniK_Total ~ attachment + Age + Bio_Sib + Half_Sib + Step_Sib
```

### 模型 2
```text
HKSS_Total ~ attachment + Age + Bio_Sib + Half_Sib + Step_Sib
```

### 关键问题
- 这里的 `attachment` 究竟用 `Attach_Total` 还是 AAQ 三个分量表？
- 必须以 Table 6 的实际列名为准。

如果论文 Table 6 用的是总 attachment score，就用 `Attach_Total`。
如果用的是多个 attachment subscales，就分别纳入。

### 论文核心结论
- perceived parental support 能显著预测 life history strategy
- 且这种预测独立于 sibling counts

### 本步产出
- `replication/04_output/table6_regressions.csv`
- `replication/05_logs/table6_model_spec.md`

### 完成标准
- 能明确 attachment 项在两个模型中的系数、方向和显著性

---

## 13. 做一份“论文-复现对账表”

到这一步不要只说“差不多复现了”。要逐表逐结论对账。

建议建一张总表，字段如下：

- `paper_section`
- `paper_result`
- `replication_result`
- `match_status` (`exact / close / mismatch / unclear`)
- `notes`

### 至少覆盖
- Table 1 描述统计
- Table 2 DSM 阈值比例
- Table 3 self-harm by sex
- Table 4 subject variable correlations
- Table 5 partial correlations
- Table 6 regressions
- moderation 结论
- 摘要中的核心结论

### 本步产出
- `replication/04_output/replication_scorecard.csv`
- `replication/05_logs/final_comparison.md`

### 完成标准
- 任一结论都能定位到具体统计输出

---

## 14. 如果结果对不上，按这个顺序排查

### 第一层：样本问题
- 你的 N 不是 138
- 某些分析用了不同缺失处理
- 你把缺失当成 0，或把 0 当成缺失

### 第二层：计分问题
- reversed item 漏处理
- 某个分量表题项纳入错了
- self-harm 总频数算法与作者不一致

### 第三层：模型问题
- 你用 Pearson correlation，但论文用 partial correlation
- 忘了控制 `Age`
- Bonferroni 阈值没按论文设定
- moderation 中 `Sex` 编码反了

### 第四层：表格解释问题
- 论文表里用的是分量表，不是总分
- 论文汇报的是百分比，不是均值
- 论文保留小数位不同导致看起来不一致

---

## 15. 最后应交付的文件清单

最低可交付版本应包括：

- `life_history_replication_checklist.md`（本文件）
- `replication/05_logs/sample_audit.md`
- `replication/05_logs/cleaning_rules.md`
- `replication/05_logs/score_validation.md`
- `replication/04_output/table1_descriptives.csv`
- `replication/04_output/table2_dsm_thresholds.csv`
- `replication/04_output/table3_selfharm_by_sex.csv`
- `replication/04_output/table4_subject_correlations.csv`
- `replication/04_output/table5_partial_correlations.csv`
- `replication/04_output/table6_regressions.csv`
- `replication/04_output/replication_scorecard.csv`

---

## 16. 最直接的执行顺序

如果你现在就开始做，按下面顺序最稳：

1. 导出 codebook
2. 导入 `Dataset.csv`
3. 核对 N 与缺失值规则
4. 重算所有总分并验证作者现成总分
5. 复现 Table 1
6. 复现 Table 2
7. 复现 Table 3
8. 复现 Table 4
9. 复现 Table 5
10. 跑两个 moderation
11. 复现 Table 6
12. 做最终对账表

---

## 17. 一句判断

这篇文章是可以做“接近完整复现”的，因为数据和 codebook 都在，而且数据里已经保留了大量作者派生变量。真正的难点不是能不能跑出结果，而是：

- 先把样本规则和缺失规则锁死
- 再验证作者总分是如何从题项算出来的
- 最后严格按论文顺序复现各张表
