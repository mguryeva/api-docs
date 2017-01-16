# cyber•Chain: Motivated Search Engine for Permanent Web
[Dima Starodubcev](https://steemit.com/@hipster)
[cyber•Fund](https://cyber.fund)
Working Draft

## Abstract
Existing search engines are restrictive centralized databases everybody forced to trust. Emergence of content-addressable storage and distributed ledger technology create opportunity to shift existing web's ubiquitously used client-server architecture based on DNS, HTTP and IP protocols to a truly peer-to-peer interactions based on stateless IPFS and variety of stateful consensus computers such as Ethereum. Moreover blockchain architecture itself allow to organize search engine for public information in a way inaccessible for previous architectures. This creates a challenge for a search engine based on emerging technologies and specifically designed for them. In this paper we discuss opportunities behind this transformation, challenges of crawling, indexing and evaluation for the next generation web and propose a blockchain based set of smart contracts to address discussed issues.

## Introduction
...
- Blockchain agnostics ...
- No single point of failure ...
- Resistance to sybil attacks ...
- Resistant to spam ...
- Challenges in indexing distributed systems ...
- ....
...

## Streaming instead of Crawling
Workflow of conventional search index is straightforward: web crawler fetch a page, than follow up links, fetch the following pages and so on. After some loops web crawler is able to get virtually all links in existence. Information contained in webpages is mutable. Thus search engine should decide than and how to fetch indexed links for new versions of documents. As webpages are loosely structured than it should somehow filter all the noise. In distributed systems all documents are protected from mutability by hash which (1) uniquely identify document and (2) work as address in a peer-to-peer network such as IPFS. Thus links to documents are also immutable. This property free search engine from rescanning work significantly reducing resources necessary for keeping index fresh. We call this approach *setup once index forever*.

It would be naive to bootstrap a search engine from a scope where Google exist. We need to find a special area there general purpose search engines sucks. Variety of distributed ledgers such as blockchains and tangles can be primary content-addressable data suppliers and this is a scope where current search engines are not the best at work. Blockchains provide realtime high quality structured data which don't requires crawling. One node of any given blockchain is enough to provide verified data about transactions within on ledger without necessity to continuously revisit resources significantly reducing costs.

As transactions are primary way of changing states of databased currently used by any web applications we don't exclude that distributed ledgers and not websites can be primary source of public information in 21 century.

## No Noise Filtering
Blockchains are highly optimized databases. Every transaction cost money so they are neutrally protected from spam and contain only data that is really matter. That reduce noise filtering to nearly zero level. Structured raw data about blocks and transaction is available for everybody. This fact also reduce resources.
![Google vs Blockchain](https://docs.google.com/drawings/d/1AkdiCTalgqKqkOKgeJCtD4CCwt68buP1rDN2J95FGSY/pub?w=1440&h=743)

## Search Engine Design
Our proposed design of search engine enable everybody to participate and be rewarded. Everybody can post to an index a document. A document can be of 3 types:
1. Link to IPFS and document itself for json and text documents.
2. Link to a IPFS document for media content.
3. Stored Search Query for any arbitrary search query every asked.

Post headers are purposefully unique. Provided consensus verify hashes for (1), hashes and availability for (2) and uniqueness of query for (3) thus ensuring that all documents are content-addressable, available and unique. Heavy use of IPFS is necessary to exclude data deduplication for mutable documents stored on chain for purposes discussed further.

We lay as a foundation consensus algorithm and payouts used in Steem []. This design is proved to work and can be applied for our use case with slight changes. Thus a market for putting into index is open for everybody. During a first week a market of ranking assign a final value which lay as input to cyber•rank calculation. Conventional search engine work with zero trust data. More than 200 factors used to calculate initial pagerank for new document in the graph. Our novel approach allow to assign initial value based on sybil resistant voting. It is our belief that proposed approach can significantly simplify ranking and be more precise for information those nature is subjective.

For every post everybody can submit an answer in form of link to an IPFS document. Thus client-side application can deliver document thorough IPFS without necessity to go somewhere. This approach is simple and powerful. This are several use cases what can be returned for user:
1. Dynamic snippet. This can be thought as micro application that can dynamically take as input data from search query, lazy on-chain oracles and conventional https apis.
2. Media content.
3. Static formatted snippet with a link to a conventional web.
4. Static formatted snippet with text answer

Thus we propose a market for answers on search queries everybody are encouraged to participate.

## Ranking Resistant to Sybil Attacks
...
We use cyber•rank algorithm that is extended version of pagerank []
![cyber•rank](https://docs.google.com/drawings/d/1yvkyeOpVZoiyUOv0Gqu-kywsaWF16A9NTw8GgJq-rX8/pub?w=1521&h=933)
cyber•rank = Congenital (what was payed out) + Acquired (what was compute)

...

## Recursion Limiting
Our model is recursive and require enormous amount of calculations which are limited within blockchain design. Model recalculation does not happens on a periodic basis rather it continuous. To limit precision of our model we can define Z as threshold for recomputing any given cyber•rank. It is hard to estimate what threshold should be set as correct. But it can be defined by market forces depending on model size and available computing resources within network. Thus Z should be defined as consensus variable by delegates.

## Stored Search Queries
Every time a user ask a search engine for answer either of two things happens:
- If a query match search engine return documents with sorted links.
- If a query is new a new document is written in a blockchain.

This is purposefully because it necessary to accumulate this data. But misspelled searches can contain forward links to correct searches. Thus entire semantic core is stored on chain and available for data mining.

## Documents in Search Results
Link to immutable documents directly in search results give client software significant benefits as (1) documents itself can be returned to client from IPFS or other content-addressable distributed network or (2) offline cache. This property can significantly improve user experience.

## Dynamic Snippets
That is the most powerful part of our proposed architecture. Dynamic snippets are small client side applications which cant be sorted by cyber•rank and delivered through content-addresable distributed network. They are naturally compete for a higher position in search results. Application developers should not develop a snippet for every unique search request. Snippets are dynamic because they can take as input information from a search query, user's data and documents distributed across the web. Thus before developing an application developer should target it for a specific semantic core before defining it. Semantic core and its statistic is publicity available in a blockchain. Developer shall need to develop application and submit a links to application for a targeted semantic core. Implication of this approach is hard to overestimate. E.g. dynamic snippets combined with blockchain wallet make possible to shop right from search results.

## Training the Model
Click-through information is stored on chain. Every time a user follow a link positive voting transaction is broadcasted e.g. with grade 1. Voting on a protocol level is a number in a range from -100 to 100. Thus application developers has a tool to implement different grades for different kind of interactions. Such design is crucial to train the model and acquire a data about search popularity of semantic core and its volume. Currently search engines are very careful in revealing this information because this information is the most important part of ranking. We want to change that. Every time a user click on a snippet developer earn fair portion of emission and on chain model is trained. Application acquire the more rank the more rank acquired by its links. The more cyber•rank acquired - the more revenue streams for application developer.

## Topical Relevance
For every answer 5 hashtags can be submitted in addition to link. This enables to compute the most relevant topics for every unique search query on chain without implementing consuming clusterizarion algorithms. This task should be done by either indexers or oracles who submit a link.

## User Relevance
It is trivial to implement a search relevant to a particular identity using proposed algorithm. The more a user train a model the more behavioural data can be associated with she. This personalized information can be stored local for (1) faster retrieval and (2) offline access. During search request global and local request can be done in parallel. This queries can be easily merged adjusted on user-defined importance of personalized search for her. The same approach is able to fix vocabulary mismatch problem.

## Spellchecking and Suggestions
Every query. Hence its better to reduce a noise and improve user experience offering simple to use API which return after-stemming suggestions. This kind of algorithm can be expensive to implement on chain. Thus in initial design this task can be solved in centralized way.

## Lazy Oracles
One specific ability is crucial for the next generation search engine. Application developers should have a motivation to provide structured arbitrary data feeds. Thus search engine can answer natural questions aggregating data from highly structured and defined feeds. This make possible a user get high quality *calculated* answers in realtime about state of reality expressed not only in links (which intelligent agent don't know how to parse) but in actionable numbers based on which its possible to make independent economic decisions.

Today different blockchain have functionality necessary to implement this. For eg. Ethereum enable construct smart contracts that can validate and incentivize data feeds. But Ethereum has strong limitation: a price. Due to a network design every operation should be validated across the network of 5k nodes. For every put operation developer of such contract should pay in hope that somebody in the future will use this feed in the future returning costs. Current cost of a permanent storage inside Ethereum contracts is around $200/megabyte. Worth to note that Ethereum has consensus variable gas limit. Currently a network load is around 10% of established limit. Once demand for computation reach a limit we will have a situation very similar for Bitcoin blocksize debate and price for storage can reach $2000k/megabyte easily without validation costs. Pretty expensive for unlimited possibilities. There is alternative - Factom. Its consensus design rely on a small amount of payed servers. Thus the cost is around $1/megabyte. Such low price comes with high limitations. You can only put data to Factom and read it. There is no validation and incentivzation built-in. There are persmissioned blockchain designs such as BigChainDB [] and Hyperledger [] which solves validation problem perfectly but require strong efforts for developers to program and establish a network and then somehow monetize it. Lazy Oracles are going to fill this gap providing robust, cheap and reliable way for monetizing structured public data.

The process consist of 3 steps:

Step 1: Everybody can declare a soft protocol for data feed by posting a document with tag *oracle-protocol*

```
// Basic Validation
doc_type: market_update // should be fixed
  exchange: string // domain name of exchange
  base: string // link to a definition of a reference namespace e.g. ISO or chaingear
  quote: string // link to a definition of a reference namespace e.g. ISO or chaingear
  price: uint16
  volume: unit32
// Audit Rules
Document format and data types should match a protocol
For every unique exchange and pair `market_update` report can be submitted no more frequently than once per minute.
If either a price or volume for unique exchange and pair has not been changed more than 0.1% a report should not be submitted.

```
There are some soft rules for protocol declaration:
- Protocol declaration should be agnostic from language implementation and unambiguous
- Protocol declaration should have a git link to open source implementation of plug-in that does validation and extend API.
- Protocol declaration should have a git link to open source implementation of data feed crawler

Step 2: Now every reporter can submit data according to a soft protocol. If data begin to be submitted without protocol definition a value of this data can be significantly lower. Thus auditors and curators encouraged to flag such documents. If false or malicious data come auditors and curators has strong incentive to flag such data.

Step 3: Curators validate any given document by scripts.

As result reporters, auditors (where objective validation is possible) and curators (where subjective validation is more appropriate) has strong incentive to (1) bring important data, (2) curate and audit data conscientiously. Proposed approach doesn't has strong guaranty of truthfulness of data such as Augur does. Rather its correct to say that we can have strong assurance that data is correct. But it is cheaper, faster and significantly more flexible. The process is robust in its unstructured simplicity.

Step 4. Payouts for curators are made. Payouts information is input information for cyber•rank. Using cyber•rank its trivial to filter feeds using plugins to give significantly more precise data with higher level of assurance.

Step 5. High quality data feeds (or lazy oracles) are available for a consensus engine of search engine (thus cyber•rank can be continuously improved) and everybody on the planet.

We call this type of oracles lazy because they don't require strict rules of validation by the expense of reducing the level of accuracy (but still enough to reason with high level of assurance). Also they are lazy because the don't require to think about monetization for participants rather consensus engine print rewards based on valuation of subjective contributions. This approach is superior to Ledgys [] than reporters should sell data pieces using costly Ethereum storage.  

## Use cases for Lazy Oracles

- Block validation
- Transaction validation
- Balance calculation
- Identity crawling
- Token valuation
- Token rating .... Link to cyber•Rating.
- Token description
- Crowdsale tracking
- Weather measuring
- Traffic measuring
- Business performance reporting

....

## Spam Protection

...

## Incentive Structure and Distribution Mechanism
... Intrinsic Value

More indexing => More people earn => More people use => More indexing

Roles:
- Indexers
- Oracles
- Curators
- Users

...

## Extensibility
Currently our implementation has the following functionality available for application developers.
- Custom Operations ...
- Plugins ...
- Escrow ...
- Private Messaging ...
- Dynamic Account Permissions ...

Our design allow to implement intensive on-chain calculations in case of 17 of 21 delelegates accpet a hardfork. This is for a purpose of keeping a protocol from bloating.

The following possibilities can be available in a future:
- Sidechains ...
- State Channels ...
- Smart Contracts ...

## Performance

...

## Scalability

...

## Self Governance

...

## Search Appliance
Fo bootsraping we are going to offer well tested open source specs for hardware configuration of commodity computer which cost around $10k and is able to participate and earn by itself.

Software is open source. Cybernode
![](https://camo.githubusercontent.com/57d52bf441a6df81026a5b9e24ac665d33b68bf3/68747470733a2f2f7261776769742e636f6d2f637962657246756e642f63796265726e6f64652f6d61737465722f63796265726e6f64655f30312e737667)
Hardware is open source. Enterprise.

...

## The power of cyber•Chain
Key purpose of our proposed design is not just replicate abilities of existing search engines which return only links but enable answering new class of question:
- How much value of X do I possess now?
- What probability of event Y?
- What packages do I need to install in order to improve ROI on available resources?

Our proposed design has all necessary components to bootstrap a markets for a new generation of answer applications.

Proposed economics model disintermediate conventional ad model there users are sold to advertiser and enable any business or people or robot benefit from pure peer-to-peer interactions which bring value for every involved participant.

... to provide necessary tools for emergence of economically rational robots. Blockchain technology enable creation of devices which are able to earn, store, spend and invest digital asset by themselves. What is needed is verified information about state of reality evaluated in transact-able assets. ...

Accessibility ... Transparency ...


## Conclusion
...


## References

...
