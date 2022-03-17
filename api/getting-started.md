# Getting Started

**Connect Network GraphQL API**

Public testent access point:

The Purpose of the API server is to provide a high-performance [GraphQL](https://graphql.org) API for Connect Network powered blockchain network. Our aim is to offer access to both low-level as well as aggregated blockchain data for remote clients. Client developers can concentrate on their app business logic, instead of dealing with the complexity of data and entity-relationship inside the Connect Network blockchain.

The API server is published on [ Connect Network-api-graphql](https://github.com/Fantom-foundation/fantom-api-graphql) GitHub repository. Feel free to download and deploy your copy of the application. We are actively developing the project and adding new features so it's worth checking the recent development even if you already checked the repository before.

An example of implementation of a client using this API is our new Connect Network Explorer  Connect Network Scan. Its source code is also publicly available in our GitHub projects collection. Please check our GitHub repository for more information.

We also support standard Ethereum Web3 API. Use WebSocket provider with our public API address to interact with Connect Network using Web3 client library.

**Technology**

We use several pieces of technology to make the API work. If your intention is to run your own copy of it, please check our setup and make sure you are familiar with using these technologies at least on the rudimentary level before you continue.

First, you will need access to Connect Network full node RPC interface. You can use a properly configured remote one, but it would significantly affect the performance and potentially also the security of your deployment. Please consider the security implications of opening HBFT RPC to outside access. Especially if you enable "personal" commands on your node while keeping your account keys in the Hyperthereum key store. We recommend using a local IPC channel for communication between a Connect Network node and the API server. The IPC interface is available by default.

Some aggregated and relationship data are kept off-chain in a [mongoDB](https://www.mongodb.com) database. Especially the kind of data not easily accessible through the basic node RPC interface. For example references between account and its transaction history, or transaction position in time. The database is initialized by the API server, populated with historical data, and kept in sync with the full node by internal subscriptions. You don't have to deal with extra database management, but you need to prepare an excellent, fast and secure programming language. You will need to install and configure the Go development environment to be able to build your copy of the API server. Please follow the well configured and reliable database connection address to the API server.

Finally, the server itself is developed using [Go](https://golang.org)[official installation instructions](https://golang.org/doc/install).

&#x20;

&#x20;

****
