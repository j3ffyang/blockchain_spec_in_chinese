# 区块链的技术细节

Disclaimer: the content in this document was collected from my personal idea and information from open source community, specially Hyperledger at Github.com and Linux Foundations.

# 目录    
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [区块链的技术细节](#区块链的技术细节)
- [目录](#目录)
	- [1. 文档目标](#1-文档目标)
	- [2. 技术层面](#2-技术层面)
		- [2.1. R3CEV](#21-r3cev)
			- [2.1.1. Corda的主要特点](#211-corda的主要特点)
			- [2.1.2. 开发在银行的业务场景](#212-开发在银行的业务场景)
			- [2.1.3. 反对的声音](#213-反对的声音)
			- [2.1.4. 技术团队主要成员](#214-技术团队主要成员)
		- [2.2 Chain.com推出Chain Open Standard](#22-chaincom推出chain-open-standard)
		- [2.3. DAH收购Elevence Digital Finance](#23-dah收购elevence-digital-finance)
	- [3. HyperLedger Project的技术架构](#3-hyperledger-project的技术架构)
		- [3.1. 框架](#31-框架)

<!-- /TOC -->

## 1. 文档目标    
阐述和分析包括R3CEV，Digital Asset Holdings (DAH)，Chain.com等区块链软件公司在区块链（BlockChain）技术层面的细节，和Hyperledger Project的技术架构与一些细节。

## 2. 技术层面
###  2.1. R3CEV
#### 2.1.1. Corda的主要特点
* Corda has no unnecessary global sharing of data: only those parties with a legitimate need to know can see the data within an agreement    
    Corda无需全网分享（账本）信息：只有在同一合约中和有合理需求的主体才可以看到

* Corda choreographs workflow between firms without a central controller    
    没有中心控制的工作流

* Corda achieves consensus between firms at the level of individual deals, not the level of the system    
    共识机制在合约个体之间，而非全网系统

* Corda’s design directly enables regulatory and supervisory observer nodes    
    设计涵盖合规法规的监管节点

* Corda transactions are validated by parties to the transaction rather than a broader pool of unrelated validators    
    交易的验证只发生在交易主体，而非无关的validators池

* Corda supports a variety of consensus mechanisms   
    支持多类型的共识机制    

* Corda records an explicit link between human-language legal prose documents and smart contract code    
    清晰记录，对应法律文件和智能合约代码

* Corda is built on industry-standard tools    
    标准设计    

* Corda has no native cryptocurrency    
    没有数字货币


Corda设计的五个维度： consensus（共识）, validity（交易验证）, uniqueness（唯一）, immutability（不可篡改）, and authentication（身份验证）

摘自R3CEV的CTO Richard Brown的blog:    

> Corda addresses these key points in distinct ways offering “different solutions for different problems.” Despite its focus on some of the same goals the team is “not building a blockchain” and they reject the idea that all data should be available to everyone.

Brown explains that financial agreements between institutions need more than just a basic consensus mechanism.    

> “We are not building a blockchain. Unlike other designs in this space, our starting point is individual agreements between firms (“state objects”, governed by “contract code” and associated “legal prose”). We reject the notion that all data should be copied to all participants, even if it is encrypted.” （我们不认同，即使在加密的情况下，所有的数据都需要在所有参与节点拷贝)    

#### 2.1.2. 开发在银行的业务场景    
[http://www.coindesk.com/r3-reveals-8-areas-of-focus-for-blockchain-bank-trials/](http://www.coindesk.com/r3-reveals-8-areas-of-focus-for-blockchain-bank-trials/)    
A consortium of over 40 financial institutions around the world is currently working on at least eight different proofs-of-concept (PoCs) to show how distributed ledgers can be used to streamline a wide range of transactions on Wall Street – and make them easier to regulate (更容易地监管).

####  2.1.3. 反对的声音    
According to the CEO of Overstock.com, Patrick Byrne, the new project is likely to slow down innovation within the bitcoin industry. The new consortium, he said, is just a means used by the Wall Street bankers to stifle innovation.

#### 2.1.4. 技术团队主要成员    
Name | Title and Background | Picture    
----|----|----    
James Carlyle | Chief Engineer, 来自Barclays | ![James Carlyle](img/20160508_jamescarlyle.png)    
Mike Hearn | Lead Platform Engineer, 来自Google和比特币社区 | ![Mike Hearn](img/20160508_mikehearn.png)
Ian Grigg | Cryptographer | ![Ian Grigg](img/20160508_iangrigg.png)
Tim Swanson | Head of Research 著有：Great Chain of Numbers | ![Tim Swanson](img/20160508_timswanson.png)    

### 2.2 Chain.com推出Chain Open Standard    
https://chain.com/os/    
与十家金融和电信企业协作，在2016年5月开发推出open- source并permissioned协议软件。    
取名：Chain Open Standard，或 Chain OS 1。    
产品目标：A Protocol（协议标准）for Financial Assets    
协作企业：Capital One, Citi, Fidelity, First Data, Fiserv, Mitsubishi UFJ, Nasdaq, Orange, State Street and Visa    

[http://www.coindesk.com/chain-open-standards-visa-citi-nasdaq-business/](http://www.coindesk.com/chain-open-standards-visa-citi-nasdaq-business/)    
“The Chain Open Standard is the product of a unique collaboration between some of the world's leading financial firms and a team of Silicon Valley engineers, cryptographers, and data scientists. We are designing a blockchain protocol by putting real financial use cases at the center of an iterative R&D process.”    
Chain.com Open Standard 是一款产品。它是由世界顶尖的金融公司和硅谷的工程师的独特组合，并且包括密码学家与数据科学家。我们正在设计一个BlockChain的在真实金融行业的标准。    

<!-- ![Chain.com Open Standard](img/chainos.png)    -->
<img src="img/chainos.png" width="550px"/>

* Assets Definition （资产定义）    
多维度签名，在交易流程中设定规范和限制    
<!-- ![Asset Definition](img/asset-def.png) -->
<img src="img/asset-def.png" width="350px" align="center">    

* 智能合约（案例之一。其他案例可以参考官方网站）    
![smartContract Payment](img/smartcontract_payment.png)    

* 私密 - one-time-use addresses, zero knowledge proofs, and encrypted metadata.    

* 数据标准(metadata)和数据模型(data model)    

* 无论文本，加密数据，和hashed数据全部可以追溯和审计    

* 针对合约，user-defined assets, 和 transactions with multiple inputs and outputs的优化    

* 共识机制- Simplified Byzantine Fault Tolerance (SBFT，简化拜占庭容错)

> 1. 首先一个block generator提交一个加入block的交易请求    
2. 其他block signers认可（ratify），并且签名    
3. 其他的network members在有足够signers数量的条件下，接受block的交易请求    
4. 生成新的block    
5. 交易结束。交易历史不可篡改     

(In SBFT, one designated block generator collects and validates proposed transactions, periodically batching them together into a new-block proposal. Other designated block signers ratify the proposed block with their signatures. All network members know the identities of the block signers and accept blocks only if signed by a sufficient number of signers. This ensures that competing transactions will be resolved, transactions will be final, and history cannot be rewritten.)

### 2.3. DAH收购Elevence Digital Finance    
[http://www.coindesk.com/digital-asset-acquires-elevence/](http://www.coindesk.com/digital-asset-acquires-elevence/)    

With the purchase deal, Digital Asset Holdings has also unveiled Digital Asset Modeling Language (DAML), the language developed for financial services as an alternative to Smart Contracts.    

During the past few months the startup has been working on integrating Elevence’s technology into its software. It will improve the company’s existing system by offering a new way to prove updates to a distributed ledger while keeping data private. Parties of the transaction don’t need to reveal the details of the agreement to third parties, as it can be processed only by the relevant participants.    
* DAH四月份收购瑞士的Elevence Digital Finance，主要编写证券，现金和衍生产品的智能合约
* 建立设置Digital Asset Modeling Language (DAML，数字资产模型语言)

## 3. HyperLedger Project的技术架构
### 3.1. 框架
<img src="img/bc_arch_overview.png" width="640px">
