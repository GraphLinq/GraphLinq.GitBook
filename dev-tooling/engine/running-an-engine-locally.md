# Running an Engine locally

Once you have prepared your own environment, you need to download and setup the Engine.

Download the Engine from the official GraphLinq repository:

```
git clone https://github.com/GraphLinq/GraphLinq.Engine
```

Install the required [Nuget](https://www.nuget.org/) packages to load the Engine through the interface or on CLI:

```
dotnet restore
```

Then you need to setup the init variables:

```
redis_master_addr=REDIS_SERVER_HOST {ex: "localhost"}redis_master_port=REDIS_SERVER_PORT {ex: 6379}redis_master_passw=REDIS_SERVER_PASSWORD {ex: 12345}eth_api_http_url=ETH_HTTP_NODE {ex: "https://mainnet.infura.io/v3/xxx"}eth_api_ws_url=ETH_WS_NODE {ex: "wss://mainnet.infura.io/ws/v3/xxx"}mariadb_uri=MARIA_URI {ex: "Server=localhost;Database=graphlinq;User=root;Password=superp@ssw0rd;Port=3306;Max Pool Size=50;Connection Timeout=60;"}factor_decimal=DECIMAL_USED_FOR_GAS {ex: "1000000000000000000"}
```

Next step is to load the Engine by running it through CLI or Visual Studio Interface

If you have something look alike as an output, you're engine is up and ready to handle new graphs, congratulations!\
The next step is to use the embedded internal API within the Engine code to deploy and start your local graphs directly.

Doing this will also make you eligible to earn GLQ as rewards since nodes will be notified that you're contributing to the network by running on-chain processor and executing graphs on-chain.&#x20;

[\
](https://docs.graphlinq.io/engine/1-index)
