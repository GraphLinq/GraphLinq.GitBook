# Block Overview

A node or block is a point in a network or diagram at which lines or pathways intersect.

Each block's type have a different use, you can link them to each other to create a powerful graph and automate your tasks.

It contains a set of instructions pre-scripted that you can use automatically, here is a sample of node that get a pair price on Uniswap using the graph API named as `GetUniswapPairPriceNode`:

{% code overflow="wrap" lineNumbers="true" %}
```clike
 [NodeDefinition("GetUniswapPairPriceNode", "Uniswap Get Pair Price", NodeTypeEnum.Function, "Uniswap")]
    public class GetUniswapPairPriceNode : Node
    {
        public GetUniswapPairPriceNode(string id, BlockGraph graph)
          : base(id, graph, typeof(GetUniswapPairPriceNode).Name)
        {
            this.InParameters.Add("pairAddress", new NodeParameter(this, "pairAddress", typeof(string), true));
            this.OutParameters.Add("token0Price", new NodeParameter(this, "token0Price", typeof(double), false));
            this.OutParameters.Add("token1Price", new NodeParameter(this, "token1Price", typeof(double), false));
        }
        private HttpClient client = new HttpClient();
        public override bool CanBeExecuted => true;
        public override bool CanExecute => true;
        public override bool OnExecution()
        {
            var query = JsonConvert.SerializeObject(new
            {
                query = $"{{ pair(id: \"{this.InParameters["pairAddress"].GetValue().ToString()}\") {{ token0Price, token1Price }} }}"
            });
            var content = new StringContent(query, Encoding.UTF8, "application/json");
            var response = client.PostAsync("https://api.thegraph.com/subgraphs/name/uniswap/uniswap-v2", content).Result;
            var result = JsonConvert.DeserializeObject<UniswapPairGraphPrice>(response.Content.ReadAsStringAsync().Result);
            this.OutParameters["token0Price"].SetValue(double.Parse(result.Root.Pair.Token0Price, CultureInfo.InvariantCulture));
            this.OutParameters["token1Price"].SetValue(double.Parse(result.Root.Pair.Token1Price, CultureInfo.InvariantCulture));
            return true;
        }
    }
```
{% endcode %}

You can ask to the community to code new nodes over external libraries and then submit them to the team for a review, or ask directly the official GraphLinq team for special requests to add new nodes type on the Engine, this way, we can really focus on the utility and implement new featured blocks quite fast and easily.
