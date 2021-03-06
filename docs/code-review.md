## Code Review 
### 背景与目的

在极限编程中，结对编程（Pair Programming）是非常重要的实践，但在业界仍然很少采用结对编程，原因之一是好处不是立竿见影，只能在中期和长期中会获得更多的回报，多数公司并不愿意采用该实践。 Code Review 则是结对编程的一种补充，建议每天下班前开发团队所有成员进行1小时内的 Code Review，它有如下好处：

* Code Review 可以帮助团队统一编码风格，达成共识。

* 代码质量不是某个人的责任，团队的每一个人都是负责人。

* 通过代码 Code Review 进行业务、技术知识分享，避免知识孤岛。

* Code Review 是保证质量的规则和实践，持续改善才能解决代码质量差的问题。

* 想要写出优雅的代码，是需要学习和练习的。Code Review就是最好的学习平台。



### 提交信息规范

提交格式：[系统变更号]标识:commit message

例子：[YJFZX-1938]feat:新增用户规范

标识

| build    | 影响构建系统或外部依赖关系的更改（示例范围：pom，npm） |
| -------- | ------------------------------------------------------ |
| ci       | 更改我们的持续集成文件和脚本（示例范围：Jenkins）      |
| docs     | 仅文档更改                                             |
| feat     | 一个新功能                                             |
| fix      | 修复错误                                               |
| perf     | 改进性能的代码更改                                     |
| refactor | 代码更改，既不修复错误也不添加功能                     |
| style    | 不影响代码含义的变化（空白，格式化，缺少分号等）       |
| test     | 添加缺失测试或更正现有测试                             |

 参考[karma 这里](https://karma-runner.github.io/6.2/dev/git-commit-msg.html)。

### 小步提交规范

**（一）** **每次提交只做一件事**

需要将手头上较大的需求/任务进行拆分，拆分成多个可独立完成的小任务。每个小任务必须能够在0.5天-1天可以做完。每次提交代码量尽量控制在100行内。

**（二）** **使用工具自动重构，重构单独提交**

做重构时，需要和新增/修复功能分开。最好使用IDE自带的重构工具进行安全重构，减少手工去修改。如：抽取方法，修改名称等。



### Code Review 原则

代码规范是绝对权威。出现与规范相违背或不在规范指南中的风格，需要与团队达成一致并修订代码规范。

### Code Review 范围

- 代码逻辑正确性
- 满足编码规范
- 代码风格统一性（注释，命名，提交规范）
- 代码可读性
- 异常和日志处理
- 单元测试有效性
- 代码分层合理性（分层职责是否清晰）
- 好的实践分享

### Code Review 方式

**参与者**：整个开发团队（如果参与评审人员超过7人，可按技术栈或业务进行分组）

**评审时机**：建议每日一次，下班前进行（代码量少的团队可适当调整，至少每周3次）

**评审时长**：控制在60分钟以内

**评审流程**：

1. 检查上次Code Review记录的改进点是否已经修复，更新记录表；

2. 代码作者简要介绍评审代码的业务上下文和代码设计思路；

3. 展示 Sonar 扫描结果及流水线状态（可选，也可增加评审单元测试）；

4. 作者展示所修改的代码，参与者提问，作者答疑；

5. 作者记录改进点； 

**评审结果**：

代码改进项记录任务卡贴在看板中，下次 Code Review 前修复。

 

 

## 背后的“思考”

 

### 为什么要全员参加？

1. Code Review 是知识传播的过程，避免对特定模块/特定人员单点依赖。**注意：Code Review 只是实践的一部分，还需要 Switch Pair （即：定期轮换人员与功能模块）避免一个人只熟悉做一个功能模块。**

2. 不是有经验的程序员去单纯评审大家的代码，需要不停地提出和解决问题。让新人从讨论中学习到解决问题的思路和技术要点。

3. Code Review 是培养新人的最直接和最有效的途径，对已有代码的讨论，即实例化，又能直接提升质量。

   

### 频率和时长如何取舍？

1. 最佳实践建议每天都做 Code Review。如果大家时间很难协调，也要保证每周三次。

2. 时长根据团队大小决定：如果小团队（2~3人），半小时就足够。如果团队人员较多，不要超过1小时为宜。如果超过1小时，精力会下降，反而会适得其反。

   

### 改进点为什么要及时完成？

1. 如果只是记录改进点，并不做任何改进，Code Review 也没有了价值。

2. 改进点只是对当前两次评审之间的代码做改动，工作量可以保证在合理的范围之内，若不及时，很可能会变成巨大的工程。

3. 及时完成也是每个人执行力的体现，没有执行力，何谈质量内建。

 