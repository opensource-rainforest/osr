# 开源使用规范及业界优秀实践

## 第一节 - Google 和 Oracle 的世纪诉讼

旷日持久的 Java 版权大战：谷歌有限责任公司诉甲骨文美国公司案（Google LLC v. Oracle America, Inc.），593 U.S. (2021)，于 2021 年 4 月 5 日以 Google 的胜利告终。这起持续了 10 余年，跨越了三个审判和两个独立上诉的以计算机代码性质为焦点的著作权法案件引发业界热议，对于科技和软件行业具有重大意义。

该案的诉争对象是 Java 编程语言的部分应用程序接口（简称 API ）以及大约 11,000 行源代码。这些代码最早由 Sun Microsystems 开发，在 Sun 被甲骨文公司收购后，甲骨文公司通过其附属的甲骨文美国公司对其享有著作权。Google 在其开发的 Android 操作系统早期版本中使用了上述接口及代码，但在后来发布的 Android 版本中没有继续使用上述有甲骨文及其公司享有著作权的源代码。对于 Oracle 的 API ，Google 虽承认存在使用行为，但主张其构成合理使用。

> 最高法院 Alsup 法官在第二次上诉裁决中引用了最高法院案件 *Campbell v. Acuff-Rose Music, Inc.510 U.S.569(1994)*，并指出：
>
>*Truth, in literature, in science and in art, there are, and can be, few, if any, things, which in an abstract sense, are strictly new and original throughout. Every book in literature, science and art, borrows, and must necessarily borrow, and use much which was well known and used before [2]*

1. **使用的目的、性质和合理使用** [4]

*它（目标代码）是否具有“变革性”以及在多大程度上具有“变革性”—— Campbell v. Acuff-Rose Music, Inc. 510 U.S. 569 (1994)*

> 法官认为谷歌的 API 是一种“创新”，它使得开发人员只需要很少的命令就能调用预先写好的代码。这里面有谷歌创造性的劳动在里面。

版权所有者不得阻止他人“合理使用 (fair use)”受版权保护的作品合理使用的目的是鼓励创新。

来看下美国版权法对“合理使用“的定义：**[Copyright Law of the United States](https://link.zhihu.com/?target=https://www.copyright.gov/title17/)**

> **107. Limitations on exclusive rights: Fair use**
>
> Notwithstanding the provisions of sections [106](https://link.zhihu.com/?target=https://www.copyright.gov/title17/92chap1.html#106) and [106A](https://link.zhihu.com/?target=https://www.copyright.gov/title17/92chap1.html#106a), the fair use of a copyrighted work, including such use by reproduction in copies or phonorecords or by any other means specified by that section, for purposes such as criticism, comment, news reporting, teaching (including multiple copies for classroom use), scholarship, or research, is not an infringement of copyright. In determining whether the use made of a work in any particular case is a fair use the factors to be considered shall include—
> (1) the purpose and character of the use, including whether such use is of a commercial nature or is for nonprofit educational purposes;
> (2) the nature of the copyrighted work;
> (3) the amount and substantiality of the portion used in relation to the copyrighted work as a whole; and
> (4) the effect of the use upon the potential market for or value of the copyrighted work.
> The fact that a work is unpublished shall not itself bar a finding of fair use if such finding is made upon consideration of all the above factors. 如何判断合理使用呢？有两种情况：

1、6种通常场景：批评，评论，新闻报道，教学（包括多份供课堂使用），奖学金或研究报告，并不构成对版权的侵犯

2、当不在6种场景以外时，考虑以下4个维度：

（1）使用目的和性质，包括该使用是商业性质还是非 营利性教育目的；

（2）受版权保护的作品的性质；

（3）与整个受版权保护作品有关的部分的数量和实质性；

（4）使用对版权作品潜在市场或价值的影响。再看谷歌案，最高法院法官的判例如下：

（1）使用的目的和性质

1. **受版权保护的作品的性质**

   计算机程序与其他受版权保护的作品是不同的，因为它总是服务于功能性目的，合理使用对计算机程序而言是非常重要的。需要进行上下文判断，而不是断章取义（仅有片段信息是不充分的）。

   同时版权保护不能延伸到“任何想法、程序(procedure)、过程(process)、系统、操作方法、原则和发现…”。

2. **与整个受版权保护作品有关的部分的数量和实质性**

   法官认为复制的数量只占整个 API 的 0.4%，而就是因为这 0.4% 使得开发者可以帮助程序员在智能手机场景下进行“变革性”的创造。再次牵涉到“变革性”的权衡，引用判例的话说就是*新作品的变革性越强，可能不利于合理使用的发现的其他因素（例如商业主义）的意义就越小。—— Campbell v. Acuff-Rose Music, Inc. 510 U.S. 569 (1994)*

3. **使用对版权作品潜在市场或价值的影响**

   法官认为 Oracle 的代码的市场和谷歌的安卓代码存在很大差异，一个是桌面端的 一个是移动端的，两者在各自领域并不存在事实的冲突和竞争关系。

   

**最终，最高法院认为谷歌的 API 代码相比甲骨文的 Java 代码具有“变革性”，为鼓励创新，不应算作侵犯版权，判决 Google 对 Java API 的使用属于合理使用，谷歌胜诉。**

*“Google 对于实现用户界面* *API* *的复制，仅采用了允许用户将其应有的才能投入新的，变革性程序中所需的一切，这就构成了对该材料的合理使用。”[3]*

像 Google 与 Sun 在 Java 语言上的关系，以及开源软件、API 的内容借鉴在科技领域内并不少见。如何依托于可信的开源软件供应链思想规范使用开源，对开源软件进行端到端的流程管理，结合上一节讲到的网络安全风险、法规风险、生命周期的风险，这一节将从**选择开源软件、使用开源软件、维护开源软件的生命周期、回馈开源社区**四个方面进行阐述。



#### **1.1** **开源项目使用的主要方式**

目前企业使用开源的场景主要有两种方式：

1. **基于开源软件进行开发** 

   很多企业在开源软件的基础上进行开发，在合规的基础上构筑自己的商业产品。譬如国内的云厂商绝大部分都有基于 CNCF 基金会下的开源项目 Kubernetes 构建容器相关的云产品，同时研发了很多开源或者闭源的插件、Operator 来满足不同客户的诉求，使得这些云厂商的相同类型产品之间产生了差异性，针对不同的客户和场景形成竞争力差异。但是使用 Kubernetes 的过程中，需要持续的跟进 Kubernetes 版本的变化，也消耗了大量的精力。所以这种情况下，各个云厂商将自己开发的特性开源贡献到上游，避免和上游社区形成不同的维护分支。

2. **调用开源软件的进程** 

   有一些企业开发的代码是在运行时调用其它开源项目的代码或者进程。譬如使用 Nextjs 开发页面应用的时候，会大量集成 JavaScript 的库；一些在 Linux 下开发的程序会调用 OpenSSL 的 MD5 库计算哈希值进行一些校验工作。

不管是那种场景都存在“使用的代码版本老旧、编写软件时进行开源代码片段引用”等现象以及由此带来的“网络安全、合法合规、可追溯性差”等开源合规、开源治理方面的问题。本节内容将从软件开发和维护的不同阶段对使用开源进行约束，并提出规则、建议、标准和对工具的要求。

为确保满足网络安全、合法合规、可追溯性要求，从产品研发角度规范产品开发团队合理使用开源软件代码，指导产品正确使用开源软件。

1. **无开源代码片段引用问题**

   案例：Google 凭什么要赔给 Oracle 88 亿？

   https://cloud.tencent.com/developer/article/1169428

2. **GPL 感染被动开源情况**

   案例：违反 GPL 协议赔偿 50 万，国内首例！

   https://www.163.com/dy/article/GJQ7HP3G0511FQO9.html

3. **开源使用声明及履行对外开源义务合规，无法务风险**

   案例：国产红芯号称自主研发浏览器核心 结果是 Chrome 换皮 

   https://tech.sina.com.cn/n/k/2018-08-16/doc-ihhvciiv6109112.shtml

4. **满足开源软件网络安全管理要求**

   案例：紧急！ Log4j 漏洞风险，堪比“永恒之蓝”或将影响 70% 以上企业 

   https://www.leiphone.com/category/gbsecurity/5D1Aq04tyjCDMill.html

在产品开发的每个阶段、不同方式使用开源都会带来各种问题和风险，需要我们关注和控制。

| 类别       | 选型     | 集成     | 架构与设计                                           | 开发                             | 维护                          |
| ---------- | -------- | -------- | ---------------------------------------------------- | -------------------------------- | ----------------------------- |
| 现象       | 版本老旧 | 协议遵从 | 没有充分利用扩展机制                                 | 片段引用、对开源原生代码进行修改 | 社区安全补丁缺乏跟踪 版本老旧 |
| 带来的问题 | 网络安全 | 合法合规 | 开源原生代码 不必要的修改带来的 网络安全、可追溯性差 | 网络安全、合法合规、可追溯性差   | 网络安全                      |



## 第二节 - 开源选型规则实践

#### 2.1 面向个人或家庭消费者的软件产品，使用 GPL v3 License 的开源软件会带来巨大风险。其它类型的软件产品需要仔细评估风险，同时在软件采购或合作开发时限制供应商或合作方引入该类型的 License 的开源软件

**案例：Ruby用实际行动向 GPL v3 吐槽，Ruby 1.9.3 将改用 BSD 许可证发布**

早期 Ruby 采用的是自由软件基金会推荐的 GPLv2 or later 许可证方式，这种许可证方式包含两层意思：[5]

- *软件本身以 GPLv2 许可证发布*

- *当自由软件基金会修订 GPL 并发布新版 GPL 时，授权一方同意授权人以新的 GPL 条款来发布软件 (\*)* 

由于 GPL v3 中增加了包含对硬件和软件专利等问题的一系列限制自由的条款（违反第 6 条），GPL v2 only 的代码和 GPL v3 许可证的代码不能一起重新分发。此外，自由软件基金会认为 Ruby License 是非自由软件许可证，根据 GPL v3 第 10 条的内容，GPL v3 许可证的软件不能与 Ruby 以 Ruby License 联合编译。

也就是说，Ruby 只能以两种许可证之一发布，发布联编的可执行文件要么违反 GPL v2，要么违反 GPL  v3，因此再发布的结果只能以源代码的形式提供，而不允许再发布其二进制文件。又因自由软件基金会从 6.0 版开始，将 readline 库改为 GPLv3 or later，这样一来，GPL v2 only 的 Ruby 便不能发布联合编译 readline 的可执行文件了。2020 年 9 月，Ruby Changeset r29262 将 Ruby 中的 GPLv2 许可证完全删除，改换为基于 FreeBSD 许可证的 2-clause BSD 许可证。[5]

- 个人或家庭消费者用户的产品在引入开源软件的阶段进行 License 校验，禁选 GPL V3 协议的开源软件。

| 场景             | 管控策略                                                     |
| ---------------- | ------------------------------------------------------------ |
| 采购场景         | 在采购协议中增加条款，禁止或限制供应商引入使用 GPL v3 类开源软件 |
| 开源软件中央仓库 | 在入库流程预审环节中增加 GPL v3 类自检 check 项，提前知会产品风险，若产品要引入 GPL v3 类软件，但无法满足 GPL v3 要求，则建议不予引入 |
| 评选等级         | 在开源软件中央仓库中，GPL v3 类软件优选等级设定较低，根据风险评估尽量限制产品选用 |
| 使用申请         | 申请使用 GPL v3 类软件，必须结合使用场景分析 License 风险，根据风险向管理决策者提出申请后使用，同时 GPL v3 类软件评审环节需要律师参与 |

#### 2.2 选择开源软件必须通过开源软件的基础安全评估

在选择开源软件，对开源软件进行评估时，必须进行基础安全的评估，根据评估结果确定是否选择。“心脏滴血”漏洞事件就是最好的例证。出现“心脏滴血”漏洞之后，OpenSSL 社区建立了完善的漏洞维护记录，挽回了其在商业领域的信誉 https://www.openssl.org/news/vulnerabilities.html

近年来，以 OpenSSL 等为代表的基础开源组件频现高危漏洞，给各国和企业造成不同程度的损失，促使国家和企业提高对开源软件基础安全评估的关注程度。美国 NSA 在《网络基础设施安全指南》技术报告中提出，定期将软件升级至供应商支持的更新版本**，**在使用前和使用过程中进行验证，以确保效率和安全。对于软件的评估包括：

- 验证软件和配置的完整性
- 维护正确的文件系统和引导管理
- 维护最新的软件和操作系统

由国家保密科学技术研究所主办的《保密科学技术》杂志曾写道，*现有的 CVE/CPE 体系以及 NVD 等漏洞库，已经无法满足开源软件安全治理的需求，需要创新开源软件的漏洞情报研究、共享、共治机制，合作建立开源软件漏洞情报库。[6] 风险控制措施：[7]* 

- 国家层面组织开展开源软件源代码检测工程

- 企业层面建设开源软件安全治理体系

- 用户侧建立软件安全渗透测试机制

- 检测机构加强对安全产品中开源组件的检测

**NVD（NATIONAL VULNERABILITY DATABASE，国家漏洞数据库）**

NVD 是美国政府使用安全内容自动化协议（SCAP）表示的基于标准的漏洞管理数据的存储库，可实现漏洞管理、安全测量和合规性的自动化，旨在帮助个人和公司研究漏洞管理的自动化及其他安全性和合规性目标。[8] *用户可以访问：[9]*

- *可搜索的漏洞数据库*

- *检查清单*

- *影响指标*

- *相关统计*


## 第三节 - 集成开源软件时关注传染性，避免商业核心代码被动开源

#### 3.1 产品集成开源软件必须满足开源 License 要求

企业管理使用开源软件需要有 IT 流程保证，避免开发人员在开发过程中随意使用开源软件。对于开发流程自动化的企业，可以在 DevOps 流程中进行检测引入的开源软件和版本是否为可以选用的版本。譬如在 nodejs 代码提交时，在代码管理平台自动检测 package.json 文件中引入软件包的变化，检查构建依赖、运行依赖的 Library 是否在容许引入的清单中。

在代码提交阶段的检查属于事后检查，需要产品经理、架构师和开发者等软件生命周期相关的参与者都在产品设计、技术架构设计阶段就考虑到使用的开源软件可能要旅行的义务。

MongoDB 一直使用 GNU AGPL（Affero General Public License）v3 的开源协议，但是 MongoDB 并没有在大量云服务厂商上赚到钱，所以 MongoDB 将协议切换为 SSPL ，即 Server Side Public License 。虽然 OSI 并不承认 SSPL 是开源许可协议，但是任何使用 MongoDB 的公司和个人也必须遵守 SSPL 对条款。如果企业的产品包含 MongoDB 并提供服务，就需要考虑 SSPL 协议带来的影响，所以在产品设计的伊始，产品经理就需要考虑开源软件的 License 遵从问题。

Elasticsearch 和 Kibana 的开源协议由之前的 Apache 2.0 切换为 Elastic 许可 + SSPL 的双重授权许可模式，对于使用 Elasticsearch 和 Kibanna 的产品也带来了重大影响，架构师要根据产品的需求、提供给客户的形态慎重选择 Elasticsearch 的组件和版本，避免带来 License 遵从的风险。架构师也可以考虑寻求其它的开源组件替代方案来解决这个问题。

所以一个软件研发的过程中，需要在流程设计上考虑到 License 遵从，在研发的每个阶段设计都要求参与者考虑到 License 遵从的风险，并且要为产品经理、架构师和开发者提供足够的支持，同时对于使用的开源软件需要通过 IT 流程机制进行控制，计划使用的开源软件需要在 IT 流程中进行申请和审批，确保参与审批的人是经过专业培训的。

| 常见许可证类型          | 典型软件              | 触发代码开源义务 前提条件                                    | 开源要求和范围                                               | 规避开源方式                                                 | License文本链接                                              |
| ----------------------- | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| BSD 类 如Apache/BSD/MIT | Tomcat，OpenSSL       | 无                                                           | 无                                                           | 不涉及                                                       | https://www.apache.org/licenses/LICENSE-2.0 （Apache license 2.0） https://www.openssl.org/source/license.html （Apache license v2） |
| MPL 类 如MPL/EPL等      | Firefox，Eclipse      | 产品集成使用该软件，并对外分发或销售，产品对该软件进行了修改 | 若无修改，则无需开源；若对其进行了修改，需将修改的部分开源   | 使用时不做任何修改                                           | https://www.mozilla.org/en-US/MPL/2.0/ （MPL license 2.0）   |
| LGPL                    | Hibernate，glibc      | 产品集成使用该软件，并对外分发或销售                         | 软件本身须开源。具有传染性，与其静态链接部分的代码也必须以 LGPL 许可开源；动态链接则不被传染 | 动态链接使用，仅开源其软件本身即可，产品代码可免受传染       | https://www.gnu.org/licenses/lgpl-3.0.html                   |
| GPL                     | Busybox，linux knrnel | 产品集成使用该软件，并对外分发或销售                         | 软件本身须开源。具有传染性，与其有链接关系的代码都必须以 GPL 许可对外开源，即与该软件在同一进程中运行的代码都必须开源 | 进程隔离，独立于产品进程运行，仅开源其软件本身即可，产品代码可免受传染 | https://busybox.net/license.html （GPL version 2） https://dri.freedesktop.org/docs/drm/process/license-rules.html#kernel-licensing （GPL version 2 only （GPL-2.0）） |
| AGPL                    | Berkeley DB           | 产品集成使用该软件                                           | 同 GPL                                                       | 同 GPL                                                       | https://www.gnu.org/licenses/agpl-3.0.html                   |
| SSPL                    | MongoDB               | 产品集成使用该软件                                           | 同 GPL + 其他相关运行服务                                    | 仅内部使用、不对外；购买商业协议                             | https://www.mongodb.com/licensing/server-side-public-license |



#### 3.2 开源软件选型原则和评估角度

##### 3.2.1 开源软件选型原则

1. 产品目标与开源软件的匹配度。业界实践认为如果需要修改开源软件的代码行数超过 **20%**，则不如购买更匹配功能的 “商业软件” 。避免在未来软件维护过程中产生的上有主干回合等开源技术债务引发的额外成本
2. 开源软件的 License 不兼容产品策略，譬如云服务要使用具有 SSPL 协议的开源软件，需要考虑到成本问题。
3. 开源软件的质量和安全是否满足产品的需求。
4. 开源社区是否已经不再更新，或者项目是否已经 Archive 

##### 3.2.2 开源软件评估原则

1. 开源软件的技术生态
   1. 技术架构、思路是否在业界具有先进性，是否有技术规划明确的项目目标
   2. 否有主流的供应商或者比较成熟的咨询公司
   3. 是否有比较大型的客户在使用该开源软件，有成熟应用场景和案例
2. 开源软件的合法合规
   1. 开源软件的获取来源是否可靠，是否可以持续的获取
   2. 开源 License 是否兼容、是否存在需要关注的专利等知识产权问题
   3. 开源软件是否满足产品销售地的贸易合规
3. 开源软件的生命周期
   1. 开源软件的版本的生命周期是否满足产品的需求
   2. 开源软件的社区是否有能力支撑
4. 开源软件的安全问题
   1. 对开源软件进行定期对病毒扫描
   2. 通过漏洞扫描发现安全风险
   3. 开源社区对已知安全问题的修复能力、修复周期
   4. 对开源软件进行全面的安全测试，保证符合产品的需求



## 第四节 - 架构设计解耦规则

#### 4.1 专有软件与开源解耦

- 规则描述：专有软件和开源代码在架构设计上解耦、逻辑解耦（可以独立升级开源软件版本）、物理解耦（独立文件或者进程）

1. GPL 传染性问题，造成不能在同一个进程中运行
   1. 对于传统修改 Kernel 的技术方案，可以采用 ebpf 的方式通过用户态应用来处理业务。ebpf 部分的代码可以根据 GPL 要求开源，但是实际处理业务的用户态的应用就可以隔离在 GPL 传染性之外。
2. 安全性问题，造成影响面扩大 - log4j 案例
3. 对于 Kernel 的修改可以采用 Patch 的方式分发，即使是商业分发，购买 Patch 的人只要不做二次分发就是合理的

- 问题案例：当因为产品原因修改开源软件的代码时，专有的代码和开源代码相互融合，难以解耦，修复开源软件的漏洞或者随开源软件的版本进行升级将非常困难

- 处理策略：制定基于开源开发的分层插件式的解耦策略，下列解耦的方式供参考

1. 特性间解耦：架构机制中将策略、数据和控制分离
2. 独立组件程序
3. 动态库链接方式 调用
4. 静态库链接方式 调用
5. 形成独立的文件

- 某产品整改过程中架构解耦的实践

1. 如果可以解耦调用，那么解耦 —— A 包含了 B 的代码变成 A 引用B的代码（案例: kernel 模块）。这种情况下，需要引入 B 项目，需要额外申请B软件的使用说明并对外履行义务

2. 如果解不开，而且的确是基于开源做的大量修改，那么老老实实认定这个项目是“对开源软件的修改”，而不是“专有软件对开源软件的引用”。—— A 包含了 B 的代码变成 A 就是 B。这种情况下，补丁式处理这种修改结果并且牵引更加合理的修改

   

#### 4.2 分析开源软件扩展机制，优先使用内置扩展机制实现定制特性

- 对于 Linux Kernel 的开发，使用 epbf 技术是目前最佳的选择。**扩展的柏克莱封包过滤器**（extented Berkeley Packet Filter，缩写 eBPF），是 类 Unix 系统上 数据链路层 的一种原始接口，提供原始链路层 封包 的收发，除此之外，如果网卡驱动支持洪泛模式，那么它可以让网卡处于此种模式，这样可以收到网络上的所有包，不管他们的目的地是不是所在 主机。参考维基百科和 eBPF 简史及 BPF、eBPF、XDP 和 Bpfilter 的区别。



![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=OGIzYjk1N2E4YzZmMDllMjdkYTY3MGI1MjNiYjk2ZTJfejVsM0llREE0NDdtR05NTGRPdEpjWHVwU2ttVUdHSzNfVG9rZW46Ym94Y25IYjV2SFZMb1lBTDNpWGczSEJ3MjZnXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)



Cilium 是基于 Kubernetes 的 Linux 容器管理平台上部署的服务，透明地提供服务间的网络和 API 连接及安全。Cilium 底层是基于 Linux 内核的新技术 eBPF，可以在 Linux 系统中动态注入强大的安全性、可见性和网络控制逻辑。 Cilium 基于 eBPF 提供了多集群路由、替代 kube-proxy 实现负载均衡、透明加密以及网络和服务安全等诸多功能。除了提供传统的网络安全之外，eBPF 的灵活性还支持应用协议和 DNS 请求/响应安全。同时，Cilium 与 Envoy 紧密集成，提供了基于 Go 的扩展框架。因为 eBPF 运行在 Linux 内核中，所以应用所有 Cilium 功能，无需对应用程序代码或容器配置进行任何更改。

这种方式为开发者提供了更多的选择，通过 ebpf 方式利用 Linux Kernel 底层的特性开发服务，并且可以在不违反 GPL 的情况下开发商业应用。当然一个架构设计的优秀开源项目会更容易拓展，Kubernetes 的架构设计可以说是经典的案例。

![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjA1NTZjOGQ3NzgyMDE2NzQ4NjIwYmY4NzYxYTdiNzRfaG9CRlZ2N0plRzltbjl3QVpHVjVrc05idVFBMDVHOWJfVG9rZW46Ym94Y25BOG10MEM2UVphbVZqa0hlY01RMElmXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)

Kubernetes 的架构更容易让商业发行版的厂商基于 Operator 、插件等机制扩展功能和性能，而选择是否开源则比较从容，并且不违反开源 License 。所以在选择开源产品的时候，对于开源软件的是否有足够的扩展机制，是选择的重要理由。



#### 4.3 遵从社区版本开发原则，对开源的修改尽量回馈社区

- 案例：虽然 [Apache 许可证（2.0 版）](https://www.apache.org/licenses/LICENSE-2.0)允许开发人员修改代码，无需将更改贡献给上游社区，但 Amazon 选择主动回馈 Lucene 和其他项目。秉承开源的贡献和收获精神，Amazon 已经向 Lucene 提出了多项重要的改进，包括：

1. 并发更新和删除
2. 建立自定义词语频率索引
3. 慵懒加载无限状态变送器

借助这些改进和 Lucene 社区已经构建的丰富现有功能，Amazon 搜索团队正在稳步实现在将 Lucene 用于所有 [Amazon ](http://amazon.com/)产品搜索的目标。它让 [Amazon](http://amazon.com/) 得以使用 Lucene 特有的功能（例如尺寸点和查询时间关联）来提升顾客购物体验。企业为客户提供良好长期体验的最佳方式，都需要投资开源软件。

- **社区版本开发原则**

1. 不背离社区，明确架构原则，遵从社区开发原则，对开源原生代码修改尽量回馈社区，不破坏开放和生态基础，避免与社区API接口不一致问题。

2. 基于开源开发新特性或功能时，产品需审视并遵从开源社区架构/设计的匹配情况，可参考以下流程决定哪些新增/修改代码应该开源或私有或废弃。

   

## 第五节 - 如何引用开源项目代码的片段

#### 5.1 将开源软件部分函数/宏或部分文件拷贝到产品专有软件代码中使用

##### 5.1.1 什么是开源项目代码片段引用

- 未完全引入开源软件版本的整包代码，仅将部分函数/宏或部分文件拷贝到产品专有软件代码中使用叫做片段引用。

- 片段引用情况举例：

1. 函数名不同，函数体相同（仅函数名不同，基本功能算法代码片段与开源完全相同） ；

2. 整段宏定义与开源代码完全相同；

3. 工具扫描相似度不高，但除函数内调用的接口不同外，变量定义等都与开源代码完全相同。

   

##### 5.1.2 引用可能产生的问题 - 案例

2021 年 12 月，TikTok Live Studio 疑似在不遵循 GPL 许可证的情况下使用了 OBS 的源代码。而 OBS 使用的 GPLv2 开源许可证具有很强的传染性：只要该软件使用过 GPL 协议的产品，则该软件产品也必须采用 GPL 协议，且必须是开源的。但 TikTok 并没有将其直播流媒体软件 “TikTok Live Studio” 开源。

![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTBkMjRjYjM4OGJkZmExYWE5ZDM5ZTg1ZDYzZjc0NTNfNDdkWlBCcGpESksxR0VjY0dBNUFuZXNRdHo1akwyMktfVG9rZW46Ym94Y252ZzU3NHJiRzdQdm1wUFZEeDg1dEVoXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)

从 TikTok Live Studio 反编译的代码看，其安装程序似乎与 OBS 的安装程序有着巧合般的相似…...

由于违反片段引用原则，TikTok Live Studio 最终在应用市场全面下架。

- **违反原则带来的风险**

1. **所有权方面** - 专有软件意味着 Copyright ，片段使用会导致专有软件代码混淆非企业版权的代码。对于本身就是开源的项目，则片段使用不存在此问题；

2. **协议履行方面** - 开源协议会涉及义务履行，片段使用容易导致“不知道使用了什么协议的代码”，进而忽略其相对应的对外义务履行；

3. **安全追溯方面** - 如果社区项目存在修复更新，片段使用的代码不容易追溯社区的修复。

   

##### 5.1.3 如何判断引用及扫码工具介绍

- 检验标准：对产品全量代码进行分析，确保所有使用的开源软件是整包使用，无片段引用情况，可借助扫描工具辅助分析。

- 扫描工具现状：

1. [SPDX](https://spdx.org/) - 一组用于传达与软件包相关的组件、许可证和版权的标准。

2. [LicenseFinder](https://github.com/pivotal-legacy/LicenseFinder) - 查找项目依赖项的许可证

3. [ScanCode-toolkit](https://github.com/nexB/scancode-toolkit)- 扫描代码以获取许可证、版权和依赖项

4. [FOSSology](https://www.fossology.org/) - 扫描代码以获取许可、版权和出口控制信息

5. [License](https://github.com/benbalter/licensee)- 识别项目的许可文件

6. [License Information Document](https://github.com/codeauroraforum/lid) - 从源代码中识别和提取许可证文本

7. [askalono](https://github.com/amzn/askalono) - 帮助检测许可证文本的库和命令行工具。它旨在快速、准确并支持各种许可文本。

8. [Licenseclassifier](https://github.com/google/licenseclassifier) - 一个库和一组工具，可以分析文本以确定它包含什么类型的许可证

9. [OSS Attribution Builder](https://github.com/amzn/oss-attribution-builder) - OSS Attribution Builder 是一个网站，可帮助团队创建软件产品中常见的归因文档（通知、“开源屏幕”、信用等）。

10. [OSS Review Toolkit](https://github.com/heremaps/oss-review-toolkit) - 通过扫描、下载源代码、报告任何错误和违反用户定义规则的行为以及创建第三方归因文档，对项目的源代码和依赖项进行高度自动化和可定制的开源合规性检查。

11. [fossa-cli](https://github.com/fossas/fossa-cli) - 任何代码库的快速、可移植和可靠的依赖分析

12. [Licensed](https://github.com/github/licensed) - 一个 Ruby gem，用于缓存和验证依赖项的许可证

13. [LicensePlist](https://github.com/mono0926/LicensePlist) - 一个命令行工具，可自动生成所有依赖项的 Plist，包括手动添加的文件（由 YAML 配置文件指定）或使用 Carthage 或 CocoaPods。

14. [dpkg-licenses](https://github.com/daald/dpkg-licenses) - 一个命令行工具，它列出了基于 Debian 的系统（如 Ubuntu）中所有已安装软件包的许可证。

15. [FOSSID](https://fossid.com/) - 用于许可证和漏洞的综合商业扫描程序。知识库涵盖 78M+ 存储库和 600B+ 片段。包括详细的片段扫描以检测片段和复制/粘贴代码上的许可证，即使未明确或正确声明开源许可证。

16. [DependencyTrack](https://github.com/DependencyTrack/dependency-track) - Dependency-Track 是一个智能组件分析平台，允许组织识别和降低软件供应链中的风险 

17. ScanOSS - 从开源项目的大型知识库中扫描您的代码库中的片段和抄袭。旨在与 CI/CD 和现代 IDE 集成，“从左开始”进行持续验证，而不是最后只报告一份。产品本身是完全开源的。


##### 5.1.4 如何正确处理开源软件的片段使用

- 如果不允许引用开源代码的片段，对于使用开源软件来说确实存在很大困难，如果必须引用，一定要遵守相应软件的 License 的义务。

- 是否重写开源软件：

1. 如果做不到完整引入开源软件，也没有可替代的商业软件，则需要根据实际产品需求进行开发。
2. 在重写时不要参照其代码，否则可能会被检测出重写的代码也使用了该开源软件。重写时可以选择其它团队，没有阅读过开源软件代码的工程师进行编写，在编写的过程中在不能访问 Internet 的网络条件下进行编写。

- 当引用一段开源软件的代码，即使做了以下的修改，也会被识别为代码片段引用

1. 修改函数名

2. 调整上下顺序

   

#### 5.2 涉及源代码交付，对开源原生代码进行修改的代码，使用 Patch 方式管理

- **什么是 Patch ？**

  Patch 是一个文本文档，也叫补丁，包含两个不同版本的源代码树之间的变化，是通过 diff 应用程序来创建

- **Patch 的业界优秀实践 - Linux Kernel** [10]

  Linux 内核的 Patch 是相对于包含内核源目录的父目录生成的。用 Patch 程序应用一个 Patch。Patch 程序读取 diff 或 patch 文件，并对其中描述的源代码树进行更改。这意味着 Patch 内部文件的路径包含生成 Patch 的内核源目录的名称（或其他一些目录名称，如“a/”和“b/”）。

- **如何应用或恢复 Patch ？**

  源代码交付场景，如涉及对开源原生代码进行修改，则修改的代码形成 Patch 文件并对其进行管理。

1. 每次贡献/合入社区的 Patch 尽量只解决一个问题，功能单一；

2. 通过 Patch 化合入每次修改的内容；

3. 修改开源的 Patch 源码文件，采用开源社区代码规范要求，方便回归社区。

   注：对开源原生代码进行修改形成 Patch 文件只是一种管理形式，并不解决耦合问题，实际上这种修改方式仍是将修改的代码与开源代码耦合在一起，模糊不清。

   

## 第六节 - 开源代码依赖管理最佳实践

#### 6.1 专有软件依赖的开源软件代码存储实践

- 将产品专有软件代码与开源软件隔离（参见业界 Google 案例），开源软件独立目录存放。从代码目录结构区分出 open_source 目录、 vendor 目录、code 专有软件目录。

- 检验标准：同规则描述

- Google 开源软件管理：https://opensource.google.com/docs/thirdparty/

  

#### 6.2 依赖管理最佳实践

**Google 的依赖管理最佳实践** [11]

- **版本锁定 -** 将应用程序依赖项的版本限制为非常特定的版本。

- **签名和哈希验证 -** 启用哈希验证可确保依赖项不会被不同的文件替换，无论是人为攻击还是破坏工件存储库；签名验证为验证过程增加了额外的安全性。

- **锁定文件和编译的依赖项 -** 通常由安装工具自动生成，锁定文件将版本锁定、签名和哈希验证与应用程序的完整依赖树相结合。应用程序的所有依赖项，包括所有子依赖项、它们的依赖项以及向下堆栈，都包含在锁定文件中。

- **混合私有和公共依赖项 -** 在混合私有和公共依赖项时，需注意“依赖项混淆”攻击：通过将与内部项目同名项目发布到开源存储库，攻击者利用错误配置的安装程序偷偷安装他们内部包上的恶意库。

- **删除未使用的依赖项 -** 在不再使用依赖项时继续将它们与应用程序一起安装会增加依赖项足迹及这些依赖项中漏洞危害的可能性。让应用程序在本地工作，将在开发过程中安装的每个依赖项复制到应用程序的需求文件中，并对其进行部署。

- **漏洞扫描 -** 漏洞扫描工具使用锁定文件准确确定依赖的工件，并在新漏洞出现时及时通知，甚至提供建议的升级路径。



为避免“依赖混淆”攻击，可采取以下步骤：

- 通过将依赖项包含在锁定文件中来验证依赖项的签名或哈希值

- 将第三方依赖和内部依赖的安装分为两个不同的步骤

- 手动或使用直通代理将需要的第三方依赖项显式镜像到私有存储库中 

  

## 第七节 - 开源软件义务履行规则

#### 7.1 开源使用声明无遗漏、易获取

- 产品发布时，随产品附上一份文档《Open Source Software Notice》，在该文档中写明产品所使用的开源软件及其版权和 License 信息，并附上不担保声明。同时确保使用声明软件与实际使用的软件保持一致，避免遗漏，易获取。

- Cisco 案例：[Open Source License Notices for Cisco Unified Communications Manager](https://www.cisco.com/c/en/us/td/docs/voice_ip_comm/cucm/os_license/cucm_lic.html)

![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=NTVlMGIzY2VjNWY1YjM4YTMzYTgzNzVjYjQxYTA5MTlfZHYwMkNhdlUzc2hTV0JudkJteExzRm5XRERicEhtdndfVG9rZW46Ym94Y25pTWN3VU9VNmtsRElTTUh3ZFo5RkhkXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)

- 根据产品中所使用的开源软件，按以下格式输出软件声明（Copyright Notice and License Texts）

1. Software: 软件名称+软件版本号
2. Copyright notice: 软件版权信息 （软件包中版权或说明文件/官网/代码文件头）
3. License: 软件 License 信息（包含具体内容）

![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjIzMzI2ZjFiZDM1N2Y0OTk5MzQ1MjZjMDI5YmQxYmJfVnhGemQxQ0xmN01NMG02R2hsaXZVZGpISWNVYUdERHhfVG9rZW46Ym94Y25pdjVqck54ZFJKVm9hU2MyR3ZZQnloXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)

- 验证《Open Source Software Notice》文档，确保其符合开源使用声明义务履行要求。



#### 7.2 履行代码对外开源义务

**案例：GitHub 伊朗等国开发者遭封禁**

2019 年下半年，美国怀疑伊朗制造核弹，国际关系进一步紧张，美国加紧了对伊朗的单边制裁，其中一项制裁措施就是「贸易禁令」，禁止美国人把美国的商品、技术、服务出口给伊朗，其中也包括美国的 GitHub 代码托管平台。[12]

2019 年 7 月，一位自 2012 年以来一直使用 GitHub 的伊朗开发者在不知情的情况下被 GitHub 封禁账户，认为他在利用免费的私有库开发核武器。此前，一位克里米亚地区的俄罗斯籍开发者的账号同样遭到封禁。2022 年 3 月，微软的开源项目 JavaScript 框架 Aurelia 因项目中有两名来自伊朗的外部贡献者被 GitHub 封禁。同年 12 月，GitHub 封禁了总部位于德国的初创服务公司 Pure Labs 的所有账号，原因竟是“一名员工在回伊朗探望父母时打开了笔记本电脑”。[13] [14]

美国对包括伊朗在内的多个国家实施的制裁措施阻断了美国公司与受制裁国家中的任何人开展任何业务。GitHub 表示，GitHub.com、GitHub Enterprise Server 以及开发者上传至其中任一产品信息都需遵守贸易管制法规，包括美国出口管理条例（Export Administration Regulations, EAR）。但为了实现让全球开发者都能使用 GitHub 的目标，GitHub 采取了以下两项措施：

- 即使 GitHub 遵守制裁，但 GitHub 上提供的公共存储库不受国际武器贸易条例（International Traffic in Arms Regulations，ITAR）的约束，即使在受制裁的国家也可以使用公共存储库。[15]
- GitHub 已获得美国财政部下属的外国资产控制办公室（OFAC）的许可，可以为位于或居住在伊朗的开发者提供云服务。 这包括为个人和组织提供的一切免费和有偿的公共和私人服务。[15]

作为全球最大的代码托管平台，GitHub 不仅是代码的天堂，更是承载开源项目的沃土。但美国长期以来对包括伊朗在内的多个国家实施广泛的制裁，这也是为什么业内一直争论开源是否有国界的原因。

- 对于涉及敏感国家地区销售的产品，若产品涉及履行对外开源义务，须组织审核验证“对外开源代码包”，根据团队所选择的对外开源方式（如 Written Offer）履行义务，确保无法务风险。

1. 产品应结合自身使用场景，按照所使用的开源软件 License 要求将相应代码从产品代码中提取出来制作开源代码包；
2. 开源内容必须为代码，若产品以二进制包形式使用开源软件，须提供其源码；
3. 开源内容不得超出 License 要求范围，且开源内容范围必须通过审批决策；
4. 对于 GPL/LGPL 类开源软件，必须确保开源代码能够通过编译：
   1. 书面要约（Written Offer）：若产品使用了 GPL、LGPL、MPL 等具有对外开源义务的软件，必须在使用声明中附上此部分，向客户承诺履行代码开源义务。此部分直接从模板中拷贝使用；若产品不涉及强制开源义务，则使用声明文档中不得包含此部分内容；
   2. AGPL V3 开源软件被用于远程交互场景下时，修改代码后即使不分发也必须向用户提供源代码。不能采用统一的 Written Offer 模式，对使用 AGPL V3 的在线软件的开源遵从方式需改成直接开源。



#### 7.3  如对开源软件修改，须在修改的源码文件头附上修改声明

- 规则描述：产品若对开源软件进行了修改，需在修改的源码文件头附上修改声明，说明修改人、修改时间、修改内容。

- 修改声明举例：

```C
/*
==============
= GetUart 
= Origin from https://github.com/id-Software/DOOM/blob/master/sersrc/PORT.C
= Commit SHA1 95e6d43
= Edited by Carl 1999
==============
*/
void GetUart (void)
{
        char   far *system_data;
        static int ISA_uarts[] = {0x3f8,0x2f8,0x3e8,0x2e8};
        static int ISA_IRQs[] = {4,3,4,3};
        static int MCA_uarts[] = {0x03f8,0x02f8,0x3220,0x3228};
        static int MCA_IRQs[] = {4,3,3,3};
        int                p;

        if (CheckParm ("-com2"))
                comport = 2;
        else if (CheckParm ("-com3"))
                comport = 3;
        else if (CheckParm ("-com4"))
                comport = 4;
        else
                comport = 1;

        regs.h.ah = 0xc0;
        int86x( 0x15, &regs, &regs, &sregs );
        if ( regs.x.cflag )
        {
                irq = ISA_IRQs[ comport-1 ];
                uart = ISA_uarts[ comport-1 ];
                return;
        }
        system_data = ( char far *) ( ( (long) sregs.es << 16 ) + regs.x.bx );
        if ( system_data[ 5 ] & 0x02 )
        {
                irq = MCA_IRQs[ comport-1 ];
                uart = MCA_uarts[ comport-1 ];
        }
        else
        {
                irq = ISA_IRQs[ comport-1 ];
                uart = ISA_uarts[ comport-1 ];
        }

        p = CheckParm ("-port");
        if (p)
                sscanf (_argv[p+1],"0x%x",&uart);
        p = CheckParm ("-irq");
        if (p)
                sscanf (_argv[p+1],"%i",&irq);


        printf (STR_PORTLOOK" 0x%x, irq %i\n",uart,irq);
}
```



## 第八节 - 开源还是专有软件判定规则进阶

- 法理依据：思想与表达 —— 思想没有版权、表达有版权。软件的功能是思想，功能的实现是表达；如果一个思想仅有少数的表达，那么表达的相似不做追究。

- 开源转专有软件的难度：思想同开源项目 —— 框架类似开源项目 —— 结构体类似开源项目 —— 流程类似开源项目 —— 代码类似开源项目

- 开源专有软件的攻防 

1. 矛：如何肉眼预估存在片段引用 如果结构体和流程相似，代码大概率类似开源项目。 
2. 盾：如何自证清白 避免陷入代码相似的争论，从源头上自证 – 功能（思想）存在差异不同，设计文档存在差异。

- 案例：企业开源的项目能否认定为专有软件
  - 某团队将代码开源出去，同时在另外一个专有软件项目里面片段复用了同样的代码，那么是否还需要修改。如果不修改，便违背了开源专有软件隔离的要求；如果修改，自己写的代码为什么开源后就失去了控制权，还要想另一个方法再实现一遍？

- 解答：这个问题主要出在“专有软件和开源”的提法上，这个提法事实上形成了“对立”：即非专有软件就是开源。它在绝大多数情况下是正确的，沿用利于团队实施。但从字眼上分析，“专有软件”的对立面是“第三方”，“开源”的对立面是“闭源”。回到上面的案例，这段代码既属于“专有软件”，也属于“开源”，而且当专有软件认定符合本文开头的三个原则时，则不需要整改。

- 所有权和开源协议

1. 所有权是企业的代码，协议解释权也属于企业 —— 可以把这段代码规定为各种开源协议，也可以规定为商业协议（参考 Oracle/Mongodb 的双协议案例）。企业代码被开源“污染”属于法务遵从的问题，不破坏所有权。
2. 企业的 A 项目和社区 GPL 协议的 B 项目静态链接生成 C 产品，则 A 项目在 C 产品的场景下需遵循 GPL 的协议对外履行义务； 之后（不包括 B )，如果 A 项目和企业内部的专有软件 D 项目静态链接生成 E 产品，那么 A 项目在 E 产品的场景下，可以以企业专有软件进行认定，不会因为“曾经被 B 污染”而导致在 E 场景下也是 GPL 协议，更不会导致 D 项目也变成 GPL 。



## 第九节 - 维护与升级替换规则

#### 9.1 产品使用开源软件须具备开源软件维护能力

产品使用开源须具备开源维护能力。对于产品核心模块的开源应用，建议参与并主导开源社区，具备社区影响力，掌握该开源软件的演进方向和发展趋势，具备开源软件维护能力，满足客户问题响应和安全漏洞修复 SLA 要求。根据自身业务特点，对开源软件进行评估确定需要投入不同的资源进行维护。



## 第十节 - 开源软件维护

#### 10.1 开源软件维护总体原则

1. 对于社区内已披露但未提供修补方案的漏洞，由产品自行消减漏洞风险；

2. 开源软件维护方发布新版本或社区补丁质量标准与社区发布的标准一致，回合补丁须保证漏洞已被修补；

3. 开源软件维护方发布新版本或补丁修补漏洞，应满足开源软件漏洞修补 SLO 时间；

4. 开源软件维护方不仅要对主软件（及下层开源组件）进行维护，依赖软件（及下层开源组件）也需维护；

5. 开源软件维护方不承接产品特性或功能需求，若有相关需求，需通过正常平台需求管道提出。

   

#### 10.2 漏洞修复流程

从上游 NVD 等漏洞库定期推送漏洞信息到社区，由专家团队，定期分析这些漏洞并修复。系统会将漏洞推送给所有使用典型商业软件的产品团队，产品团队进一步分析，是否影响产品，如果影响，就会推送给维护方。维护方可能是专业的开源软件专家，进一步调整解决方案；解决方案有可能来自社区，社区有解决方案，我们是要用社区解决方案还是企业自己的解决方案？社区版本可以自己维护控制，一旦产品团队自己过多的维护干扰，后面的代码升级有可能出现漏洞。所以，尽可能用社区的解决方案，保障代码的升级。如果社区没有解决方案，我们在SLA的使用范围内，产品团队可以做一些修复，消解风险后，可以通知市场销售团队，哪些产品在哪些国家、哪些客户产生了影响，提供修复的方案给市场销售团队，和客户一起修复漏洞。

对于开源社区当接收到上报的漏洞信息时，安全团队对漏洞进行评估并完成漏洞影响描述，获得CVE（Common Vulnerabilities & Exposures，通用漏洞披露）。SIG 维护者完成补丁开发并进行验证。系统将漏洞修复方案推送给下游厂商的技术市场、市场销售团队，由市场销售团队和客户产品团队进一步分析是否影响产品，进一步调整解决方案。

![img](https://openeuler.feishu.cn/space/api/box/stream/download/asynccode/?code=YzYxMjNjNDJiNzFhMTM5N2NmOTg4Nzg5ZGY2NjBjMGFfNWdIV2lPZGtrZ1A5MWd0MDNLVnRtaEs2bFNZbmFkRlBfVG9rZW46Ym94Y256WHRoekdQNnhwNHN3TFRRQ3pxODZmXzE2NTE5OTA5Nzc6MTY1MTk5NDU3N19WNA)



#### 10.3 升级版本模式要求

- **规则1：社区同时提供新版本和补丁解决漏洞时，由开源软件维护方确定提供何种修补方案。** 

- 说明：社区升级新版本，开源软件维护方就提供新版本；社区提供补丁，开源软件维护方也提供社区补丁；但当社区同时提供两种修补方案时，开源软件维护方需要与社区进行互动，选择社区推荐的修补方案并进行评估，确定提供何种修补方案。 

- 案例：Libssh 是一款采用升级版本模式维护的软件，为解决 Libssh 0.7.3 以前版本存在的 CVE-2016-0739 漏洞，社区不仅发布了 0.7.4 新版本，还发布了 CVE-2016-0739-libssh-0.5.5.patch、CVE-2016-0739-libssh-0.6.5.patch 等补丁文件，开源软件维护方根据社区建议选择新版本 0.7.4 来修补漏洞。

- **规则2：解决漏洞的新版本须满足选型规范的要求进行引入。** 

- 说明：如果社区提供的解决漏洞的新版本均不满足公司对产品的需求，且社区没有提供解决漏洞的补丁，则开源软件维护方可不提供漏洞解决方案，由产品自行消减漏洞风险。 

- 案例：为解决 fastjson 1.2.60 拒绝服务安全漏洞，某团队在社区发布修复漏洞 1.2.61 hotfix 版本的当天将其引入公司。经公司 TMG 评审发现，该版本并未经社区测试，该团队也并未评估社区安全修复建议，新版本存在不兼容 bug，导致产品测试环境宕机。



#### 10.4 补丁回合模式要求

- **规则1：为形成一套面向客户可见的企业开源软件版本管理机制，开源软件维护方须遵循开源软件维护版本命名和漏洞补丁命名规则，规范开源软件维护版本及补丁的名称。** 

1. **开源软件维护版本命名：**

   开源软件自身版本命名沿用各自社区命名，维护方后续发布的开源软件补丁版本命名如下：

   - 开源软件名 - 社区版本 - hX，代号固定为 h ，X 表示数字 1~n ，可根据需要扩展多位
   - 如 openssl - 1.1.1a - h1，表示维护方发布的 Openssl 软件 1.1.1a 版本的第一个补丁版本。

2. **开源软件漏洞补丁命名**：

   开源软件漏洞补丁命名：

   - 社区发布的 CVE 补丁，需体现 CVE 名，例如 openssl-1.1.1a-CVE-1234.patch；

   - 如果涉及一个 CVE 有多个补丁，可增加编号，例如 openssl-1.1.1a-CVE-1234-001.patch；如涉及多个 CVE，可采用 fix-CVE-multiple 等标识，最终在公共配置文件里面描述详细修复内容；

   - 开源软件维护方从新版本回合的 CVE 补丁，除体现 CVE 名之外，还需增加 backport 前缀，例如 openssl-1.1.1a-backport-CVE-1234.patch；

   - 社区发布的非 CVE 补丁，简单描述补丁的功能，例如 openssl-1.1.1a-fix-xxxxx.patch；

   - 每个补丁修复一个漏洞，避免出现超大补丁。

- **规则2：为支撑开源软件维护方跨开源软件版本维护，开源软件维护方须遵循维护分支管理规则，对各维护版本进行管理和隔离。** 

1. 每个开源软件版本建立一个分支，存放开源软件社区原始包、公共补丁及公共补丁配置文件；
2. 版本分支从 master 拉出，命名为“软件名_软件版本-stable/upstream”；



#### 10.5 依赖软件维护要求

- 依赖软件的漏洞按照主软件社区提供的漏洞修补方案进行修补，主软件社区未提供漏洞修补方案的，由商业产品自行消减漏洞风险。

- 主软件社区修补依赖软件漏洞的方式：（开源软件维护方可选择任意一种社区方案进行漏洞修补）

1. 如果主软件升级新版本，依赖软件也升级新版本，则升级主软件；
2. 如果主软件不升级新版本，但提供补丁修补依赖软件漏洞，则提供社区补丁。

- 案例1：开源软件 EDKII 依赖 OpenSSL 提供加解密算法能力，社区老版本 edk2-stable201908 使用的 OpenSSL 1.1.1b 社区曝出漏洞 CVE-2019-1543,CVE-2019-1552 和 CVE-2019-1563。EDKII 社区在 2019 年 11 月发布新版本 edk2-stable201911，将 OpenSSL 1.1.1b 升级到 OpenSSL 1.1.1d 以解决该漏洞，同时开源软件维护方应通过升级 EDKII 到 edk2-stable201911 来修补漏洞。

- 案例2：开源软件 curl 依赖 kerberos 提供 ftp 通信能力，curl 7.66.0 曝出依赖的 Kerberos 有高危漏洞 CVE-2019-5481。curl 社区在 2019 年 9 月发布补丁解决该漏洞，但未同时发布新版本，开源软件维护方应通过引入社区补丁来修补漏洞。



## 附录

#### 附录 A - 术语表

| **术语**                                          | **含义及解释**                                               |
| ------------------------------------------------- | ------------------------------------------------------------ |
| **Proprietary Software** **专有软件 或 私有软件** | 软件生产方自己保有知识产权的软件，不包含任何第三方知识产权的软件，这种软件往往被其拥有者视为商业秘密 |
| **开源代码片段使用**                              | 截取部分开源软件代码片段整合入专有软件中的行为称为片段使用开源代码。片段使用开源代码可能产生版权合规和网络安全问题 |
| **合理使用**                                      | 并不是所有的片段使用开源代码都是违反版权法的，各国著作权法允许个人在一定使用范围和场景内使用有版权的代码片段。这一条款称之为合理使用 |
| **开源软件中央仓库**                              | 在企业中设立开源软件中央仓库，企业内开发时只能使用开源软件中央仓库中规定的开源软件项目及指定的版本；对开源项目和指定的版本设立优先级，在选用开源软件的时候，依据产品、用户、销售范围等因素选择合适的开源软件及版本；使用过程中设定申请使用流程，根据不同级别进行限定。 |



#### 附录 B - License 参考

| License                                                      | SPDX                     | Can（Rights）                                                | Must（Obligations）                                          | Cannot（Limitations）                                        |
| ------------------------------------------------------------ | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| BSD Zero Clause License                                      | 0BSD                     | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | None Yet. 暂无                                               | Hold Liable / Place Warranty 质量保证                        |
| Academic Free License v3.0                                   | AFL-3.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License  包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证 Use Trademark 使用商标 |
| GNU Affero General Public License v3.0                       | AGPL-3.0-only            | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Install Instructions 包含安装指南/脚本  Disclose Source 源代码可获取 Include Copyright & License 包含版权和许可证  Network Use Is Distribution 网络访问也视同分发  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty  质量保证                       |
| Apache License 2.0                                           | Apache-2.0               | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Artistic License 2.0                                         | Artistic-2.0             | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Install Instructions 包含安装指南/脚本  Include Original 包含原始软件  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty  质量保证  Use Trademark 使用商标 |
| BSD 2-Clause "Simplified" License                            | BSD-2-Clause             | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty  质量保证                       |
| BSD 3-Clause Clear License                                   | BSD-3-Clause-Clear       | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Patent Use 专利授权  Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| BSD 3-Clause "New" or "Revised" License                      | BSD-3-Clause             | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| BSD 4-Clause "Original" or "Old" License                     | BSD-4-Clause             | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Give Credit 指明原始作者 Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Boost Software License 1.0                                   | BSL-1.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty  质量保证                       |
| Creative Commons Attribution 4.0 International               | CC-BY-4.0                | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Give Credit 指明原始作者  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Patent Use 专利授权  Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Creative Commons Attribution Share Alike 4.0 International   | CC-BY-SA-4.0             | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  Same License 许可证“传染性”  State Changes 列明修改 | Patent Use 专利授权  Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Creative Commons Zero v1.0 Universal                         | CC0-1.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | None Yet. 暂无                                               | Patent Use 专利授权  Hold Liable / Place Warranty  质量保证  Use Trademark 使用商标 |
| CeCILL Free Software License Agreement v2.1                  | CECILL-2.1               | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty  质量保证                       |
| Educational Community License v2.0                           | ECL-2.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty  质量保证  Use Trademark 使用商标 |
| Eclipse Public License 1.0                                   | EPL-1.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Install Instructions 包含安装指南/脚本  Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性” | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Eclipse Public License 2.0                                   | EPL-2.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Install Instructions 包含安装指南/脚本  Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性” | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| European Union Public License 1.1                            | EUPL-1.1                 | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Network Use Is Distribution 网络访问也视同分发  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| European Union Public License 1.2                            | EUPL-1.2                 | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Network Use Is Distribution 网络访问也视同分发  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| GNU General Public License v2.0                              | GPL-2.0-only             | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| GNU General Public License v3.0                              | GPL-3.0-only             | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Install Instructions 包含安装指南/脚本  Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| ISC License                                                  | ISC                      | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| GNU Lesser General Public License v2.1                       | LGPL-2.1-only            | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License (library) 许可证“传染性”-动态链接可隔离  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| GNU Lesser General Public License v3.0                       | LGPL-3.0-only            | Commercial Use商业使用 Distribute分发 Modify修改 Patent Use专利授权 Private Use私下使用 | Include Install Instructions 包含安装指南/脚本  Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License (library) 许可证“传染性”-动态链接可隔离  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| LaTeX Project Public License v1.3c                           | LPPL-1.3c                | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取 Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| MIT License                                                  | MIT                      | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| Mozilla Public License 2.0                                   | MPL-2.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Original 包含原始软件 Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License (file) 许可证“传染性”-仅文件 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Microsoft Public License                                     | MS-PL                    | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Microsoft Reciprocal License                                 | MS-RL                    | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License (file) 许可证“传染性”-仅文件 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| University of Illinois/NCSA Open Source License              | NCSA                     | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| SIL Open Font License 1.1                                    | OFL-1.1                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  Same License 许可证“传染性” | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Open Software License 3.0                                    | OSL-3.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Network Use Is Distribution 网络访问也视同分发  Same License 许可证“传染性”  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| PostgreSQL License                                           | PostgreSQL               | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| The Unlicense                                                | Unlicense                | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | None Yet.暂无                                                | Hold Liable / Place Warranty 质量保证                        |
| Universal Permissive License v1.0                            | UPL-1.0                  | Commercial Use 商业使用 Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| Vim License                                                  | Vim                      | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性”  State Changes 列明修改 | None Yet. 暂无                                               |
| Do What The F*ck You Want To Public License                  | WTFPL                    | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | None Yet. 暂无                                               | None Yet. 暂无                                               |
| zlib License                                                 | Zlib                     | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| Artistic License 1.0 (Perl)                                  | Artistic-1.0-Perl        | Private Use 私下使用                                         | None Yet. 暂无                                               | None Yet. 暂无                                               |
| Artistic License 1.0                                         | Artistic-1.0             | Private Use 私下使用                                         | None Yet. 暂无                                               | None Yet. 暂无                                               |
| GNU Library General Public License v2 only                   | LGPL-2.0-only            | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Original 包含原始软件  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  Same License 许可证“传染性” State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| [Zope Public License 2.0](https://spdx.org/licenses/ZPL-2.0.html) | ZPL-2.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Zope Public License 2.1](https://spdx.org/licenses/ZPL-2.1.html) | ZPL-2.1                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [zlib/libpng License with Acknowledgement](https://spdx.org/licenses/zlib-acknowledgement.html) | zlib-acknowledgement     | Commercial Use 商业使用  Distribute 分发  Modify 修改        | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| [Common Development and Distribution License 1.1](https://spdx.org/licenses/CDDL-1.1.html) | CDDL-1.1                 | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Mozilla Public License 1.1](https://spdx.org/licenses/MPL-1.1.html) | MPL-1.1                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Give Credit 指明原始作者  Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Common Public License 1.0                                    | CPL-1.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证                        |
| [Common Development and Distribution License 1.0](https://spdx.org/licenses/CDDL-1.0.html) | CDDL-1.0                 | Commercial Use 商业使用  Distribute 分发  Modify 修改  Patent Use 专利授权  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Freetype Project License](https://spdx.org/licenses/FTL.html) | FTL                      | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| [BSD Protection License](https://spdx.org/licenses/BSD-Protection.html) | BSD-Protection           | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Give Credit 指明原始作者  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Creative Commons Attribution 3.0 Unported](https://spdx.org/licenses/CC-BY-3.0.html) | CC-BY-3.0                | Commercial Use 商业使用 Distribute 分发  Modify 修改         | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证                        |
| [Unicode Terms of Use](https://spdx.org/licenses/Unicode-TOU.html) | Unicode-TOU              | None Yet. 暂无                                               | None Yet. 暂无                                               | None Yet. 暂无                                               |
| [Apache License 1.1](https://spdx.org/licenses/Apache-1.1.html) | Apache-1.1               | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Adobe Postscript AFM License](https://spdx.org/licenses/APAFML.html) | APAFML                   | Distribute 分发  Modify 修改  Private Use 私下使用           | Include Original 包含原始软件  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| [Apple Public Source License 2.0](https://spdx.org/licenses/APSL-2.0.html) | APSL-2.0                 | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [Server Side Public License, v 1](https://spdx.org/licenses/SSPL-1.0.html) | SSPL-1.0                 | None Yet. 暂无                                               | None Yet. 暂无                                               | None Yet. 暂无                                               |
| [Imlib2 License](https://spdx.org/licenses/Imlib2.html)      | Imlib2                   | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证                        |
| [Open Software License 2.1](https://spdx.org/licenses/OSL-2.1.html) | OSL-2.1                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| BSD-3-Clause-Attribution                                     | BSD-3-Clause-Attribution | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| SGI Free Software License B v2.0                             | SGI-B-2.0                | Commercial Use 商业使用 Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Python License 2.0                                           | Python-2.0               | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| FSF All Permissive License                                   | FSFAP                    | Private Use 私下使用                                         | None Yet.暂无                                                | None Yet.暂无                                                |
| Academic Free License v2.1                                   | AFL-2.1                  | Private Use 私下使用                                         | None Yet.暂无                                                | None Yet.暂无                                                |
| Mozilla Public License 1.0                                   | MPL-1.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证                        |
| MIT +no-false-attribs license                                | MITNFA                   | None Yet.暂无                                                | None Yet.暂无                                                | None Yet.暂无                                                |
| copyleft-next 0.3.0                                          | copyleft-next-0.3.0      | None Yet.暂无                                                | None Yet.暂无                                                | None Yet.暂无                                                |
| CNRI Python License                                          | CNRI-Python              | Private Use 私下使用                                         | None Yet.暂无                                                | None Yet.暂无                                                |
| Open Software License 2.0                                    | OSL-2.0                  | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Disclose Source 源代码可获取  Include Copyright & License 包含版权和许可证 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| Aladdin Free Public License                                  | Aladdin                  | Distribute 分发  Modify 修改                                 | Include Original 包含原始软件  Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Commercial Use 商业使用  Hold Liable / Place Warranty 质量保证 |
| [Apple MIT License](https://spdx.org/licenses/AML.html)      | AML                      | Commercial Use 商业使用  Distribute 分发  Modify 修改  Private Use 私下使用 | Include Copyright & License 包含版权和许可证                 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |
| [bzip2 and libbzip2 License v1.0.6](https://spdx.org/licenses/bzip2-1.0.6.html) | bzip2-1.0.6              | Commercial Use 商业使用  Modify 修改                         | Include Copyright & License 包含版权和许可证  State Changes 列明修改 | Hold Liable / Place Warranty 质量保证  Use Trademark 使用商标 |



## 参考资料

[1]甲骨文诉谷歌 Java 侵权案

https://zh.wikipedia.org/wiki/%E7%94%B2%E9%AA%A8%E6%96%87%E8%AF%89%E8%B0%B7%E6%AD%8CJava%E4%BE%B5%E6%9D%83%E6%A1%88

[2]ORACLE AMERICA，INC. V. GOOGLE LIC

https://www.leagle.com/decision/infco20180327178

[3]所有判决被推翻，美最高法院：Java 版权世纪大案，谷歌战胜甲骨文

https://finance.sina.com.cn/tech/2021-04-06/doc-ikmyaawa7809324.shtml

[4] Google VS Oracle 90 亿美金代码悬案落锤 

https://zhuanlan.zhihu.com/p/510872344

[5] Ruby用实际行动向GPLv3吐槽，Ruby 1.9.3将改用 BSD 许可证发布  

https://blog.delphij.net/posts/2011/08/rubygplv3ruby-1/

[6] 国家保密局——开源软件漏洞安全风险分析  http://www.gjbmj.gov.cn/n1/2020/1127/c411033-31947310.html

[7] 开源软件风险分析及治理措施研究  http://www.gjbmj.gov.cn/n1/2020/1127/c411033-31947270.html

[8] NATIONAL VULNERABILITY DATABASE General Information  https://nvd.nist.gov/general

[9] Techopedia 解释了国家漏洞数据库（NVD） https://cn.theastrologypage.com/national-vulnerability-database

[10]  Applying Patches To The Linux Kernel  https://www.kernel.org/doc/html/v4.18/process/applying-patches.html

[11] 谷歌的依赖管理最佳实践

https://www.jdon.com/57083

[12]  财政部禁令政策  https://home.treasury.gov/policy-issues/office-of-foreign-assets-control-sanctions-programs-and-information

[13]《GitHub 的挣扎：已获美国许可，恢复在伊朗的服务》https://www.infoq.cn/article/uss2tktbzdzls9cafk5x

[14]《我疯起来自己都害怕！GitHub 封禁自家开源项目 Aurelia 引众怒，CEO 公开道歉，但开发者们并不买账》https://baijiahao.baidu.com/s?id=1661953225202005584&wfr=spider&for=pc

[15]  GitHub 和贸易管制  https://docs.github.com/cn/site-policy/other-site-policies/github-and-trade-controls