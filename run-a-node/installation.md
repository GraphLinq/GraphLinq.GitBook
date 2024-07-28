# Installation

**`docker pull graphlinqchain/docker-glq-nodemanager:v0.0.3`**

**`docker run -d -p 8080:8080 -p 8545:8545 -p 30310:30310 -p 30311:30311 graphlinqchain/docker-glq-nodemanager:v0.0.9`**

### 1. Setup First Access Password&#x20;

To begin setting up your Graphlinq node, navigate to http(s)://ip:8080/status. Here, you'll be prompted to set an access password to secure the node management. It's important to choose a strong password of at least 15 characters to ensure maximum security. Once you've entered your chosen password, you'll be taken to the setup page to continue the process.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please setup a big password \~15characters minimum.
{% endhint %}



### 2. Node Setup&#x20;

In the Node Setup section, you will need to provide a keystore or the secret of a wallet, and define a strong password to create a keystore. This step is crucial to protect your node from any potential risks. You can refer to the image provided for guidance.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

After providing the necessary information, simply click on the "Fire" button to launch your node.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### 3. Add Peers



Add enode:// peers or domain names of other docker manager nodes.

examples of enode://:

> [http://103.125.216.32:8080/](http://103.125.216.32:8080/)\
> enode://ebdfb40a6b7aa55a5907519630b736866ab0f8d87b3bb63b7ffa85b83448b05db2a5c3e6f7b3a88fb025712920f90b337d2c071d0135c699245aa6b8df25caeb@139.99.143.9:30310\
> enode://0800b9f12b35973d219f51d072b2fff600f390e72af173730a0603f161200fcbcb8aa0d28a233d3ccdd52e2d32b00bd6a176c81cafa4adfe20be87c45e11748f@51.91.10.33:30310\
> enode://a0d795683d38d03690f25f216e699c646410841dfcc6aa29a085affafab19eac1d26612499489c142ca667abcb3c6ad200b040bc75460d0442c4b257519fe043@34.122.85.128:30310\
> enode://7bac6e22dd728711e793c9d0868a593d3aa503ea3fa0471cb612b8c3fb2d38fbd2a038317d6cf16ae96f2a3fe955f1ff8c7ef0aa1864d54b0630aa0f895bdbbd@103.125.216.32:30311\
> [enode://6b61197a2c652ab024f4d19b18862e927e6cca223649aec7b4ce38e5755eebfe3ec18629c2f96723d6f329adf3c77a9fdb28638c778a0ea08e68bd878fd7e14c@103.125.216.32:30310](enode://6b61197a2c652ab024f4d19b18862e927e6cca223649aec7b4ce38e5755eebfe3ec18629c2f96723d6f329adf3c77a9fdb28638c778a0ea08e68bd878fd7e14c@103.125.216.32:30310)

### 4. Node Management Page

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

1. Enter your keystore password in the "Node Wallet Password Field" and click on the "Start" button labeled as (1) to begin the node startup process.
2. Once the node has completed its initial synchronization, you can start the exposed node by clicking on the "Start" button labeled as (2).
3. If you are using an Internal Node Wallet that is designated as a validator, you can click on the "Start Miner" button.

(Note that the main node is never accessible from the outside to increase security. You should only enter your password when launching the node. The second node should only be started if you want to expose an RPC. The exposed ports will be displayed in the red square, and the second node (external node) will be connected to the internal node.)

Please note that the "Start Miner" button is only available for validators who have been accepted by Graphlinq. If you would like to request acceptance, please contact the Graphlinq team at [info@graphlinq.io](mailto:info@graphlinq.io).
