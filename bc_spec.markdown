# 区块链的技术细节

## 1. 文档目标    
阐述和分析包括R3，Digital Asset Holdings (DAH)，Chain.com等区块链软件公司在区块链（BlockChain）技术层面的细节，和Hyperledger Project的技术架构与一些细节。

## 2. 技术层面
###  2.1 R3CEV
#### 2.1.1 Corda的主要特点
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

Corda addresses these key points in distinct ways offering “different solutions for different problems.” Despite its focus on some of the same goals the team is “not building a blockchain” and they reject the idea that all data should be available to everyone. Brown explains that financial agreements between institutions need more than just a basic consensus mechanism.    

“We are not building a blockchain. Unlike other designs in this space, our starting point is individual agreements between firms (“state objects”, governed by “contract code” and associated “legal prose”). We reject the notion that all data should be copied to all participants, even if it is encrypted.” （我们不认同，即使在加密的情况下，所有的数据都需要在所有参与节点拷贝）
