# 开源安全及其风险管理

## 开源安全现状和挑战

### 重点挑战  开源组件选型、漏洞提前感知和修复、未公开漏洞发掘、韧性架构

* 开源选型和质量管控：当前选型规则较松，缺乏选型质量把控；存在安全问题，一些问题可能带来隐患和质疑。
  * 挑战：开源软件安全问题排查工作量大，目前扫描工具效果不佳，存在大量误报。
    部分典型问题：
    * 明文密钥问题
    * 不安全随机数问题
    * 包含大量未公开接口和公网地址
    * 使用不安全协议和算法
* 漏洞管理：上千款开源软件已知漏洞管理是个大工程，攻击者常用的手段是使用未修复的已知漏洞及其变种来攻击目标。
  * 挑战：
    * 明文密钥问题
    * 无CVE警示的漏洞修复
    * 协议类、架构类漏洞修复成本高
* 未公开漏洞：攻击者很可能使用开源软件的未公开漏洞（0-day）攻击，如何减少0-day漏洞攻击影响是业界难题。
  * 每年数十例0-day攻击被发现，近年有上升势态。0-day攻击的防范一直是业界挑战，需要在漏洞发现和韧性架构等方面综合投入

### 开源软件漏洞数逐年增加，安全形势日益严峻

从2016年到2020年，开源软件包含的安全问题是逐年增加，16年每一个开源软件包含的漏洞问题平均是84个，到2020年，增长到了528个，5年259%，增长了2.5倍。越来越频繁使用开源软件，例如云计算或者AI，80%以上是使用开源软件技术来搭建系统的，安全方面就非常脆弱，这就需要我们有相应完整的流程，完备的技术和方法来保护开源软件的安全，尽量把安全风险降低到可控的范围内。

具体参考SYNOPAYS报告：https://www.synopsys.com/software-integrity/resources/analyst-reports/open-source-security-risk-analysis.html?intcmp=sig-blog-os-rightrail

### 网络安全： Log4Shell漏洞影响面之广！

* 案例：2021年11月24日在Web服务器软件阿帕奇（Apache）下的开源日志组件Log4j 2.x内发现漏洞，这个后来编号为 CVE-2021-4428的漏洞，花名为Log4Shell。这一漏洞的存在，可以让网络攻击者无需密码就能访问网络服务器。网络安全管理公司Cloudflare首席安全官乔·沙利文（Joe Sullivan）表示，这一漏洞允许恶意攻击者“远程执行代码”，以获取对其他系统的访问，鉴于Log4j软件被广泛使用，这可能是迄今为止“最大的漏洞”。
* 启示：
  * 识别产品中正在使用关键的开源项目
  * 大规模使用开源软件的公司对开源软件要谨慎选择、持续维护

## 业界开源安全实践洞察

### 开源社区安全：主流社区安全能力建设从突破单点安全技术，逐步发展到打造安全基础设施、供应链安全、整体安全架构的系统化防护体系

* 业界主流社区从单点安全特性逐步向整体安全架构、供应链安全和安全基础设施等系统化建设方向发展。

* 案例：Google在发布AOSP开源项目的时候，更多的使用的是传统的Linux安全能力。随着对安全的认知及安全观加强之后，开始创造一些原创的安全能力。

  * Linux：项目诞生（1991）--- 支持SELinux（2003）--- Syzkaller Fuzz关键（2016）----KSPP安全项目（2017）--- 任命供应链（2020）--- Sigstore签名服务（2021）
  * ASOP：项目诞生（2008) --- 漏洞致谢（2009）--- 支持SEAndroid（2014）---- 原生支持Fuzzing（2017)--- 奖励开源软件安全研究（2019）

  | 分类                   |          开源社区可借鉴点          |
  | ---------------------- | :---------------------------------------: |
  | 安全架构               |       单点安全技术---- 整体安全架构       |
  | 供应链安全             |       自身安全----上下游供应链安全        |
  | 安全基础设施(漏洞挖掘) |    单个漏洞奖励 ----漏洞挖掘等基础设施    |
  | 安全基础设施(安全开发) | 单一构建工具支持 ----安全开发基础设施支持 |

* 围绕开源件健康度和依赖度评估、漏洞感知与修复等系统化建设，是供应链安全发展的重点。

  * 开源软件存在的安全薄弱点：
    * 缺少安全Metadata（缺乏文档、LICENSE、反馈渠道、维护状况等）
    * 未做到默认安全（使用不安全的加密算法、协议、设计等）
    * 软件依赖链不明确（较难获知依赖链的安全状况）
  * 开源软件漏洞风险
    * 漏洞库信息缺乏（具体版本漏洞信息不准确）
    * 代码质量参差，存在漏洞风险（潜在漏洞数量多）
  * Google安全实践
    * 2020年布局 OpenSSF 社区 ，构建开源社区安全能力量化评估体系
    * 2021年发布OSI（Open Source Insights），建立开源软件依赖链信息库
    * 2021年发布OSV（Open Source Vulnerabilities），建立开源软件漏洞信息库，支持开源版本漏洞查询
    * 发布OSS-Fuzz平台及Patch奖励项目，提供Fuzz算力和修复资源，增强开源软件漏洞挖掘力量

### 开源选型：Google布局OpenSSF社区，制定开源软件安全评估体系，推动开源项目安全状况改善

对社区安全有评分，对社区的活跃度也有评分，从开源软件的角度，评分越高，也就意味着即使有一些开源软件漏洞，也会很快被软件开发者发现并修复。通过这些度量，可以让开发者或者开源软件使用方能理解这个社区是不是舍得被信赖，是不是一个可信的开源软件提供商，或者在选型时可以有的放矢地解决一些选型问题。

Security Scorecards项目：           

* 对开源项目的安全情况进行自动分析；       
* 推动改善关键项目的安全情况；        

| Name                   |                         Description                          |
| ---------------------- | :----------------------------------------------------------: |
| Binary-Artifacts       |         Is the project free of checked-in binaries?          |
| Branch-Protection      |           Does the project use Branch Protection ?           |
| CI-Tests               | Does the project run tests in CI, e.g. GitHub Actions, Prow? |
| CII-Best-Practices     |      Does the project have a CII Best Practices Badge?       |
| Code-Review            |                      CII-Best-Practices                      |
| Contributors           | Does the project have contributors from at least two different organizations? |
| Dependency-Update-Tool | Does the project use tools to help update its dependencies?  |
| Fuzzing                |      Does the project use fuzzing tools, e.g. OSS-Fuzz?      |
| Maintained             |                  Is the project maintained?                  |
| Pinned-Dependencies    |        Does the project declare and pin dependencies?        |
| Packaging              | Does the project build and publish official packages from CI/CD, e.g. GitHub Publishing ? |
| SAST                   | Does the project use static code analysis tools, e.g. CodeQL, SonarCloud? |
| Security-Policy        |         Does the project contain a security policy?          |
| Signed-Releases        |      Does the project cryptographically sign releases?       |
| Token-Permissions      | Does the project declare GitHub workflow tokens as read only? |
| Vulnerabilities        | Does the project have unfixed vulnerabilities? Uses the OSV service. |

Criticality Score项目：       

* 制定社区打分标准；       
* 筛选开源世界的关键项目列表；         
* 推动关键项目的安全改进；
            

| Parameter             | Weight | Max threshold | Description                                                 |
| --------------------- | :----: | ------------- | ----------------------------------------------------------- |
| created_since         |   1    | 120           | Time since the project was created (in months)              |
| updated_since         |   -1   | 120           | Time since the project was last updated (in months)         |
| contributor_count     |   2    | 5000          | Count of project contributors (with commits)                |
| org_count             |   1    | 10            | Count of distinct organizations that contributors belong to |
| commit_frequency      |   1    | 1000          | Average number of commits per week in the last year         |
| recent_releases_count |  0.5   | 26            | Number of releases in the last year                         |
| closed_issues_count   |  0.5   | 5000          | Number of issues closed in the last 90 days                 |
| updated_issues_count  |  0.5   | 5000          | Number of issues updated in the last 90 days                |
| comment_frequency     |   1    | 15            | Average number of comments per issue in the last 90 days    |
| dependents_count      |  0.5   | 500000        | Number of project mentions in the commit messages           |

### 开源选型：OSI项目提供统一的软件及依赖分析工具，结合高质量的数据，更好的洞察软件的健康度

* 2021年6月，Google发布OSI（ Open Source Insights）开源软件资产库，应对开源安全及合规挑战，其信息包括：安全建议、合规信息、软件依赖关系、安全及修复建议、OSSF ScoreCard等，软件组合分析能力需要积累的数据资产。
* 目前涵盖的开源资产：1.73M的NPM Packages；678k的Go Modules；418k的Maven Artifacts；68k的Cargo Creats； NuGet、PyPI的数据资产待发布。
* 借鉴：持续优化开源软件组合分析工具，构建漏洞精准定位和开源软件依赖解析能力，可视化开源软件的健康度

### 漏洞挖掘：Google构建并开放OSS-Fuzz平台、Github收购集成CodeQL等静态开源漏扫工具，赋能开源软件仓漏洞发掘

* Google开放大规模Fuzz平台，助力开源仓持续Fuzz，发掘和验证漏洞：
  * 开放OSS-Fuzz平台，将内部构建的ClusterFuzz能力开放给开源社区
  * 到2021年已被500个开源项目使用
  * 为开源软件提供集群服务器，以及自动化跟踪闭环的能力
* Github集成静态开源漏扫工具，赋能开源仓安全扫描、漏洞变种分析：
  * Github收购CodeQL工具，免费开放给开源代码仓使用，使用codebase查询语句进行变种分析，消除同一类型漏洞
  * Github集成sonarcloud等静态安全工具，助力开源仓持续集成安全扫描
* 借鉴：构建自己的开源软件集群Fuzz平台、优化静态安全扫描工具，提升挖掘开源软件漏洞的能力，减小开源漏洞攻击风险

### 开源漏洞管理：Google提供漏洞修复奖励加速开源软件漏洞修复；构建并开放开源软件漏洞数据库OSV，帮助开源软件使用者确认其版本是否存在漏洞

* Google提供漏洞修复奖励计划：
  * 鼓励开源软件维护者修复其维护的开源项目中的漏洞
  * 吸引第三方人员帮助修复开源软件漏洞
  * 通过Fuzz对修复补丁进行验证
* Google构建并开放开源软件漏洞数据库：
  * 提供API给开源软件使用者查询使用版本是否存在漏洞
  * 确认开源软件漏洞的引入和修复commit信息
  * 从多个源获取漏洞信息，包括Google自己的OSS-Fuzz
  * 目前，还没有将漏洞关联到CVE信息

### 开源供应链危机应对：面向全生命周期，采用工具+管理+安全增强特性等多方式组合看护供应链安全

整个研发流程之外，还有很多问题，比如，有一些恶意的开发者往社区投毒，近几年供应链安全投毒的安全事件逐渐增多，部分事件如SolarWinds影响巨大。

* 案例1：明尼苏达大学Linux内核投毒
  美国大学教授“故意”向Linux提交含Bug代码，内核管理员“封杀”明尼苏达大学。
  他通过Linux Curl做安全实验，通过机器生成一些不安全的代码和函数，然后不停地提交给社区，这些不安全地代码和函数如果不通过某些自动化工具，很难被识别。如果是面对一些不负责任或者安全意识不高或者相应专业能力不强的审核人员审核，很容易通过。当时很多新闻报道，最终虽然没有产生严重的后果，因为这个代码马上被发现退回。
  启示：如果不使用自动化工具或者使用更好的安全方法，面对所谓的投毒的恶意代码提交者，很难防范这个风险。
* 案例2：SolarWinds Orion 攻击事件
  *  攻击者篡改SolarWinds更新包代码将恶意代码插入DLL组件（SolarWinds.Orion.Core.BusinessLayer.dll)，该恶意动态链接库是攻击者主要篡改代码部分，具备执行各类攻击插件以及进行HTTP后门通信等功能。
  *  因直接攻击代码仓库，且代码写得高度整洁，被正常构建具备合法的数字签名证书。
     带有后门的更新包在官网上架：
     更新包名称为：CORE-2019.4.5220.20574-SolarWinds-Core-v2019.4.5220-Hotfix5.msp。
     该更新包具有SolarWinds合法的数字签名证书客户基于信任精神从官网下载和安装该恶意更新包。
  *  HTTP后门代码通过域名生成算法(DGA)，构造和解析avsvmcloud.com的子域，观察到的部分恶意域名。
  *  一旦通过对这些DGA域名（CNAME）进行解析，并成功检索到对应的域名，其会使用这些对应的域名进行C2通信;
  *  进行C2通信过程中，攻击者会根据攻击目标，从而发放不同的控制命令，从而执行对应的恶意代码功能。该后门代码会接收制定指令，指令包括收集系统信息、运行指定任务、写删读文件等等，通过写文件可以执行其他功能模块程序。

* 案例3：SolarWinds Orion 攻击事件
  * XCode官网下载慢，使攻击者有可乘之机，提供无Hash校验码(Xcode 6.4版本)恶意下载源。
  * MacOS上存在允许任何来源安装的选项。低版本Gatekeeper恶意软件检测机制可被绕过。

### 开源软件安全管理热点问题

总结：当前开源软件热门的安全管理事件，都是因为安全流程的疏忽，或者是没有使用相应的安全自动化工具，或者过多的让低技能甚至是不负责的代码审核者去审核这些代码而导致的各种安全问题，这些安全问题最终会因为开源软件的依赖和组件漏洞的关联导致进行一个广泛的传播，造成企业和个人的一些资产和信息的损失。

* 开源软件漏洞由POC披露到NVD首次公开时间长达11年
  * CVE-2009-4067 Linux 内核 USB缓冲区溢出漏洞
* 最主要的缺陷类型为：跨站脚本、内嵌的恶意代码、资源耗尽、信息暴露等
* 软件代码/制品仓中安全风险态势严峻：
  * Maven (Java) 数据量达650万+，Nuget (.NET) 累计下载930亿+，Rubygems （Ruby）累计下载 712亿+，PyPI (Python) 用户49万+，其余还有 Composor (PHP)、npm (JavaScript) 等。
  * 2020年新增漏洞数为3426，环比去年增长40%；近3年增长速度呈上升趋势，2020年新增漏洞数是2015年的4.48倍。
  * 对 Maven、NPM、PyPI 等仓库的删除、投毒攻击持续发生
* 组件漏洞存在广泛的依赖层级传播
