<!-- Output copied to clipboard! -->

<!-----
NEW: Check the "Suppress top comment" option to remove this info from the output.

Conversion time: 5.437 seconds.


Using this HTML file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β29
* Sun Jun 13 2021 00:21:50 GMT-0700 (PDT)
* Source doc: XinFin Network-XDC Consensus Algorithm White Paper 05:04:21
* Tables are currently converted to HTML tables.
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

* Footnote support in HTML is alpha: please check your footnotes.

WARNING:
You have 8 H1 headings. You may want to use the "H1 -> H2" option to demote all headings by one level.

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 1; ALERTS: 11.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>
<a href="#gdcalert11">alert11</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>


<p>

    XinFin Network-XDC Consensus Algorithm White Paper (Updated)
</p>
<p>

    Updated on May 4th, 2021
</p>
<p>

    (edited for grammar, readability, consistency)
</p>
<p>

    XinFin (XDC) Hybrid Blockchain R&D Team
</p>
<p>

    XinFin Hybrid Blockchain Network 
</p>
<p>

    Email: info@XinFin.org
</p>
<h1 id="abstract">
    <strong>ABSTRACT</strong></h1>


<p>
In this paper, we present an overview of the architectural design of XinFin Network's consensus algorithm. XinFin Network is a public EVM (Ethereum Virtual Machine)-compatible blockchain with the following advantages: low transaction fees (near zero), low energy consumption, efficient confirmation time, double validation, and randomization for security guarantees. In particular, we propose XinFin’s Delegated Proof of Stake (XDPoS) consensus, a Proof-of-Stake (XDPoS)-based blockchain protocol with rigorous security guarantees and fast finality. We also present a novel reward mechanism - demonstrating that, with this mechanism, the blockchain has a low probability of forks and fast confirmation times. Additionally, the contributions and benefits of masternodes are fair and equitable, in the sense that the probability distribution function is uniform, eventually. As we go into details, explaining the motivation and double validation process as well as the finality checkpoint of the protocol, we also present the formalization of the XinFin model in a mathematical manner, demonstrating the soundness of the XinFin model and protocol. Lastly, we conduct a security analysis to examine the protocol’s ability to resist different attacks. Comparing the XinFin Network with several existing blockchains, we explain why XinFin Network’s consensus algorithm offers a more secure protocol.
</p>
<ol>

<li><strong>INTRODUCTION</strong>

<li><strong>Context</strong>
</li>
</ol>
<p>
Today, many companies use blockchain to drive greater veracity and transparency across their digital information ecosystems. And, they are boosting awareness of the blockchain industry and its accompanying infrastructure in a variety of sectors—ranging from consumer-packaged goods (CPG) to cloud computing and storage, and from infrastructure to public policy.
</p>
<p>
Building upon these developments, blockchain has surpassed initial forecasts based on its promise within the banking and cryptocurrency arenas. Worth noting: Funding to blockchain-based companies, despite dipping from 2018’s highs, more than doubled in 2020 as compared to 2017.<sup id="fnref1"><a href="#fn1" rel="footnote">1</a></sup> Moreover, forecasts predict that annual spending on blockchain solutions will exceed $16B in 2023—thanks to the increased adoption of blockchain-based ecosystems. 
</p>
<p>
To add, 2020 has branded its mark in history as a year of crypto institutionalization, with large multinationals (e.g., JPMorgan, PayPal, DBS) starting to offer crypto-based services. 
</p>
<p>
While blockchain was invented in 2008 by Satoshi Nakomoto, developments in blockchain ecosystems, today, have a striking semblance to the early years of the internet. During the inception years pioneers, dreamers, and early adopters came together to build the internet space we experience today. 
</p>
<p>
In the blockchain space, many pioneers, dreamers, and early adopters have introduced ground-breaking projects. XinFin is among these novel organizations. The XinFin Network is a pioneer in today’s establishment of blockchain ecosystem architecture. Leveraging the power of cryptographic tokens, XinFin interconnects an ecosystem of applications via a unique blockchain infrastructure that allows fast, frictionless and secure payment, and ensures reliable storage of value.
</p>
<p>
Powered by XDC Protocol, XinFin’s XDPoS Hybrid Network is a highly interoperable blockchain network supporting global trade and finance. Thanks to the XDPoS’ interoperability, the network permits digitization, tokenization, and swift settlement of trade transactions, increasing efficiency and reducing reliance on complex foreign exchange infrastructures. Operating as a blockchain agnostic middleware, the XinFin Network ensures flexibility in liquidity management by connecting MSME originators and decentralized liquidity pools.
</p>
<p>
Recently, XinFin received recognition from the World Trade Organization (WTO) for its hybrid protocol that supports permissionless ledgers for public verification and permissioned ledgers for restricted data sharing.<sup id="fnref2"><a href="#fn2" rel="footnote">2</a></sup> 
</p>
<ol>

<li><strong>XinFin’s Efficient and Secured Protocol</strong>
</li>
</ol>
<p>
Satoshi Nakamoto’s blockchain protocol attempted to achieve consensus within a permissionless setting—that is, anyone can join or leave the protocol execution without seeking permission from a centralized or distributed authority. Additionally, the protocol’s instructions weren’t dependent on the players’ identities, presenting a game-changing protocol architecture. Later, Ethereum and the Ethereum Virtual Machine (EVM), which were released in July 2015, proposed notable enhancements compared to the Bitcoin protocol. The Ethereum protocol introduced the smart contract functionality.
</p>
<p>
Whilst Bitcoin and Ethereum are game-changing technologies, they present a myriad of issues, especially with transaction processing performance. That said, to create an efficient and secured consensus protocol for the XinFin Network, the novel network tackles the following bottlenecks of classic blockchains.
</p>
<ul>

<li><strong>Transaction In-Efficiency</strong>
<p>

    Consortium blockchains, employed by leading cryptocurrencies like Bitcoin and Ethereum, experience a blockchain scaling problem. More specifically, they don’t scale well to handle large transaction volumes. Put into context: the fixed block size in the Bitcoin blockchain and gas prices in Ethereum cap their transactions per second (TPS) to 7 and 15, respectively. This small throughput severely hinders the wide-spread adoption of such cryptocurrencies.
</p>
</li>
</ul>
<ul>

<li><strong>Confirmation Times</strong>
<p>

    Network latency—the time required to generate an additional block of transaction in a chain or the time it takes for a transaction to appear on a blockchain—is a major issue of concern. For instance, Bitcoin’s 10-minute block-time is significantly longer than the average network latency. To add, Bitcoin blocks require 5 subsequent blocks to ensure confirmation. Thus, it takes close to an hour for transactions to receive confirmation. On the other hand, Ethereum, which has lower latency, has a relatively high block-time, around 13 minutes. These long confirmation times hinder the wide scale adoption of these classic blockchains in many smart contract applications.
</p>
<ul>

<li><strong>Fork Generation</strong>
<p>

    Fork generation—whether hard or a soft fork—is time-consuming, creates potential vulnerabilities, and consumes significant computational energy. In regards to vulnerabilities, fork generation exposes blockchain networks to costly attacks like Peer-to-Peer Network-based, Smart Contract-based, Consensus & Ledger-based, and Wallet-based attacks. In the past, Ethereum Classic, Bitcoin gold, Feathercoin, Vertcoin, Grin, and Verge blockchain networks suffered 51% attacks. (A 51% attack refers to an attack on Proof-of-Work (PoW) blockchain where attackers gain control of 51% or more of a networks’ hash rate). Given the vulnerabilities therein, private/permissioned blockchains are usually very resistant to possible forks of their blockchain.
</p>
<ul>

<li><strong>High Energy Consumption</strong>
<p>

    With classic blockchain networks, the Proof-of-Work (POW) consensus mechanism requires mining (computational power) to do proof-of-work computations. These transactions consume alarmingly large amounts of energy. To clarify, the current annual estimated energy consumption of Bitcoin mining activities is 87.17 terawatt-hours (TWh)<sup id="fnref3"><a href="#fn3" rel="footnote">3</a></sup> while the energy consumption of Ethereum is 29.41 TWh.<sup id="fnref4"><a href="#fn4" rel="footnote">4</a></sup><sup> </sup>Put into further perspective, as of 2017, Bitcoin mining activities consumed energy levels equivalent to Denmark’s energy consumption. With projections indicating that energy consumption in Bitcoin mining will soar by the year 2022, the POW consensus remains unsustainable. 
</p>
<ul>

<li><strong>Anonymous Network Node</strong>
<p>

    A transaction hash is a unique string of code that’s given to transactions that have been verified and added to a blockchain. With blockchain nodes playing an important part in transaction hashing, the anonymity of nodes—which store copies of the distributed ledger and maintain the reliability of the stored data—poses a problem. With governments seeking control of sensitive transactions, lack of government control, lack of regulatory authority, and maintaining pseudo-anonymity is a challenge. Notably, anonymous transactions may lead to misuse of blockchain technology, undermining government and regulatory activities. 
</p>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>
Motivated by the above-mentioned challenges, the XinFin Network proposes a consensus protocol that focuses on the following key strategies:
</p>
<ul>

<li>Double Validation to strengthen security and reduce likelihood of forks. 

<li>Randomization to guarantee fairness and prevent handshaking attacks.

<li>Fast confirmation time and efficient checkpoints for finality or rebase.

<li>Self-KYC layer while setting up Network Node. 
</li>
</ul>
<p>
To start dealing with these problems, this whitepaper presents an overview of the architectural design of XinFin Network’s masternodes. In particular, the paper proposes XinFin Delegated Proof of Stake (XDPoS) consensus, a Proof-of-Stake (PoS)-based blockchain protocol with rigorous security guarantees and fast finality. The white paper also presents a novel reward mechanism and demonstrates that with the POS mechanism, the blockchain can provide efficient confirmation times, and a low probability of forks. Additionally, the contributions and benefits of masternodes are equitable, in regards to the eventual uniformity of the probability distribution function. 
</p>
<ol>

<li><strong>Structure of The Paper. </strong>
</li>
</ol>
<p>
<strong>Section II-A</strong> Goes over the architectural design of the XinFin Network’s masternodes, framework, and background protocols that help mass readers (e.g., investors, traders, participants) absent the technical education to understand the network’s masternodes.<br><br><strong>Section II-B</strong> presents the XinFin masternode stakeholder policy, masternode committee, and reward and slashing mechanism. 
</p>
<p>
<strong>Section II-C</strong> explains the motivation and double validation process as well as the finality checkpoint of the protocol. 
</p>
<p>
<strong>Section II-D</strong> presents the formalization of XinFin Network’s architecture in a mathematical model to show the soundness of the model and the protocol. 
</p>
<p>
<strong>Section III</strong> discusses the security analysis and the systems resistance to potential attacks. 
</p>
<p>
<strong>Section IV</strong> discusses and compares the XinFin Network with several existing blockchains. 
</p>
<p>
<strong>Section V </strong>concludes the paper.
</p>
<h1><strong>II. XINFIN NETWORK Masternode DESIGN </strong></h1>


<h2><strong>A. The XinFin Network Architecture </strong></h2>


<p>
The XinFin Network consensus protocol or XinFin Delegated Proof of Stake (XDPOS) Consensus shown in Fig. 1 below, regulates the consistent production and maintenance of masternodes in the XinFin Blockchain. 
</p>
<p>
Masternode Parameters
</p>
<p>
    Suggested parameter values from requirements:
</p>
<p>
    MIN_STAKE: 10000000 XDC
</p>
<p>
    VALIDATOR_REWARD: NOS_masternode / TOTAL_REWARD
</p>
<p>
    REWARDS_TRANSFER: Every next block of epoch
</p>
<p>
    VALIDATOR_SET_SIZE: 108
</p>
<p>
    WITHDRAWAL_PERIOD: Set of Epoch (1 Epoch == 900 Blocks)
</p>
<p>
(Worth noting, there’s a proposal to increase the VALIDATOR_SET size to 144 after approval from the governance committee.)
</p>
<p>
Each XinFin masternode is a full node that holds XDC. For coin-holders to operate a masternode, 8 (eight) key requirements must be satisfied. These include:
</p>
<ul>

<li>More than 10,000,000 XDC held by the new masternode holder, helping them perform random delegated proof of stake consensus, seamlessly.

<li>A suitable wallet to store XDC tokens. Preferably in hardware form.

<li>A dedicated and stable hardware environment.

<li>A dedicated Static Public IP address.

<li>100% network uptime by IDC network.

<li>A minimum of tier 3+ IDC environment.

<li>Virtual Private Server (VPS). Though optional, this option is highly recommended.

<li>When using cloud-based services like Amazon EC2 M3, large virtual machine (VM) sizes are appropriate. Similar configurations are applicable for the Microsoft Azure Cloud network users.
</li>
</ul>
<p>
Given that the XinFin masternode is a full node, it stores a copy of the blockchain, produces blocks and keeps the chain consistent. These nodes are controlled by consortium members and come with a number of caveats. As previously noted, full nodes must purchase (and hold) a fixed equity of XDC (more than 10,000,000) to be able to host the full XDC protocol. This design introduces the advantage that no Full Node or groups of Full Nodes have control over the network. For node holders to possess more than 51% hashing power, a full node must acquire more and more XDC. With increased demand, XDC prices rise, making it financially impossible for a Full Node cartel to control the XinFin Network.
</p>
<p>
The XinFin Network also employs Double Validation complemented with a Randomization mechanism to prevent unscrupulous characters from gaining control of the network. With these techniques, the network reduces the probability of having invalid blocks in the blockchain, ultimately reducing its effectiveness. These enhancements and the components of the XinFin Network are explained in subsequent sections. 
</p>
<h2 id="b-stakeholders"><strong>B. Stakeholders.</strong></h2>


<h3 id="coin-holders-masternodes"><strong>Coin Holders, Masternodes</strong></h3>


<p>
Coin-holders are as simple as the name suggests: users who join the network and who own and transfer the required amount of XDC. It's worth noting that the XinFin Network doesn’t have miners as is with Proof-of-Work-based blockchain systems like Bitcoin and Ethereum. The XinFin Network employs a Proof-of-Stake (PoS)-based protocol.
</p>
<p>
On the XDPoS, only masternodes can produce and validate blocks. Once coin holders deposit 10 million XDC to the Smart Contract, they are listed as masternode candidates in the DApp. Masternodes that work consistently within the system creating and verifying blocks are incentivized with XDC. XinFin Network engineers take responsibility for designing this fair, explicit, automated, and accountable reward mechanism.
</p>
<p>


<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image1.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig. 1. XinFin Network Architecture
</p>
<p>
Since 108 masternodes are the maximum number in the masternode committee, masternode holders must deposit 10 million XDC to be considered for positions in the masternode committee. The amount (10,000,000 XDC) is locked in a smart contract. In the event that a masternode is demoted or intentionally resigns from the masternode, the candidate’s deposits are locked for 30 days and can be accessed thereafter.
</p>
<h3><strong>Reward Mechanism </strong></h3>


<p>
For each iteration of 900 blocks (called an epoch), a checkpoint block is created, which implements only reward works. The checkpoint block is referred to as the block signer. Tasked with storing all block signatures, block signers count the number of signatures sent to the block signer smart contract during the epoch. Rewards are based on the number of signatures linked to a masternode in an epoch.
</p>
<p>
In addition, block creators are selected in a circular and sequential order, allowing each masternode holder an equal opportunity to create and sign a block. In XDPoS's current implementation, failure of a masternode to create a block causes a 10-second delay before the next masternode in the sequence takes its turn to create the next block.
</p>
<p>
Further, there is a reward-sharing ratio among coin-holders and masternodes that have been elected via the support of coin-holders. Specifically, each epoch consists of 900 blocks, which receive a 250 XDC reward in the first 2 (two) years. The 250 XDC reward is divided among masternodes based on the number of signatures associated with the node in each epoch. Thereafter, masternode rewards are divided into three portions, namely:
</p>
<ul>

<li><strong>Infrastructure Reward:</strong>  This reward comprises the first portion of 40%. The reward goes to the masternode.
<ul>

<li><strong>Staking Reward:</strong> This reward accounts for 50% of the reward. The reward is shared proportionately amongst the pool of voters for a specific masternode. Token stake is the criteria used to share the reward amongst voters.
<ul>

<li><strong>Foundation Reward:</strong>  The foundation reward accounts for the last 10%. This reward is channelled into a special account that’s controlled by the masternode foundation. The foundation is initially run by the XinFin Network founding company.
</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>
Worth noting, coin-holders that un-vote prior to the check-out block don’t receive any rewards in the staking reward portion.
</p>
<h3 id="slashing-mechanism"><strong>Slashing Mechanism</strong></h3>


<p>
Slashing is an inbuilt mechanism for proof of stake blockchain protocols that seeks to discourage validator misbehaviour. Slashing incentivises node security, availability, and network participation.
</p>
<p>
On the XDPoS, underperforming masternodes dramatically decrease the performance capabilities of the entire network and cause instabilities. In XinFin’s Hybrid Network, failure by a masternode to create a block causes a 10 second delay. If a masternode has several turns (say <strong><em>M</em></strong> times) to produce a block within an epoch, the masternode causes more delays (that is <strong><em>M*10 sec</em></strong>). To mitigate the aforementioned problem, adoption of the slashing mechanism is key. XinFin’s slashing mechanism entails as follows: 
</p>
<p>
First, if a masternode fails to create a block during an epoch, the masternode is slashed for the 4 (four) subsequent epochs. Second, if more than one masternodes underperform, several changes occur in the treatment of the masternodes list for the next epoch. To specify, a masternode that’s considered to have underperformed within the past 4 epochs is considered as “kicked-out” and it loses the right to create blocks. At such times, the number of masternodes taxed with creating blocks falls below 108. At the same time, active masternodes do not wait the 10 seconds for the underperforming masternodes.
</p>
<p>
Once kicked out of XinFin’s masternode list, underperforming masternodes can still verify and sign blocks. This caveat is used to enable underperforming masternodes to notify other masternodes of their liveness. Nonetheless, underperforming masternodes don't receive rewards for verifying and signing off blocks after being slashed out.
</p>
<p>
To make the slashing process more effective, the XinFin Network employs both off-chain and on-chain slashing mechanisms. With the off-chain slashing, detection of misbehaviour is easier to implement, and it can be used for crafty characters. Within the contract is a <strong><em>reportBenign</em></strong> method (part of the Validator Set Contract) which only Validators can call, pass a message and a block-number. Slashing is executed if more than 2/3 of the Validators agree on the misbehaviour. Misbehaviours might include: validators consistently propagating blocks late or validators being offline for more than 24 hours. The slashing can be executed on portion of the stake—say 4%.
</p>
<p>
For the on-chain slashing, the process occurs when a validator signs-off two blocks with the same step—a condition known as equivocation. Once a validator node enters the wrong KYC detail, the contract includes a <strong><em>reportMalicious</em></strong> method. With the reportMalicious method only Validators can call, pass a message and a block-number. If more than 2/3 of the validators agree on the<strong><em> reportMalicious</em></strong>, a slashing will be executed. The process can slash a portion of the entire 100% stake of a Validator Node.
</p>
<h2><strong>C. XinFin Network Consensus Protocol </strong></h2>


<h3 id="motivation-for-xinfin’s-double-validation"><strong>Motivation for XinFin’s Double Validation</strong></h3>


<p>
On the XDPoS, Double Validation is motivated by the need for an additional trust-less validation layer that enhances security via a provable uniform distribution. The trust-less validation layer is achieved through decentralized randomization. To clarify, once a masternode creates a block, and before it’s added to XinFin’s blockchain, it’s mandatory that such a masternode is verified by a randomly selected set of masternodes. 
</p>
<p>
Leveraging Double Validation, XinFin’s hybrid protocol strengthens the network, improves XDPoS security, reduces possibilities for nothing-at-stake and fork attacks, and makes the hybrid blockchain unique among Delegated Proof-of-Stake-based blockchains.
</p>
<h3><strong>Double Validation Process </strong></h3>


<p>
Within the XinFin Network, masternodes have equal responsibility in running the network and keeping it stable. The network’s Full nodes (in this case masternodes) run on powerful hardware configurations and high-speed network connectivity, ensuring the required block time (estimated to be two seconds). 
</p>
<p>
Moreover, only masternodes can produce and seal blocks. For blocks to be produced and sealed, the XinFin Network consensus relies on the concept of Double Validation to improve the reliability of existing consensus mechanisms, namely Single Validation.
</p>
<p>
In the next section, we will cover XinFin’s Double Validation process, then analyse the differences and improvements of Double Validation compared to Single Validation. 
</p>
<p>
XinFin’s Double Validation (DV) is similar to some existing PoS-based blockchains such as Cardano. In the process, each block is created by a block producer. A block producer is primarily a masternode that takes its block creation permission turn following a pre-determined and circular sequence of masternodes in each epoch.<sup id="fnref5"><a href="#fn5" rel="footnote">5</a></sup> 
</p>
<p>
However, the DV process in the XinFin Network differs from the process in other blockchains. It’s worth noting that DV in the XinFin Network requires the signatures of two masternodes on a block for the block to be published on its blockchain. The block creator (first masternode) provides the first signature. The second masternode, which is the block verifier, is randomly selected among a set of voted masternodes to verify and sign a new block.
</p>
<p>
In subsequent sections—for a more convenient read—the terms ‘block creator’ and ‘block verifier’ are used interchangeably for masternode 1 (block producer) and the randomly selected masternode 2, respectively. The process of randomly selecting the block verifiers is detailed in the next paragraphs. Additionally, there is no mining in the block creation as demonstrated in Proof-of-Work-based blockchains (e.g., Ethereum and Bitcoin). This means that a created block is valid if, and only if, it is sealed by two signatures from a block creator and a corresponding block verifier that confirms its accuracy. 
</p>
<p>
At XinFin, there is a strong belief that the unique DV technique enhances the stability of the blockchain by diminishing the probability of producing ‘garbage’ blocks, while simultaneously maintaining the system security and consistency. Randomization of block verifiers in DV is a key factor in reducing risks associated with paired masternodes trying to commit malicious blocks. 
</p>
<p>
Additionally, comparing XinFin’s blockchain architecture with other blockchain setups indicates that there are significant advantages to the unique DV technique. Specifically, DV introduces improvements in block time by only requiring two signatures per block. In the interest of demonstrating how the XinFin Network has undergone enhancements, compared to existing PoS-based blockchains, the following figures analyze the differences between Double Validation and Single Validation mechanisms. The limitations in some existing blockchains serve to highlight the improvement introduced by Double Validation over Single Validation.
</p>
<p>
In Fig. 2 and Fig. 3 below, benefits introduced by DV as compared to SV are compared by analyzing some attack scenarios.
</p>
<p>


<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image2.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig. 2. Single Validation (SV): (a) SV with block creation masternode as an attacker and (b) SV with two consecutive block creation masternodes as attackers
</p>
<ul>

<li><strong>Single Validation</strong>
</li>
</ul>
<p>
In Single Validation and in an epoch, each masternode (e.g., M1 in figure 2.), sequentially takes its turn to create a block (e.g., block100). The next masternode (e.g., M2) in the sequence then validates the new block100. In the event that block100 is invalid (implying that M1 is potentially an attacker) and that the new block contains a transaction that invalidly benefits M1, an honest M2 rejects block 100 and creates a valid block 100 next to block 99 (see Fig. 2 [a].) 
</p>
<p>
However, if M2 is also an attacker (see Fig. 2 [b]) that cooperates with M1, M2 ignores the invalidation of block100, signs it, and creates the next block, namely block101 that is valid. Subsequently, if masternode M3 verifies the validity of block101, M3 signs block101 and creates a block102. This way, Single Validation potentially leaves the blockchain with ‘garbage’ or invalid blocks which require a ‘rebase’ to restore the validity of the blockchain. 
</p>
<ul>

<li><strong>Double Validation (DV)</strong> 
</li>
</ul>
<p>
With XinFin's DV technique, the likelihood of having garbage blocks in the blockchain is significantly reduced. In this case let’s assume that M1 and M2 are the block creator and block verifier of block100, respectively.
</p>
<p>
If block100 is invalid and M2 is honest (see Fig. 3 [a]), the next block creator M3, when creating block101, notes that block100 doesn't have the required number of signatures (two signatures in XinFin’s case), and thus, rejects block100 and creates another block100 next to block99. In the event that M2 is also an attacker pairing/handshaking with M1 (see Fig. 3 [b]), M2 signs block100 despite its invalidity. Worth noting is that XinFin’s block verifiers or M2 are randomly selected, therefore there is little chance of successfully pairing M1 and M2. This limits the possibility of invalid blocks being added to the blockchain. 
</p>
<p>
Next, even after M3 verifies that block100 has two valid signatures, M3 still rejects it because block100 is invalidated by M3 that will create another valid block100. To break the stability and consistency of XinFin’s blockchain, in this case, M3 should be an attacker together with M1 and M2. This scenario has a low probability of occurring since block verifiers are randomly selected. That said, DV strengthens the consistency of the blockchain and makes it hard to disrupt.
</p>
<p>


<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image3.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig. 3. Double Validation (DV): (a) DV with block creator as an attacker and (b) DV with both block creator and block verifiers as attackers
</p>
<h3><strong>Randomization for Block Verifiers for Double Validation</strong> </h3>


<p>
The First masternode or Block Creator: Within a given epoch, the first masternode/block creator(<em>v<sub>1</sub></em>) is selected by a round-turn game and it can be formally defined as an array.<sup id="fnref6"><a href="#fn6" rel="footnote">6</a></sup> The array’s formula is as follows: 
</p>
<p>


<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image4.png" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
       <strong><em> (equation: 1)</em></strong>
</p>
<h3 id="random-matrix-and-smart-contract"><strong>Random Matrix and Smart Contract</strong></h3>


<p>
To select random verifiers for a subsequent epoch (<strong><em>e+1</em></strong>), 3 (three) steps are followed. To understand the three steps explained below, let <strong><em>m</em></strong> be the number of masternodes, <strong><em>n</em></strong> be the number of slots in an epoch. 
</p>
<h4 id="step-1-random-numbers-generation-and-commitment-phase"><strong>Step 1: Random Numbers Generation and Commitment Phase</strong></h4>


<p>
First,<strong> </strong>at the beginning of epoch <strong><em>e</em></strong>, each masternode <strong><em>Vi </em></strong>creates an array of <strong><em>n + 1 </em></strong>special random numbers<em> <strong>Recommendi = [ri.1, ri.2, ..., ri. n, θi]</strong></em>, where <strong>ri. k ∈ [1, ..., m] </strong>indicates the recommendation of an ordered list of block verifiers for the next epoch of <strong><em>Vi</em></strong>, <br>and <strong>θi ∈ {−1, 0, 1}</strong> is used for increasing the unpredictability of the random numbers.
</p>
<p>
Second, each masternode <strong><em>Vi</em></strong> has to encrypt the array <strong><em>Recommendi</em></strong> using a secret key SKi, say<strong> Secreti = Encrypt (<em>Recommendi</em>, SKi)</strong> as the encrypted array. Next, each masternode forms a “lock” message that contains encrypted array Secreti, signs off this message with its blockchain’s private key through the Elliptic Curve Digital Signature Algorithm (ECDSA) scheme that’s currently used in Ethereum and Bitcoin along with the corresponding epoch index and its public key generated from its private key. After forming a “lock” message and signing off the message via the ECDSA verifiable key, every masternode can check who created this lock message through ECDSA verification scheme and which epoch it relates to. Thereafter, each node <strong><em>Vi</em></strong> sends their lock message with its signature and public key to a Smart Contract stored in the blockchain. The process enables each masternode to collect and know the locks from all other masternodes.<sup id="fnref7"><a href="#fn7" rel="footnote">7</a></sup>
</p>
<h4 id="step-2-recovery-phase"><strong>Step 2: Recovery Phase</strong></h4>


<p>
The recovery phase is for every node to reveal its previous lock message so other nodes can get to know the secret array it has sent before. A masternode only starts revealing its lock message if all masternodes have sent their lock messages to the smart contract or a certain timeout event occurs. Each masternode then opens its lock message by sending an “unlock” message to the smart contract for other masternodes to open the corresponding lock. Let’s imagine a commitment-like scheme, in this case, where a lock message is a commitment message locking its contained recommendation array <strong><em>Recommendi</em></strong> so that no one can open or guess the contained array, and the unlock message gives the key for other masternodes to decrypt the box and retrieve the values of <strong><em>Recommendi</em></strong>. Eventually, a masternode has both locks and unlocks to other masternodes. If some elector is an adversary which might publish its lock but not intend to send the corresponding unlock, other masternodes can ignore the adversary’s lock and set all its random values be 1, by default. The idea is simple: the network can keep working successfully even if some masternodes are adversaries. 
</p>
<h4 id="step-3-assembled-matrix-and-computation-phase"><strong>Step 3: Assembled Matrix and Computation Phase</strong></h4>


<p>
At the point of the slot <strong><em>n<sup>th</sup></em></strong> of the epoch <strong><em>e</em></strong>, the secret arrays Secreti in the smart contract will be decrypted by each masternode and return the plain version of Recommendi. Each tuple of the first n numbers of each<strong><em> Vi</em></strong> will be assembled as the<strong><em> i<sup>th</sup></em> </strong>column of an<strong><em> n × m</em></strong> matrix. All the last number<strong><em> θi </em></strong>forms a <strong><em>m × 1</em></strong> matrix. Then each node will compute the block verifiers ordered list by some mathematical operations as explained below. The resulting output is a matrix <strong><em>n × 1</em></strong> indicating the order of block verifiers for the next epoch <strong><em>e + 1</em></strong>.
</p>
<p>
For the second masternode or block verifier, each node computes the common array <strong><em>ν<sub>2</sub></em></strong> for the order of the block verifiers by the following steps as in Equation 1.
</p>
<p>


<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image5.png" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
(<strong><em>equation: 2</em></strong>)
</p>
<p>


<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image6.png" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
(<strong><em>equation: 3</em></strong>)
</p>
<p>
Then, <strong>ν<sub>2</sub></strong> is obtained by modulo operation of element values of ν 0 2 as in Equation 2:
</p>
<h3><strong>Finality Analysis  </strong></h3>


<p>
A standard definition of “total economic finality”: A phenomenon occurring when ¾ (three quarters) of all masternodes make maximum-odds bets that a given block or state will be finalized. This condition offers very strong incentives for masternodes to never attempt colluding to revert a block. When masternodes make such a maximum odds bet, in any blockchain where that block or state is not present, the masternodes lose their entire deposit.<sup id="fnref8"><a href="#fn8" rel="footnote">8</a></sup><br>
</p>
<p>
XinFin Network maintains this standardization in the design so that one block is considered as irreversible if it collects up to three-quarters of the signatures of all members in the masternodes committee. The time-line of the blockchain creation process, checking finality, and marking the block as immutable are described in Figure 4 below. 
</p>
<p>


<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image7.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig. 4. Timeline of Blockchain Making Process
</p>
<h2><strong>D. Consensus Protocol: Formalization </strong></h2>


<h3><strong>Basic Concepts & Protocol Description </strong></h3>


<p>
To provide a solid educational foundation and to prove that the XinFin Network can achieve its claims, in the following section, we will present a preliminary examination of the concepts discussed in our yellow paper and an overview of XinFin Delegated Proof of Stake (XDPoS).
</p>
<p>
To start, we will provide a presentation of XinFin’s proof of stake consensus algorithm. The formalization follows that of notable tokens, such as Cardano and Thunder, in recent literature. More specifically, XinFin places emphasis on the following concepts and definitions that were presented in literature for Cardano and Thunder tokens and adapts them to the context of XinFin Network.
</p>
<h3><strong>Time, Slots, Epoch </strong></h3>


<p>
Ideally, each epoch is divided into 900 block times. Each of these block times is referred to as a block slot. Only one block can be created in a slot. The main assumption is that there is a roughly synchronized clock that allows for masternodes to learn the current slot. This simplification effectively permits masternodes to execute the signing and validation process of the XDPoS consensus, where each masternode must collectively create a block to the current slot. Simplified further, each slot SLR is accessed by an integer <strong>r ∈ {1, 2, ...}</strong>, and is supposed that the real-time window that corresponds to each slot has the following properties, which are similar to what is specified in Cardano.<sup>6</sup> 
</p>
<ol>

<li>Every masternode can determine the index of the current slot based on the current time. And, any discrepancies between parties’ local time are insignificant in comparison with the length of time represented by a slot. 
<ol>

<li>The amount of a slot time is sufficient to guarantee that any message transmitted by an honest party at the beginning of the time window will be received by any other honest party by the end of that time window. While similar to Cardono’s assumption, the XinFin Network adopts the assumption to ensure that block creators seamlessly propagate their created blocks to the corresponding block verifiers. This guarantees a block is signed by both the masternodes before the next block creator builds another block on top of it.
</li>
</ol>
</li>
</ol>
<p>
As mentioned in Section II-A, in XinFin’s setting, it's assumed that the fixed set of <strong><em>m</em></strong> (150) masternodes <strong>V1, V2, ...., Vm</strong> interacts throughout the protocol to reach the consensus. For each <strong><em>Vi</em></strong>, a public/private key pair <strong>(PKI, ski)</strong> for a prescribed signature scheme, ideally ECDSA, is generated. 
</p>
<p>
Additionally, XinFin’s protocol adopts the assumption that the public keys <strong>pk<sub>1</sub>, ..., pk<sub>m</sub></strong> of the masternodes are distributed and known by all masternodes in the protocol (that means a masternode knows all public keys of all other nodes). Some notable definitions of the blockchain concepts are defined following the notation. 
</p>
<p>
<strong>Definition 1 (State):</strong>
</p>
<p>
A state is an encoded string <strong>st ∈ {0, 1} </strong>
</p>
<p>
<strong>Definition 2 (Block):</strong>
</p>
<p>
A block B generated at a slot sli contains the current state <strong>st ∈ {0, 1} λ, data d ∈ {0, 1} ∗</strong>, the slot number <strong><em>i</em></strong> and a signature <strong>Σ = Signski (st, d, sli)</strong> computed under ski corresponding to the masternode Vi generating the block
</p>
<p>
Algorithm 1: The algorithm illustrated the consensus protocol 
</p>
<p>
Input: <strong><em>m</em></strong> - Number of masternodes, <strong><em>n</em></strong> number of slots in an epoch 
</p>
<p>
Output: The complete ledger of the blockchain C 
</p>
<p>
To create the complete ledger for block C, several steps must be completed. These are as follows: <strong>(a)</strong> Creating the empty blockchain (stack) C <strong>(b)</strong> Commencing an Initial Coin Offering (ICO) to raise funds to support the provision of cryptocurrencies and blockchain-related products and services <strong>(c)</strong> Issuance of tokens/coins to holders. These tokens do not provide equity stake, rather they deliver their owners some stake in a product or service created by the company and<strong> (d)</strong> Voting for the masternode committee (masternodes) <strong>VC ← {V1; V2; ..., Vm}</strong>.
</p>
<p>
 
</p>
<p>
Thereafter, <strong>(e)</strong> Initiate the first epoch <strong>e<sub>1</sub> ← {sl<sub>1</sub>, sl<sub>2</sub>, ..., sl<sub>n</sub></strong>};<strong>(f)</strong> Randomly generate the array of second masternodes for the first epoch <strong>SV1 ← [v <sub>1 2.1</sub>, v<sub>1 2.2</sub>, ..., v<sub>1 2. n</sub>]</strong>; <strong>(g) </strong>Create the genesis block B<sub>0</sub>; <strong>(h</strong>) Update the blockchain <strong>C ← C. push(B<sub>0</sub>)</strong>; while true do while j is less than n to create block B<sub>j </sub>by the first masternode; Update the blockchain C<strong> ← C. push (B<sub>j</sub>)</strong>; 
</p>
<p>
Then, step <strong>(i)</strong> validate the block Bj by the second masternode; <strong>(j) </strong>broadcast and validate the block B<sub>j</sub> by VCi; if Bj has more than 3/4 masternode committee members’ signature then FINALITY(Bj .ID) = true; if j = n then j ← 1; else j++; if len(C) mod n = 0 then doCheckpoint(); Voting for the masternode committee for the next epoch <strong>VC ← {V1; V2; ..., Vm}</strong>; Random generate the array of verifier masternodes for the next epoch <strong>(i + 1)th; SVi+1 ← [v i+1 2.1 , vi+1 2.2 , ..., vi+1 2.n ]; ei+1 ← i ∗ n ∗ 2 + e1; i++</strong>;
</p>
<p>
Here’s a pictorial summary of the process:
</p>
<p>


<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image8.png" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
<strong>Definition 3 (Blockchain):</strong>
</p>
<p>
A blockchain C is a sequence of blocks <strong>B<sub><em>1</em></sub>, ..., B<sub>n</sub></strong> associated with a strictly increasing sequence of slots for which the state sti of <strong>B<sub>i</sub> </strong>is equal to H(Bi−1), where H is a collision-resistant cryptography hash function. To add, a blockchain has a number of properties, including the length of a chain len(C) = n, which is its number of blocks, and the block B<sub>n</sub> is the head of the chain, denoted head(C).
</p>
<p>
As mentioned earlier, in the XinFin Network model, each time slot <strong><em>sli  </em></strong>is set<strong><em> </em></strong>as 2 seconds and an epoch is a set as <strong><em>R</em></strong> of 900 slots <strong><em>{sl<sub>1</sub>, sl<sub>2</sub>, ..., sl<sub>900</sub></em></strong>}.  The duration of an epoch equals 1800 seconds. In summary, the consensus protocol of XinFin Network consensus can be formalized in Algorithm 1. Algorithm 1 is simulated and explained as a process shown in Fig. 5
</p>
<p>


<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image9.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig. 5. Randomization of Block Verifiers, Creating and Validating Blocks in Each Epoch
</p>
<h1><strong>III. SECURITY ANALYSIS </strong></h1>


<ol>

<li><strong>Nothing-at-stake</strong> 
</li>
</ol>
<p>
Nothing-at-stake is a well-known problem in PoS-based blockchain, just like the 51% attack in PoW algorithms. For PoW-based miners, it’s mandatory to have CapEx (capital expenditures) for buying mining equipment such as ASICs. Similarly, there's a need for OpEx (operation expenditures) such as electricity to solve mathematical puzzles securing the network. That means, there is always an intrinsic cost for miners in mining regardless of its success. In case of a fork, miners therefore always allocate their resource (equipment) to the chain that they believe is correct in order to get incentives for compensating the intrinsic costs in mining. 
</p>
<p>
On the contrary, PoS-based systems don't rely on mining. During an ideal execution creating a fork, the only costs incurred relate to block validation and signing. That is because masternodes do not incur intrinsic costs. In this case, there’s an inherent problem of the masternode having no downside to staking both forks. Therefore, there are actually two issues in the original design of PoS. On one hand, for any masternode, the optimal strategy is to validate every chain/fork, so that the masternode receives its rewards no matter which fork wins. On the other hand, for attackers/malicious masternodes, they can easily create a fork for double spending.
</p>
<p>
The XinFin Network handles these two problems exceptionally. (Note: Through the XinFin Network consensus protocol, the XinFin Network maintains a certain order of masternodes in creating and sealing blocks during each epoch).
</p>
<p>
For the first issue, random/arbitrary forks never happen because block creation by the masternodes is predetermined in each epoch. For the second issue, the Double Validation mechanism ensures that only one block can be validated by the second randomly selected masternode. That’s even when one malicious masternode creates two blocks at its turn.
</p>
<ol>

<li><strong>Long-range attack </strong>
</li>
</ol>
<p>
Within the XinFin Network, a block is valid only if it collects Double Validation and is finalized once 3/4 of masternodes verify. Therefore, as long as the number of attackers or malicious nodes and/or fail-stop nodes is less than or equal to 1/4 the number of masternodes, the number of masternodes signing a block is at least 3/4 the total number of masternodes, which makes the block finalized. 
</p>
<p>
Thus, there is no chance for one malicious masternode to create a longer valid chain on the XinFin Network because other masternodes will reject the new block.
</p>
<ol>

<li><strong>Censorship Attack </strong>
</li>
</ol>
<p>
In the event that there are more than 3/4 malicious masternodes in the XinFin Network, censorship attacks may occur. For example, if the malicious masternodes refuse valid blocks or simply become inactive, the chain is stuck. To avoid censorship attacks, masternodes are paid for their effort of correctly working so that the chain is actively updated in a consistent manner. 
</p>
<p>
More importantly, becoming a masternode means a certain number of coins is locked —10,000,000 XDC in this case. Therefore, to control more than 3/4 masternodes, attackers must hold a considerable amount of XDC and gain substantial support from coin-holders. Given the inhibiting cost, the attackers do not have incentives to engage in any malicious activity that could harm the chain
</p>
<p>
However, in the worst-case scenario, XinFin Network can conduct a soft fork to reduce the number of masternodes, keeping the chain running and figuring out slasher mechanisms to weed out the malicious masternodes.
</p>
<ol>

<li><strong>Relay Attack  </strong>
</li>
</ol>
<p>
The XinFin Network supports EIP155. The EIP-155 provides unique identifiers to a blockchain helping it overcome relay attacks. With EIP-155, two conditions are met: (a) definition of an integer for Chain-id for a blockchain and (b) signing of a <strong><em>chain-id</em></strong> into a transaction data. This prompts attackers to send the same transaction to different blockchains. With specifications in the EIP-155, blockchains have to define a <strong><em>chain-id</em></strong> and register the <em>chain-id</em> in a public repository.<sup id="fnref9"><a href="#fn9" rel="footnote">9</a></sup>
</p>
<p>
A challenge for using an integer for chain-id is that it’s not broad enough to cover all blockchains and it doesn't prevent the use of the same <strong><em>chain-id</em></strong> by different blockchains. Furthermore, using an integer fails to address issues introduced by two forked blockchains having the same <strong><em>chain-id</em></strong>. In this context, the XinFin Network has adopted a more robust blockchain identifier that overcomes these drawbacks, especially for cross chain operations where multiple chains are involved thus providing extensive protection against relay attacks. 
</p>
<p>
With the XinFin Network, the process through which a transaction id is made unique is as illustrated with the following example: 
</p>
<p>
Consider a transaction with: <strong>nonce = 9, gas price = 20 * 10**9, start gas = 21000, to = xdc3535353535353535353535353535353535353535, value = 10**18, data='' (empty).</strong>
</p>
<p>
Once signed the “signing data" becomes:
</p>
<p>
<strong>0xec098504a817c800825208943535353535353535353535353535353535353535880de0b6b3a764000080018080</strong>
</p>
<p>
And, the "signing hash" becomes:
</p>
<p>
<strong>0xdaf5a779ae972f972197303d7b574746c7ef83eadac0f2791ad23db92e4c8e53</strong>
</p>
<p>
In the event that a transaction within the XinFin Network is signed with a private key like <strong>0x4646464646464646464646464646464646464646464646464646464646464646</strong>, then the v, r, s values would be:
</p>
<p>
<strong>(37, 18515461264373351373200002665853028612451056578545711640558177340181847433846, 46948507304638947509940763649030358759909902576025900602547168820602576006531)</strong>
</p>
<p>
With the use of 37 instead 27 in the v, r, s values, the signed Tx would become:
</p>
<p>
<strong>0xf86c098504a817c800825208943535353535353535353535353535353535353535880de0b6b3a76400008025a028ef61340bd939bc2195fe537567866003e1a15d3c71ff63e1590620aa636276a067cbe9d8997f761aecb703304b3800ccf555c9f3dc64214b297fb1966a3b6d83</strong>
</p>
<p>
Within the XinFin Network, a cross chain-id can be used to present a relay attack. Notably, applications handling cross chain transactions can verify cross <strong><em>chain-id</em></strong> via their block hash and decide whether the transaction is valid or not. Transactions without a verifiable cross <em>chain-id</em> are rejected. In effect, EIP-155 specifications provide a robust approach to preventing relay attacks.
</p>
<p>
Table 1 shows chains and <strong><em>chain-ids</em></strong> recognized on the network.
</p>
<p>
TABLE 1
</p>
<p>
CHAINS AND CHAIN_ID
</p>

<table>
  <tr>
   <td>CHAIN ID
   </td>
   <td>Chain(s)
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td>Ethereum mainnet
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td>Morden (disused), Expanse mainnet
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td>Ropsten
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td>Rinkeby
   </td>
  </tr>
  <tr>
   <td>30
   </td>
   <td>Rootstock mainnet
   </td>
  </tr>
  <tr>
   <td>31
   </td>
   <td>Rockstock testnet
   </td>
  </tr>
  <tr>
   <td>42
   </td>
   <td>Kovan
   </td>
  </tr>
  <tr>
   <td>61
   </td>
   <td>Ethereum Classic mainnet
   </td>
  </tr>
  <tr>
   <td>62
   </td>
   <td>Ethereum Classic testnet
   </td>
  </tr>
  <tr>
   <td>1337
   </td>
   <td>Geth private chains (default)
   </td>
  </tr>
  <tr>
   <td>77
   </td>
   <td>Sokol, the public POA Network testnet
   </td>
  </tr>
  <tr>
   <td>99
   </td>
   <td>Core, the public POA Network main network
   </td>
  </tr>
  <tr>
   <td>50
   </td>
   <td>XinFin Mainnet
   </td>
  </tr>
  <tr>
   <td>51
   </td>
   <td>XinFin Testnet
   </td>
  </tr>
</table>


<ol>

<li><strong>Safety and Liveness</strong> 
</li>
</ol>
<p>
A consensus protocol is considered live if it can eventually propagate and make valid transactions onto the blockchain. A liveness fault occurs when transaction omission, information withholding, or message reordering, among a number of violations are observed. This type of fault is unlikely to happen in XinFin Network because the block creation masternodes list is ordered in a predetermined way for each epoch, thus if even an attacking masternode omits some transactions, the latter will be processed and validated by the next honest masternode in the next block.
</p>
<p>
Furthermore, safety implies having a single agreed upon chain where there are not two or more competing chains with valid transactions in either chain. As such, consensus protocols are safe when blocks have settlement finality, or else probabilistic finality. The XinFin Network provides safety because it has a settlement finality.
</p>
<p>
To note, XinFin Network has implemented the Istanbul Byzantine Fault Tolerant (IBFT) consensus mechanism. The IBFT consensus mechanism ensures instant finality, higher throughput, manageable validator set, and a high Transaction Per Second (TPS) rate.<sup id="fnref10"><a href="#fn10" rel="footnote">10</a></sup> 
</p>
<p>
With the IBFT consensus mechanism, the XinFin Network introduces several benefits guaranteeing the network's safety and liveness. First, the XinFin Network—via the IBFT—guarantees immediate block finality. That is because only 1 block is proposed at a specific chain height. Thus, the single chain removes forking, prevents uncle blocks, and the risks that a transaction may be “undone” once on the chain at a later date. It’s worth noting that XinFin’s MyContract—a next generation smart-contract platform—will be IBFT compliant, enabling the consensus to scale up to 2500 TPS. 
</p>
<p>
Second, the IBFT consensus mechanism reduces times between blocks. This occurs by effectively reducing efforts needed to construct and validate blocks, increasing the throughput of the network. Third, with the IBFT consensus, the XinFin Network ensures high data integrity and fault tolerance. To clarify, the IBFT employs a group of validators to ensure the integrity of each block being proposed. Plus, a super majority (66%) of the validators are required to sign a block Byzantine, which is inserted to the chain, making block forgery very difficult. Thirdly, the IBFT consensus mechanism guarantees operational flexibility. Notably, the ‘leadership’ of the network's validators rotates over time, preventing faulty nodes from exerting long-term influence over the chain, introducing undesirable liveness and safety issues.<sup id="fnref11"><a href="#fn11" rel="footnote">11</a></sup>
</p>
<ol>

<li><strong>DDOS Attack </strong>
</li>
</ol>
<p>
Distributed denial of service (DDoS) attacks occur when malicious characters overwhelm the target or the related infrastructure with malicious traffic. Employing networks of malware compromised computers, bots, and other devices, an attacker remotely controls the target infrastructure. DDOS adversary affects the bandwidth and connectivity leading to the disruption of services on a network. To add, cloud-based ecosystems suffer significant losses since DDOS causes service degradation and in some cases complete service denial.
</p>
<p>


<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image10.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image10.jpg" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig.6.Distributed denial of service (DDoS) attack.<sup id="fnref12"><a href="#fn12" rel="footnote">12</a></sup>
</p>
<p>
In the context of the XinFin Network, masternodes are required to run on reputable public cloud providers like AWS, Microsoft Azure or Google Cloud, which provide multiple DDOS prevention mechanisms. When some nodes are attacked or fail-stop, the network still operates correctly as long as the number of failing and/or attacked nodes remains less than 1/4 of the number of masternodes.
</p>
<ol>

<li><strong>Spam Attack </strong>
</li>
</ol>
<p>
XinFin Network keeps the same transaction fee mechanism as Ethereum which employs gas prices.<sup id="fnref13"><a href="#fn13" rel="footnote">13</a></sup>(Gas refers to the unit that measures the amount of computational effort required to execute specific operations on the Ethereum network).<sup id="fnref14"><a href="#fn14" rel="footnote">14</a></sup> However, the XinFin Network supports a minimum transaction fee (1 wei--approx. 1/100 the gas price of Ethereum). Concerns have been raised on the likelihood of spamming given that attackers try to broadcast a huge amount of low fee transactions to the system. To deter spamming attacks, however, the XinFin Network’s masternodes always sort transactions and pick up only high fee transactions into the proposing block. Thus, spammers have little chance of harming the system.
</p>
<h1><strong>IV. RELATED WORK </strong></h1>


<p>
Consensus plays an important role in guaranteeing the success of distributed and decentralized systems. Bitcoin’s core consensus protocol, often referred to as the Nakamoto consensus, realizes a “replicated state machine” abstraction. In the abstraction, nodes in a permissionless network reach agreement about a set of transactions committed as well as their ordering.<sup id="fnref15"><a href="#fn15" rel="footnote">15</a></sup> However, known permissionless consensus protocols such as Bitcoin’s Nakamoto consensus come at a cost. Bitcoin and Ethereum rely on PoW to enforce, albeit roughly, the idea of “one vote per hash power” and to defend against Sybil attacks. 
</p>
<p>
Unfortunately, PoW-based Bitcoin and Ethereum are known to have terrible performance (Bitcoin’s transaction processing performance is at peak of around 7 transactions per second as previously mentioned). Moreover, PoW is much criticized because it costs a lot in terms of electric energy consumed.
</p>
<p>
 
</p>
<p>
XinFin’s XDC Network Consensus is able to achieve 99% less energy consumption compared to Proof of Work based networks like Bitcoin or Ethereum. Data generated from XinFin’s 140 Validators nodes power usage is compared to that of Bitcoin and Ethereum in Figure 7 below. 
</p>
<p>


<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image11.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image11.png" width="" alt="alt_text" title="image_tooltip">

</p>
<p>
Fig.7. Comparison of Energy Consumption between Bitcoin, Ethereum and XinFin XDC Network. 
</p>
<p>
To design an efficient and cost-effective consensus protocol in the permissionless model, PoS has been discussed extensively in the Bitcoin and Ethereum forum. A PoS blockchain can substitute the costly PoW in Nakamoto’s blockchain while still providing similar guarantees in terms of transaction processing in the presence of a dishonest minority of users (this “minority” is to be understood here in the context of stake rather than computational power.) The Ethereum design, Casper, published by Buterin & Griffith, provides as its initial version a PoW/PoS hybrid consensus protocol, which might eventually switch to a pure XDPoS system. As with the XinFin Network, Ethereum Casper requires that validators (similar to block creators) deposit a specified amount of ETH — a concept similar to that used in the XinFin Network.
</p>
<p>
XinFin’s Delegated Proof of Stake (XDPoS) consensus protocol, proposed in this paper, can be seen as a hybrid model. In particular, XinFin applied XDPoS with Double Validation to create and verify blocks smoothly and efficiently. Whenever potential fork branches are detected, XinFin employs the concept PoW to select the longest branch and then discard the other branches. With this hybrid approach, XDPoS does not only increase the performance and security of the blockchain, but it also reduces forks in an efficient and practical manner.
</p>
<p>
Recently, there are several consensus protocol research works that are closely related to XinFin Network such as EOS and Ouroboros of Cardano. The mechanism of relying on masternodes to reach consensus is utilized by Bitshares and EOS, whose consensus protocol is termed Delegated Proof-of-Stake (DPoS). This DPoS is similar to the XinFin Delegated Proof of Stake consensus in the XinFin Network. Both systems are similar in the sense that masternodes (block creators or witnesses in DPoS) are elected through a voting system.<sup id="fnref16"><a href="#fn16" rel="footnote">16</a></sup> However, XinFin Network requires that masternodes need to deposit a required minimum amount of XDC to become a masternode candidate, which puts more pressure on masternodes to work honestly. Furthermore, the Double Validation mechanism of XinFin Network lowers the probability of handshaking attacks and having invalid blocks, as previously analyzed. EOS also has a maximum of 21 block producers for each epoch, which is less decentralized than XinFin Network with a maximum of 108 masternodes.<sup id="fnref17"><a href="#fn17" rel="footnote">17</a></sup><sup>,</sup><sup id="fnref18"><a href="#fn18" rel="footnote">18</a></sup>
</p>
<p>
The research-backed Cardano blockchain solution, namely Ouroboros, with the ADA coin, which is purely based on Proof-of-Stake, promises to provide rigorous security guarantees. Similar to the XinFin Network, Ouroboros has a set of block producers for each epoch creating blocks in a given sequence. Additionally, each block producer candidate needs to deposit a minimum amount of stake (an amount of ADA).<sup id="fnref19"><a href="#fn19" rel="footnote">19</a></sup> Worth noting, however, is that Ouroboros only provides Single Validation, while the XinFin Network carries out Double Validation providing several advantages over Single Validation, as previously analyzed. In Ouroboros, the order of block producers, selected among stakers, is based on a biased randomization, while the XinFin Network randomization for block verifiers is potentially uniform and based on smart contracts. Furthermore, the use of voting as in XinFin Network and DPoS enables more incentive equality between stakers.
</p>
<h1><strong>V. CONCLUSION AND PERSPECTIVES</strong> </h1>


<p>
In this paper, the XinFin Network proposed a XDPoS blockchain protocol which has heuristic and rigorous security guarantees, in addition to fast finality. Also presented is a novel reward mechanism, showing a capability to lower the probability of having forks, and guaranteeing fast confirmation time. Plus, the reward mechanism indicates that the contributions and benefits of masternodes are fair in the sense that the probability distribution function is uniform, eventually.
</p>
<h3 id="perspectives"><strong>Perspectives</strong></h3>


<ul>

<li>Future work: The XinFin team is currently working on the implementation of the XDPoS, which will be released on schedule as stated in its roadmap. Furthermore, in line with the network’s novel consensus protocol, its team will investigate the Sharding mechanism in order to provide even better transaction processing and performance. The XinFin team believes that the Sharding technique with a stable number of masternodes will provide better stability and efficiency to the blockchain. At the same time, the XinFin team commits to keeping EVM-compatible smart contracts within the network’s masternode Sharding framework.
<ul>

<li>Economic sustainability is also an important concept for a blockchain based decentralized network. That means to maintain the network in a sustainable condition, an equilibrium needs to be achieved, in which the cost of running the network infrastructure could be offset by the revenues generated. In this context, the cost of network infrastructure consists of two parts: the physical cost of having hardware such as servers, memories that pass the network technical requirements; and the capital cost of having XDC locked into smart-contracts. The revenues for masternodes would primarily come from Reward Engine emission, and later on from service revenues such as token exchange fees provided by applications running on top of the XinFin Network. We will publish a XinFin Network economic analysis and proposal, separate from this technical paper, at a later date.
</li>
</ul>
</li>
</ul>
<h1><strong>VI. Updated Note as on 17th march, 2021</strong></h1>


<p>
<strong>Consensus level issue:</strong>
</p>
<p>
XDPoS Network is stable for the last 2 years but one small Side Chain has been created as of 14th march, 2021
</p>
<p>
Here is the event description and how fixed by the masternode holders: 
</p>
<p>
<strong>Incident date as on:</strong> 14-03-2021
</p>
<p>
<strong>Total Node affected: </strong>67 out of 143<br><strong>Side Chain Created at Blocks No:</strong>  27307800<br><br><a href="https://en.m.wikipedia.org/wiki/Byzantine_fault">Byzantine Fault/Problem</a>: Two separate networks started after block 27307800 where one original network and 27 nodes started synching as an additional side network within a few minutes 67 nodes became part of the side network. Issue also described as <a href="https://en.m.wikipedia.org/wiki/Byzantine_fault">Byzantine fault</a>. 
</p>
<p>
<strong>Quick fix</strong>: Got Validators support (side chain validators) and resolve additional network issues by restarting/syncing nodes with original nodes network. 
</p>
<p>
<strong><a href="https://xinfin.network">XinFin Network</a> reference to understand issue:</strong>
</p>
<p>
XinFin Network is Fork of Ethereum Network and change Network Consensus to XDPoS
</p>
<p>
<strong>Reference to GitHub code for consensus: </strong><a href="https://github.com/XinFinOrg/XDPoSChain/tree/master/consensus">https://github.com/XinFinOrg/XDPoSChain/tree/master/consensus</a> 
</p>
<p>
<strong>Current network consensus details:</strong> 
</p>
<p>
Validators Node have to stake 10Millions XDC to become a part of validators Network. 
</p>
<p>
<strong>Nos of masternoder/validators:</strong> 108 
</p>
<p>
<strong>Backup Node:</strong> 32
</p>
<p>
<strong>Transaction process:</strong> ⅔ Node Validation to Write Block of the transaction
</p>
<p>
<strong>Block time:</strong> 2 Seconds. 
</p>
<p>
<strong>Block confirmation time to sync:</strong> 32 Blocks. 
</p>
<p>
<strong>Current size of data:</strong> 40GB+
</p>
<p>
<strong>More details on Consensus at:</strong> <a href="https://xinfin.org/xinfin-consensus">https://XinFin.org/XinFin-consensus</a> 
</p>
<p>
<strong>Network Bounty</strong>: Technical as well as Research team is still looking to resolve the above consensus level issues. Foundation announced a large bounty to prevent the above-mentioned network consensus issue. XinFin Network invites the technical/research team to welcome suggestions to resolve the above issue. Please create a GitHub pull request and claim <a href="https://www.xinfin.org/bounty">XDC bounty</a> if you would like to collaborate with a solution. 
</p>
<p>
This whitepaper evolved on a time-to-time basis after Livenet and testing various situations and errors faced by the network. Please feel free to add/suggest your feedback on the GitHub page.  
</p>
<p>

</p>
<h1 id="endnotes"><strong>Endnotes:</strong></h1>


<ol>

<li>CB Insights. “58 Big Industries Blockchain Could Disrupt.” CB Insights Research. CB Insights, March 19, 2021. <a href="https://www.cbinsights.com/research/industries-disrupted-blockchain/">https://www.cbinsights.com/research/industries-disrupted-blockchain/</a>.

<li>Ganne Emmanuelle, and Deepesh  Patel. “Blockchain & DLT In Trade: Where Do We Stand?” Trade Finance Global. © Trade Finance Global, October 1, 2020. <a href="https://www.tradefinanceglobal.com/wp-content/uploads/2020/11/2020_TFG_BLOCKCHAIN-_-DLT-IN-TRADE_Compressed.pdf">https://www.tradefinanceglobal.com/wp-content/uploads/2020/11/2020_TFG_BLOCKCHAIN-_-DLT-IN-TRADE_Compressed.pdf</a>.

<li>Digiconomist “Bitcoin Energy Consumption Index.” Digiconomist, March 10, 2021. <a href="https://digiconomist.net/bitcoin-energy-consumption/">https://digiconomist.net/bitcoin-energy-consumption/</a>.

<li>Digiconomist “Ethereum Energy Consumption Index (Beta).” Digiconomist, March 5, 2021. <a href="https://digiconomist.net/ethereum-energy-consumption">https://digiconomist.net/ethereum-energy-consumption</a>.

<li>XinFin. 2021. "How to Deploy a XinFin Public masternode". XinFin.Org. <a href="https://docs.xinfin.org/docs/raw/masternodes">https://docs.XinFin.org/docs/raw/masternodes</a>.

<li>Hoskinson, Charles. “Why We Are Building Cardano --a Subjective Approach.” https://whitepaper.io/search/result?q=Cardano. Cardano. Accessed March 28, 2021. <a href="https://assets.whitepaper.io/documents/HkUIhFWhL/HkUIhFWhL.pdf?AWSAccessKeyId=AKIAI7X7HAN3A7HLG22A&Expires=1616935771&Signature=42S80pEKu3c1R5yA%2Bh6p1i5srrA%3D">https://assets.whitepaper.io/documents/HkUIhFWhL/HkUIhFWhL.pdf?AWSAccessKeyId=AKIAI7X7HAN3A7HLG22A&Expires=1616935771&Signature=42S80pEKu3c1R5yA%2Bh6p1i5srrA%3D</a>

<li> Zoltu , Micah. “Ethereum/EIPs.” GitHub, September 29, 2020. <a href="https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md">https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md</a>.

<li>Yutelin. “Istanbul Byzantine Fault Tolerance · Issue #650 · Ethereum/EIPs.” GitHub, June 22, 2017. <a href="https://github.com/ethereum/EIPs/issues/650">https://github.com/ethereum/EIPs/issues/650</a>

<li>Wani, Sharyar, Mohammed Imthiyas, Hamad Almohamedh, KhalidM Alhamed, Sultan Almotairi, and Yonis Gulzar. “Distributed Denial of Service (DDoS) Mitigation Using ...” Multidisciplinary Digital Publishing Institute. Accessed March 29, 2021. <a href="https://www.mdpi.com/2073-8994/13/2/227/pdf">https://www.mdpi.com/2073-8994/13/2/227/pdf</a>.

<li>Buterin, Vitalik. “Ethereum Whitepaper.” ethereum.org, 2013. <a href="https://ethereum.org/en/whitepaper/">https://ethereum.org/en/whitepaper/</a>.

<li>Richards, Sam. “Gas and Fees.” ethereum.org, January 15, 2021. <a href="https://ethereum.org/en/developers/docs/gas/">https://ethereum.org/en/developers/docs/gas/</a>.

<li>Nakamoto, Satoshi. “Bitcoin: A Peer-to-Peer Electronic Cash System.” bitcoin.org, 2008. <a href="https://bitcoin.org/bitcoin.pdf">https://bitcoin.org/bitcoin.pdf</a>.

<li>Lee, Greg. “EOSIO/Documentation.” GitHub, April 28, 2018. <a href="https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md">https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md</a>.
</li>
</ol>
<h1 id="figures-list"><strong>Figures List:</strong></h1>


<ul>

<li>Fig. 1. XinFin Network architecture

<li>Fig. 2. Single Validation (SV): (a) SV with block creation masternode as an attacker and (b) SV with two consecutive block creation masternodes as attackers.

<li>Fig. 3. Double Validation (DV): (a) DV with block creator as an attacker and (b) DV with both block creator and block verifier as attackers

<li>Fig. 4. Timeline of Blockchain Making Process

<li>Fig. 5. Process of Voting Committee, Randomization of Block Verifiers, Creating and Validating Blocks in Each Epoch

<li>Fig.6.Distributed denial of service (DDoS) attack.

<li>Fig.7. Comparison of Energy Consumption between Bitcoin, Ethereum and XinFin XDC Network

<!-- Footnotes themselves at the bottom. -->

<h2>Notes</h2>
<div class="footnotes">
<hr>
<ol><li id="fn1">
<p>
     CB Insights. “58 Big Industries Blockchain Could Disrupt.” CB Insights Research. &nbsp;<a href="#fnref1" rev="footnote">&#8617;</a><li id="fn2">
<p>
    <sup> </sup>Ganne Emmanuelle, and Deepesh Patel. “Blockchain & DLT In Trade: Where Do We Stand?” Trade Finance Global&nbsp;<a href="#fnref2" rev="footnote">&#8617;</a><li id="fn3">

<p>
    <sup> </sup>Digiconomist “Bitcoin Energy Consumption Index.”&nbsp;<a href="#fnref3" rev="footnote">&#8617;</a><li id="fn4">
<p>
    <sup> </sup>Digiconomist “Ethereum Energy Consumption Index (Beta).”&nbsp;<a href="#fnref4" rev="footnote">&#8617;</a><li id="fn5">
<p>
    <sup> Hoskinson, Charles. “Why We Are Building Cardano --a Subjective Approach.”</sup>&nbsp;<a href="#fnref5" rev="footnote">&#8617;</a><li id="fn6">
<p>
    <sup>EMPTY</sup>&nbsp;<a href="#fnref6" rev="footnote">&#8617;</a><li id="fn7">&nbsp;<a href="#fnref7" rev="footnote">&#8617;</a><li id="fn8">&nbsp;<a href="#fnref8" rev="footnote">&#8617;</a><li id="fn9">
<p>
    <sup> Zoltu, Micah. “Ethereum/EIPs.” GitHub, September 29, 2020. https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md.</sup>&nbsp;<a href="#fnref9" rev="footnote">&#8617;</a><li id="fn10">
<p>
    Yutelin. “Istanbul Byzantine Fault Tolerance · Issue #650 · Ethereum/EIPs.” GitHub, June 22, 2017. https://github.com/ethereum/EIPs/issues/650&nbsp;<a href="#fnref10" rev="footnote">&#8617;</a><li id="fn11">
<p>
    <sup>Yutelin. “Istanbul Byzantine Fault Tolerance · Issue #650 · Ethereum/EIPs.” </sup>&nbsp;<a href="#fnref11" rev="footnote">&#8617;</a><li id="fn12">
<p>
    <sup> Wani, Sharyar, Mohammed Imthiyas, Hamad Almohamedh, KhalidM Al Hamed, Sultan Almotairi, and Yonis Gulzar. “Distributed Denial of Service (DDoS) Mitigation Using ...”</sup>&nbsp;<a href="#fnref12" rev="footnote">&#8617;</a><li id="fn13">
<p>
    <sup> Buterin, Vitalik. “Ethereum Whitepaper.” ethereum.org, 2013. https://ethereum.org/en/whitepaper/.</sup>&nbsp;<a href="#fnref13" rev="footnote">&#8617;</a><li id="fn14">
<p>
    <sup> Richards, Sam. “Gas and Fees.” ethereum.org, January 15, 2021. https://ethereum.org/en/developers/docs/gas/.</sup>&nbsp;<a href="#fnref14" rev="footnote">&#8617;</a><li id="fn15">
<p>
    <sup> Nakamoto, Satoshi. “Bitcoin: A Peer-to-Peer Electronic Cash System.” bitcoin.org, 2008. https://bitcoin.org/bitcoin.pdf.</sup>&nbsp;<a href="#fnref15" rev="footnote">&#8617;</a><li id="fn16">
<p>
    <sup> Lee, Greg. “EOSIO/Documentation.” GitHub, April 28, 2018. https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md.</sup>&nbsp;<a href="#fnref16" rev="footnote">&#8617;</a><li id="fn17">
<p>
    <sup> Lee, Greg. “EOSIO/Documentation.</sup>&nbsp;<a href="#fnref17" rev="footnote">&#8617;</a><li id="fn18">
<p>
    <sup> Lee , Greg. “EOSIO/Documentation.</sup>&nbsp;<a href="#fnref18" rev="footnote">&#8617;</a><li id="fn19">
<p>
    <sup> Hoskinson, Charles. “Why We Are Building Cardano --a Subjective Approach.”</sup>&nbsp;<a href="#fnref19" rev="footnote">&#8617;</a>

</ol></div>
