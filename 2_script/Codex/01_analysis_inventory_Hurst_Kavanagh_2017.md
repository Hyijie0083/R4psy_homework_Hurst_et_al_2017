# Hurst & Kavanagh (2017) 分析清单

论文：*Life history strategies and psychopathology: the faster the life strategies, the more symptoms of psychopathology*  
作者：Jessie E. Hurst, Phillip S. Kavanagh  
期刊：*Evolution and Human Behavior* 38 (2017) 1-8

## 说明

这份清单只基于当前文件夹中的主文 PDF 整理，目标是为后续“逐个复现每一个分析”建立总目录。你要求的口径是严格全量版，因此我把主文中出现的描述性统计、信度、相关、偏相关、回归、调节分析、Bonferroni 校正，以及各张表承载的统计内容都列入。

文中明确写到存在补充材料，但本轮不展开分析补充材料内容：

- 补充材料标注位置：PDF 第 7 页，`Supplementary data to this article can be found online at doi:http://dx.doi.org/10.1016/j.evolhumbehav.2016.06.001`

## 研究设计总览

- 样本：`N = 138`
- 男性：`46`
- 女性：`92`
- 原始开始作答人数：`209`
- 因未完成全部量表而排除：`71`
- 研究设计：横断面、相关设计
- 主要自变量/预测变量：`Mini-K`、`HKSS` 两个生活史策略指标
- 主要结果变量：依恋、攻击性、精神病理症状总分、自伤频率、家庭结构变量
- 常用协变量：`age`
- 多重比较校正：主分析中的多次偏相关使用 `Bonferroni correction`，阈值设为 `p < .002`

## 分析 1：样本筛选与样本描述

- 目的：交代最终分析样本的形成过程与基本人口学特征。
- 数据/变量：
  - 起始样本数
  - 排除人数
  - 最终样本数
  - 性别构成
  - 年龄均值与标准差
  - 混合家庭相关比例
- 方法：描述性统计。
- 结果位置：`Method > 2.1 Participants and Procedure`，PDF 第 3 页。
- 关键结果：
  - `209` 人开始作答，`71` 人因未完成全部量表被排除。
  - 最终样本 `n = 138`。
  - 男性 `46` 人，女性 `92` 人。
  - 男性年龄 `M = 36.67, SD = 15.73`；女性年龄 `M = 33.13, SD = 14.16`。
  - `83.3%` 至少有 1 个 half-sibling，`89.1%` 至少有 1 个 step-sibling，`8.7%` 有 stepmother，`10.9%` 有 stepfather。
- 原文标注：
  - `Two hundred and nine participants initially started the online survey; however, 71 participants did not complete all measures and were subsequently excluded from the final analyses.`
  - `The final sample (n = 138) consisted of 46 men ... and 92 women ...`

## 分析 2：量表内部一致性与描述性统计（Table 1）

- 目的：报告核心量表及其分量表的均值、标准差和内部一致性。
- 数据/变量：
  - Attachment：`Total attachment`、`Availability`、`Goal-corrected partnership`、`Angry distress`
  - Aggression：`Total aggression`、`Physical aggression`、`Verbal aggression`、`Anger`、`Hostility`
  - Life history strategy：`Mini-K`、`HKSS`
- 方法：
  - 计算各量表/分量表的 `M`、`SD`、`Cronbach's alpha`
  - 将项目求和形成总分或分量表分数
- 结果位置：
  - `Method > 2.2 Measures`，PDF 第 3-4 页
  - `Table 1`，PDF 第 4 页
- 关键结果：
  - Attachment 总分：`M = 15.54, SD = 7.63, alpha = .92`
  - Total aggression：`M = 59.90, SD = 19.62, alpha = .93`
  - Mini-K：`M = 14.62, SD = 11.25, alpha = .84`
  - HKSS：`M = 87.34, SD = 13.64, alpha = .91`
- 原文标注：
  - `The subscales and the total measure demonstrated high internal consistency.`
  - `All the items of each of the domains, as well as the total measure, demonstrated good internal consistency...`
  - `The Mini-K demonstrated good internal consistency...`
  - `The items on the HKSS demonstrated high internal consistency...`

## 分析 3：两种生活史策略量表之间的相关

- 目的：证明 `Mini-K` 与 `HKSS` 作为生活史策略指标之间具有一致性，并说明同时纳入两者的理由。
- 数据/变量：
  - `Mini-K`
  - `HKSS`
- 方法：双变量相关分析。
- 结果位置：`Method > 2.2.3 Life History`，PDF 第 4 页。
- 关键结果：
  - `r = .71, p < .01`
- 原文标注：
  - `Both measures were included in the study to provide a more robust measurement of life history strategy and in the current sample were significantly correlated (r = .71, p < .01).`

## 分析 4：精神病理条目达到“需进一步评估阈值”的比例（Table 2）

- 目的：描述 DSM-5 cross-cutting symptom measure 各条目中，达到“需要进一步 inquiry”的参与者比例。
- 数据/变量：
  - DSM-5 Self-Rated Level 1 Cross-Cutting Symptom Measure - Adult
  - 23 个条目，对应 13 个精神病理领域
- 方法：
  - 依据量表说明，统计各条目达到阈值的人数比例
  - 同时将全部 23 个条目求和形成总精神病理指数
- 结果位置：
  - `Method > 2.2.4 Psychopathology`，PDF 第 4 页
  - `Table 2`，PDF 第 4-5 页
- 关键结果：
  - 论文报告了各条目达到阈值的百分比。
  - 总精神病理指数：`M = 40.10, SD = 14.57, range = 23 to 84`
- 原文标注：
  - `See Table 2 for the percentage of participants whom met the threshold for psychopathology symptom criteria.`
  - `As we were interested in total psychopathology severity the scores on all items were summed to produce an index of psychopathology (M = 40.10, SD = 14.57; range = 23 to 84).`

## 分析 5：各类自伤行为在男女中的频数分布（Table 3）

- 目的：描述 17 种具体自伤方式在女性和男性中的报告频数与比例。
- 数据/变量：
  - Deliberate Self-Harm Inventory 的 17 种方法
  - 性别
- 方法：
  - 统计每种自伤行为在女性和男性中的频数与百分比
  - 使用各方法的频率求和形成 `total frequency of self-harm`
- 结果位置：
  - `Method > 2.2.5 Self-Harm`，PDF 第 4 页
  - `Table 3`，PDF 第 5 页
- 关键结果：
  - 论文给出了全部 17 种自伤方式的男女频数/百分比。
  - 例如：`Cutting` 女性 `13 (14.0%)`，男性 `6 (13.0%)`。
  - `Banging head` 女性 `1 (1.1%)`，男性 `5 (10.9%)`。
- 原文标注：
  - `See Table 3 for the individual frequencies of the various self-harm behaviours.`

## 分析 6：预分析，年龄与性别和主要结果变量的相关（Table 4）

- 目的：检验年龄与性别是否和各因变量有关，以决定后续主分析是否需要控制协变量。
- 数据/变量：
  - 自变量：`age`、`sex`
  - 结果变量：依恋总分及分量表、攻击性总分及分量表、总精神病理、自伤总频率
- 方法：相关分析。
- 结果位置：
  - `Results > 3.1 Preliminary Analyses`，PDF 第 4-5 页
  - `Table 4`，PDF 第 5 页
- 关键结果：
  - 年龄更大者报告：
    - 更安全的依恋
    - 更低的攻击性
    - 更低的精神病理
  - 性别与大多数因变量不显著相关，唯一例外是 `anger`，男性更高。
  - 因此，后续主分析统一控制 `age`。
- 原文标注：
  - `A series of correlations were conducted to determine the potential influence of subject variables (i.e., age and sex) on the dependent variables.`
  - `people who were older reported more secure attachment, were less aggressive, and had less psychopathology.`
  - `Given these multiple associations, age was entered as a covariate in all main analyses...`
  - `There were no significant associations between sex and any of the dependent variables, with the exception of anger, with men more angry than women.`

## 分析 7：生活史策略与家庭结构的偏相关（Table 5）

- 目的：检验混合家庭结构是否如预测那样更对应于快速生活史策略。
- 数据/变量：
  - 生活史策略：`Mini-K`、`HKSS`
  - 家庭结构：`number of full biological siblings`、`number of half-siblings`、`number of step-siblings`、`presence of stepparent`
  - 协变量：`age`
- 方法：
  - 偏相关分析（controlling for age）
  - 多重比较采用 `Bonferroni correction`，显著性阈值 `p < .002`
- 结果位置：
  - `Results > 3.2.1 Life History Strategies and Family Structure`，PDF 第 5 页
  - `Table 5`，PDF 第 5 页
  - 讨论中的补充解释见 PDF 第 6 页
- 关键结果：
  - 严格 Bonferroni 校正后，无显著关联。
  - 但讨论中报告存在趋势：
    - `HKSS` 与 `number of half-siblings`：`pr = -.20, p = .02`
    - `Mini-K` 与 `presence of stepparent`：`pr = -.19, p = .03`
- 原文标注：
  - `There were no significant associations at p < .002.`
  - `The results from our analyses revealed an association between faster life strategies and numbers of half-siblings (pr = −.20, p = .02) and step-parents (pr = −.19, p = .03). Although these correlations were not significant given our Bonferroni correction...`

## 分析 8：生活史策略与精神病理、自伤总频率的偏相关（Table 5）

- 目的：检验更快的生活史策略是否与更多精神病理症状和更高自伤频率有关。
- 数据/变量：
  - 生活史策略：`Mini-K`、`HKSS`
  - 结果变量：`total psychopathology`、`total frequency of self-harm`
  - 协变量：`age`
- 方法：
  - 偏相关分析（controlling for age）
  - 使用 `Bonferroni correction`，阈值 `p < .002`
- 结果位置：
  - `Results > 3.2.2 Life History Strategies and Psychopathology`，PDF 第 5 页
  - `Table 5`，PDF 第 5 页
- 关键结果：
  - 更快生活史策略与更高总精神病理显著相关：
    - `Mini-K` 与 total psychopathology：`pr = -.51`
    - `HKSS` 与 total psychopathology：`pr = -.41`
  - 两个生活史指标与自伤总频率均不显著：
    - `Mini-K`：`pr = -.04`
    - `HKSS`：`pr = -.17`
- 原文标注：
  - `The results ... revealed significant associations between both life history measures and total psychopathology symptom frequency with faster life strategies associated with more symptoms of psychopathology.`
  - `Neither of the life history strategy measures was significantly correlated (p < .002) with frequency of self-harm behaviours.`

## 分析 9：性别是否调节生活史策略与自伤之间的关系

- 目的：检验论文预注册式预测中的性别差异，即生活史策略与自伤的关系是否因性别而异。
- 数据/变量：
  - 预测变量：生活史策略指标
  - 结果变量：自伤
  - 调节变量：`sex`
  - 协变量：`age`
- 方法：
  - 调节分析（moderation analysis）
  - 按 `Hayes (2013)` 的程序进行
- 结果位置：`Results > 3.2.2 Life History Strategies and Psychopathology`，PDF 第 5 页。
- 关键结果：
  - 未发现性别主效应
  - 未发现 `sex × life history strategy` 交互作用
- 原文标注：
  - `a series of moderation analyses were conducted using procedures outlined in Hayes (2013), with sex as the moderating variable, and age entered as a covariate.`
  - `The results did not confirm any main effects for sex or any significant sex by life history strategy interactions.`

## 分析 10：生活史策略与依恋的偏相关（Table 5）

- 目的：检验更快的生活史策略是否与更差的父母/照顾者响应性感知相关。
- 数据/变量：
  - 生活史策略：`Mini-K`、`HKSS`
  - Attachment 指标：
    - `Total attachment`
    - `Availability`
    - `Angry distress`
    - `Goal-corrected partnership`
  - 协变量：`age`
- 方法：
  - 偏相关分析（controlling for age）
  - 使用 `Bonferroni correction`，阈值 `p < .002`
- 结果位置：
  - `Results > 3.2.3 Life History Strategies and Attachment`，PDF 第 5 页
  - `Table 5`，PDF 第 5 页
- 关键结果：
  - 两个生活史指标与所有 attachment 指标均显著相关。
  - 例如：
    - `Mini-K` 与 total attachment：`pr = -.42`
    - `HKSS` 与 total attachment：`pr = -.41`
    - `Mini-K` 与 angry distress：`pr = -.44`
    - `HKSS` 与 angry distress：`pr = -.44`
- 解释口径：
  - 因为较高的 `Mini-K/HKSS` 代表更慢生活史，因此负相关意味着更快生活史与更差依恋相关。
- 原文标注：
  - `there were significant correlations between both life history strategy measures and all subscales of parental attachment.`
  - `People who reported less empathy toward their caregivers ... perceived that their caregivers were less responsive ... and reported greater anger within the attachment relationship ... also indicated engaging in a faster life strategy.`

## 分析 11：在控制年龄和兄弟姐妹数量后，依恋是否独立预测生活史策略（Table 6）

- 目的：检验 perceived parental support/attachment 是否能在家庭规模变量之外独立预测生活史策略。
- 数据/变量：
  - 因变量 1：`Mini-K`
  - 因变量 2：`HKSS`
  - 主要预测变量：`Total attachment`
  - 协变量：
    - `age`
    - `half-siblings`
    - `step-siblings`
    - `biological siblings`
- 方法：
  - 分别进行两次多元线性回归
  - 回归 1：`Mini-K ~ age + half-siblings + step-siblings + biological siblings + total attachment`
  - 回归 2：`HKSS ~ age + half-siblings + step-siblings + biological siblings + total attachment`
- 结果位置：
  - `Results > 3.2.3 Life History Strategies and Attachment`，PDF 第 5 页
  - `Table 6`，PDF 第 6 页
- 关键结果：
  - 对 `Mini-K`：
    - `Total attachment: b = -0.60, beta = -.41, t = -5.20, 95% CI [-0.83, -0.37]`
    - `R^2 = .28`
    - `F(5,132) = 10.49, p < .001`
  - 对 `HKSS`：
    - `Total attachment: b = -0.67, beta = -.37, t = -4.68, 95% CI [-0.95, -0.38]`
    - `R^2 = .26`
    - `F(5,132) = 9.09, p < .001`
  - 结论：依恋在控制年龄和兄弟姐妹数量后，仍显著预测生活史策略。
- 原文标注：
  - `two regressions were conducted – one with each life strategy measure.`
  - `The result from these analyses ... revealed that perceived parental support was a significant predictor of life history strategy, independent of numbers of siblings.`

## 分析 12：生活史策略与攻击性的偏相关（Table 5）

- 目的：检验更快的生活史策略是否与更高攻击性相关。
- 数据/变量：
  - 生活史策略：`Mini-K`、`HKSS`
  - 攻击性指标：
    - `Total aggression`
    - `Physical aggression`
    - `Verbal aggression`
    - `Anger`
    - `Hostility`
  - 协变量：`age`
- 方法：
  - 偏相关分析（controlling for age）
  - 使用 `Bonferroni correction`，阈值 `p < .002`
- 结果位置：
  - `Results > 3.2.4 Life History Strategies and Aggression`，PDF 第 5-6 页
  - `Table 5`，PDF 第 5 页
- 关键结果：
  - 显著相关：
    - `Mini-K` 与 total aggression：`pr = -.46`
    - `HKSS` 与 total aggression：`pr = -.43`
    - `Mini-K` 与 physical aggression：`pr = -.44`
    - `HKSS` 与 physical aggression：`pr = -.34`
    - `Mini-K` 与 anger：`pr = -.31`
    - `HKSS` 与 anger：`pr = -.25`
    - `Mini-K` 与 hostility：`pr = -.52`
    - `HKSS` 与 hostility：`pr = -.52`
  - 不显著：
    - `Mini-K` 与 verbal aggression：`pr = -.03`
    - `HKSS` 与 verbal aggression：`pr = -.10`
- 原文标注：
  - `there were significant associations for both measures of life history strategy and all components of aggression except verbal aggression.`
  - `People with fast life strategies reported more physical aggression, anger, hostility, and overall aggression.`

## 分析 13：性别是否调节生活史策略与攻击性的关系

- 目的：检验生活史策略与攻击性的关系是否因性别而异。
- 数据/变量：
  - 预测变量：生活史策略指标
  - 结果变量：攻击性
  - 调节变量：`sex`
  - 协变量：`age`
- 方法：
  - 调节分析（moderation analysis）
  - 按 `Hayes (2013)` 的程序进行
- 结果位置：`Results > 3.2.4 Life History Strategies and Aggression`，PDF 第 5-6 页。
- 关键结果：
  - 未支持性别调节效应。
  - 生活史策略本身仍是攻击性的显著预测变量。
- 原文标注：
  - `a series of moderation analyses were conducted using procedures outlined in Hayes (2013), with sex as the moderating variable, and age entered as a covariate.`
  - `None of the results from this series of analyses supported a moderating effect of sex with life history strategy remaining a significant predictor of aggression.`

## 分析 14：Bonferroni 多重比较校正

- 目的：控制主分析中多次偏相关带来的 I 类错误。
- 数据/变量：适用于主分析中的多组偏相关。
- 方法：
  - `Bonferroni correction`
  - `p < .002`，作者给出的换算为 `.05 / 30 = .001666`
- 结果位置：`Results > 3.2 Main Analyses`，PDF 第 5 页。
- 备注：
  - 这不是单独的实证分析结果，但它是复现时必须忠实实现的统计决策。
- 原文标注：
  - `Given the multiple partial correlation analyses that were conducted as part of the main analyses, we used Bonferroni corrections to protect from type I error...`
  - `statistical significance was set at p < .002 (i.e., .05/30 = .001666).`

## 后续复现时建议的执行顺序

1. 先复现样本筛选和描述性统计。
2. 再复现 Table 1 的量表求分、均值、标准差、Cronbach's alpha。
3. 复现 `Mini-K` 与 `HKSS` 的相关。
4. 复现 Table 2 与 Table 3 的频数/阈值统计。
5. 复现 Table 4 的预分析相关。
6. 复现 Table 5 的全部偏相关，并同步应用 Bonferroni 校正。
7. 复现 Table 6 的两组回归。
8. 最后复现两组调节分析。

## 当前结论

若以后按“主文中的每一个分析”来复现，这篇论文至少包含上面 14 个需要单独核对的统计步骤/统计块。其中真正的核心假设检验集中在分析 7-13，但为了严格复现，分析 1-6 和分析 14 也不能省略。
