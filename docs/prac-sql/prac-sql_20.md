# 第二十章：讲述你的数据故事

![](img/chapterart.png)

学习 SQL 本身就可以很有趣，但它有更重要的意义：它帮助你挖掘数据中的故事。正如你所学到的，SQL 为你提供了找到数据中有趣的趋势、洞察或异常的工具，并基于这些发现做出明智的决策。但你如何从仅仅是一堆行和列的数据中识别出这些趋势呢？在识别出这些趋势后，你又该如何从中提取有意义的洞察？

在本章中，我将概述我作为记者和产品开发人员用来发现数据中故事并传达我的发现的过程。我将从如何通过提问和收集、探索数据来生成创意开始。然后，我会解释分析过程，最终是清晰地呈现你的发现。识别数据集中的趋势并将你的发现形成叙述，有时需要相当多的实验和足够的毅力来应对偶尔的死胡同。把这些建议当作指南，而不是检查清单，帮助确保一个全面的分析，最大程度减少错误。

## 从一个问题开始

好奇心、直觉，或有时仅仅是运气，往往能激发数据分析的灵感。如果你是一个细心的观察者，你可能会注意到社区随着时间的变化，并想知道是否能衡量这些变化。考虑一下你当地的房地产市场。如果你看到“待售”标志比平时更多地出现在镇上，你可能会开始提出问题。今年与去年相比，房屋销售是否大幅增加？如果是，增加了多少？哪些社区正在受益于这一波变化？这些问题为数据分析提供了一个很好的机会。如果你是记者，你可能会发现一个故事。如果你经营一家企业，你可能会看到一个营销机会。

同样地，如果你推测你的行业中出现了某种趋势，确认这一点可能会为你提供商业机会。例如，如果你怀疑某个产品的销量不景气，你可以分析数据来验证这个猜测，并适当调整库存或营销策略。

记录这些创意并根据其潜在价值进行优先排序。为了满足好奇心进行数据分析是完全可以的，但如果这些答案能让你的机构更高效或让你的公司更有利润，那就意味着它们值得追求。

## 记录你的过程

在进行分析之前，考虑如何使你的过程透明且可重复。为了保证可信度，组织内外的其他人都应该能够复制你的工作。此外，确保你记录下足够的过程细节，这样如果你将项目搁置几个星期，回来时你也不会遇到困难。

记录工作并没有一种唯一正确的方法。记录研究笔记或创建逐步的 SQL 查询，让其他人可以跟随这些步骤复制你的数据导入、清理和分析过程，可以让别人更容易验证你的发现。有些分析师将笔记和代码存储在文本文件中，另一些则使用版本控制系统，如 GitHub，或在代码笔记本中工作。重要的是你要创建一个文档管理系统，并始终如一地使用它。

## 收集你的数据

在你想出一个分析思路之后，下一步是找到与趋势或问题相关的数据。如果你在一个已经有相关数据的组织工作，那就太幸运了——你可以直接使用现成的数据！在这种情况下，你可能能够访问内部的市场营销或销售数据库、客户关系管理（CRM）系统，或订阅者或活动注册数据。但如果你的话题涉及更广泛的领域，如人口统计、经济学或行业特定的问题，你就需要做一些深入的挖掘。

一个好的起点是询问专家他们使用的数据来源。分析师、政府决策者和学者可以为你指明可用的数据来源，并描述其有用性。正如你在本书中看到的那样，联邦、州和地方政府会生产大量关于各种主题的数据。在美国，你可以查看联邦政府的数据目录网站 [`www.data.gov/`](https://www.data.gov/) 或各个联邦机构的网站，如国家教育统计中心（NCES） [`nces.ed.gov/`](https://nces.ed.gov/) 或劳工统计局 [`www.bls.gov/`](https://www.bls.gov/)。

你还可以浏览当地政府网站。每当你看到一个让用户填写的表单或一个按行和列格式化的报告时，这通常是结构化数据可能可以用于分析的信号。如果你只能访问非结构化数据，别灰心——正如你在第十四章学到的，你甚至可以挖掘非结构化数据，如文本文件，进行分析。

如果你想分析的数据是多年来收集的，我建议你尽量分析五年、十年甚至更长时间的数据，而不仅仅是分析一两年的数据。分析一个月或一年的数据快照可能会得到有趣的结果，但许多趋势是在更长的时间段内展现的，如果你只看一年数据，可能看不到这些趋势。我将在“识别关键指标和趋势”一节中进一步讨论这个问题。

## 没有数据？建立自己的数据库

有时，没有人能提供你需要的格式的数据。如果你有时间、耐心和方法论，你可能能够建立自己的数据集。这就是我和我的*今日美国*同事罗伯特·戴维斯所做的，当时我们想研究与美国大学校园中学生死亡相关的问题。没有任何一个组织——无论是学校、州政府还是联邦政府——能够告诉我们每年有多少大学生在校园内因事故、药物过量或疾病死亡。我们决定收集自己的数据，并将信息结构化为数据库中的表格。

我们从研究与学生死亡相关的新闻文章、警察报告和诉讼开始。找到 2000 年至 2005 年间 600 多起学生死亡的报告后，我们进一步采访了教育专家、警察、学校官员和家长。从每个报告中，我们记录了每个学生的年龄、学校、死亡原因、年级以及是否与毒品或酒精有关。我们的发现最终促成了 2006 年在*今日美国*刊登的文章《在大学，第一年是最危险的》。该报道展示了我们 SQL 数据库分析的关键发现：大一新生尤为脆弱，占据了我们研究的学生死亡事件中最高的比例。

如果你缺乏所需的数据，你也可以创建一个数据库。关键是要识别出重要的信息，并系统地收集它们。

## 评估数据的来源

在你确定了一个数据集之后，尽可能多地了解其来源和维护方法。政府和机构以各种方式收集数据，而有些方法产生的数据比其他方法更具可信度和标准化。

例如，你已经看到，美国农业部（USDA）食品生产商的数据中同一公司名称有多种拼写方式。了解原因是值得的。（可能数据是手动从书面表格转录到计算机的。）类似地，你在第十二章分析的纽约市出租车数据记录了每次行程的开始和结束时间。这引发了一个问题，计时器什么时候开始和停止——是乘客上下车时，还是有其他触发条件？你应该了解这些细节，不仅为了从分析中得出更好的结论，还要将这些信息传递给可能解读你分析的其他人。

数据集的来源也可能影响你如何分析数据和报告你的发现。例如，对于美国人口普查局的数据，重要的是要知道每十年进行一次的普查是对人口的完整统计，而美国社区调查（ACS）仅基于部分家庭样本。因此，ACS 的数据存在误差范围，而十年一次的普查则没有。若不考虑误差范围的影响，报告 ACS 数据是不负责任的，因为误差范围可能使得数字之间的差异变得微不足道。

## 用查询采访数据

一旦你获得了数据，了解它的来源，并将其加载到数据库中，你就可以通过查询来探索数据。在本书中，我称这个步骤为*采访数据*，这是你应该做的事情，以了解数据的内容，并查看其中是否存在任何警示信号。

一个好的起点是聚合数据。计数、求和、按列值排序和分组应该能揭示最小值和最大值、可能存在的重复条目问题，以及数据的整体范围。如果你的数据库包含多个相关表格，尝试使用连接查询以确保你理解这些表格之间的关系。使用`LEFT JOIN`和`RIGHT JOIN`，正如你在第七章学到的那样，可以查看一个表中的关键值是否在另一个表中缺失。这可能会引起或不引起关注，但至少你能够识别潜在的问题并着手解决。列出你所有的问题或关注点，然后继续下一步。

## 咨询数据的所有者

在探索了你的数据库并形成了关于观察到的数据质量和趋势的初步结论之后，花时间向了解数据的人提出问题或关注点。这个人可能是为你提供数据的政府机构或公司的工作人员，或者是之前曾处理过这些数据的分析师。这一步是你澄清对数据的理解、验证初步发现并发现数据是否存在任何问题，进而判断其是否适合你的需求的机会。

例如，如果你在查询一个表格时，发现某些列中的值似乎是明显的异常值（比如，本应发生在过去的事件却出现了未来的日期），你应该询问这个不一致的情况。如果你期望在表格中找到某个人的名字（也许是你自己的名字），但却没有找到，这也应该引发另一个问题。是不是可能你没有获得完整的数据集，或者数据收集存在问题？

目标是获得专家的帮助，以完成以下工作：

1.  了解数据的限制。确保你知道数据包含了什么，排除了什么，以及可能影响你分析方式的内容提示。

1.  确保你拥有完整的数据集。核实你是否拥有应该看到的所有记录，并且如果有数据缺失，你了解其原因。

1.  确定数据集是否符合你的需求。如果数据源承认数据质量存在问题，考虑寻找其他地方的数据以获得更可靠的来源。

每个数据集和情况都是独特的，但咨询其他用户或数据所有者可以帮助你避免不必要的失误。

## 确定关键指标和随时间变化的趋势

当你确认自己理解数据，并且对数据的可信度、完整性以及其对分析的适用性充满信心时，下一步就是运行查询，识别关键指标，并在可能的情况下，观察随时间变化的趋势。

你的目标是挖掘出可以用一句话总结的数据，或者可以作为演示文稿中的幻灯片展示的内容。一个发现的例子可能是这样的：“经过五年的下降后，Widget 大学的注册人数在连续两个学期内增长了 5%。”

要识别这种趋势，你将遵循一个两步过程：

1.  选择一个指标进行跟踪。在普查数据中，它可能是超过 60 岁的人口比例；或者在纽约市出租车数据中，它可能是一年中每周工作日的平均出行次数。

1.  跟踪这个指标多个年份，看看它是否有变化。

实际上，这些是我们在第七章中用来将百分比变化计算应用于多个年份的普查数据的步骤。在那种情况下，我们查看了 2010 年到 2019 年间各县人口的变化。人口估算是关键指标，而百分比变化展示了每个县在九年期间的趋势。

关于衡量时间变化的一个警告：即使你在任何两个年份之间看到剧烈的变化，仍然值得尽可能深入挖掘更多年份的数据，以便在长期趋势的背景下理解短期变化。任何年度变化可能看起来很剧烈，但将其放在多年活动的背景下可以帮助你评估其真正的重要性。

例如，美国国家健康统计中心每年发布出生人数数据。作为一个数据迷，这是我喜欢关注的指标之一，因为出生人数往往反映了文化或经济的广泛趋势。图 20-1 展示了 1910 年至 2020 年间每年的出生人数。

![f20001](img/f20001.png)

图 20-1：1910 年到 2020 年的美国出生人数。来源：美国国家健康统计中心

只看这个图表的最后五年（灰色部分），我们看到出生人数稳步下降，从 2016 年的 395 万人降至 2020 年的 361 万人。近期的下降确实值得注意（反映了出生率持续下降和人口老龄化）。但从长期背景来看，我们可以看到国家在过去 100 年里经历了几次婴儿潮和婴儿潮破裂。你可以在图 20-1 中看到的一个例子是第二次世界大战后，1940 年代中期出生人数的急剧上升，标志着婴儿潮一代的开始。

通过识别关键指标并观察短期和长期的变化，你可能会发现一个或多个值得呈现给他人或采取行动的发现。

## 问问为什么

数据分析可以告诉你发生了什么，但它并不总是能说明为什么会发生某事。要了解*为什么*，值得与相关领域的专家或数据所有者一起重新审视数据。在美国出生数据中，我们可以轻松计算出每年的百分比变化。但这些数据并没有告诉我们，为什么从 1980 年代初到 1990 年，出生人数持续增加。要了解这一信息，你可以咨询一位人口学家，他很可能会解释，在这些年里，出生人数的增加恰好与更多的婴儿潮一代进入生育年龄相吻合。

在与你的专家分享发现和方法时，要求他们注意任何看起来不太可能或值得进一步探讨的内容。对于他们能够证实的发现，要求他们帮助你理解背后的原因。如果他们愿意被引用，你可以使用他们的评论来补充你的报告或演示文稿。以这种方式引用专家对趋势的见解是记者常用的标准方法。

## 传达你的发现

你如何分享分析结果取决于你的角色。学生可能会通过论文或学位论文来展示他们的结果。在企业环境中工作的人可能会使用 PowerPoint、Keynote 或 Google Slides 来呈现他们的发现。记者可能会撰写故事或制作数据可视化。不管最终产品是什么，以下是展示信息的建议，以一个虚构的住宅销售分析为例：

1.  根据你的发现确定一个总体主题。将主题作为你的演讲、论文或可视化的标题。例如，你可能会将有关房地产的演示命名为“郊区住宅销售上升，城市下降”。

1.  展示总体数字以显示大体趋势。突出你的分析中的关键发现。例如，“所有郊区社区在过去两年中每年销售增长了 5%，扭转了三年的下降趋势。与此同时，城市社区的销售下降了 2%。”

1.  强调支持这一趋势的具体例子。描述一两个相关的案例。例如，“在史密斯镇，住宅销售在 XYZ 公司总部搬迁后增长了 15%。”

1.  承认与整体趋势相反的例子。这里也可以使用一两个相关的案例。例如，“两个城市的社区确实出现了住宅销售增长：Arvis（增长 4.5%）和 Zuma（增长 3%）。”

1.  坚持事实。永远不要歪曲或夸大任何发现。

1.  提供专家见解。使用引用或引文。

1.  **使用条形图、折线图或地图可视化数字。** 表格有助于为观众提供具体数字，但通过可视化更容易理解趋势。

1.  **引用数据的来源及其分析包含或省略的内容。** 提供涵盖的日期、提供者的名称以及任何影响分析的区分，例如：“基于沃尔顿县 2022 年和 2023 年的税务申报数据。排除商业地产。”

1.  分享你的数据。将数据发布到网上供下载，并附上你分析过程中所采取步骤的描述。没有什么比与他人分享数据更能体现透明度了，这样他们可以进行自己的分析并验证你的发现。

通常，一个简短的报告能够清晰简洁地传达你的发现，并邀请听众进行对话，效果最佳。当然，你可以遵循自己偏好的数据工作和展示结论的方式。但多年来，这些步骤帮助我避免了数据错误和错误假设。

## 总结

最后，你已经完成了我们对 SQL 的实用探索！感谢你阅读本书，欢迎通过电子邮件向我提出建议和反馈：[practicalsqlbook@gmail.com](http://mailto:practicalsqlbook@gmail.com)。本书末尾有一个附录，列出了你可能想尝试的其他 PostgreSQL 相关工具。

我希望你已经掌握了数据分析技能，能够立即应用到你日常遇到的数据中。更重要的是，我希望你已经看到每个数据集都有一个故事，或者多个故事可以讲述。识别并讲述这些故事是与数据工作值得的原因；它不仅仅是翻看一堆行和列。我期待听到你所发现的内容！
