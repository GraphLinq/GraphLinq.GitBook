# File compression

Graphs saved are compressed in a specific format to assure reliability, security and authenticity. The raw json payload is converted using the gzip compression protocol:\
GZip is a form of data compression -- ie it takes a chunk of data and makes it smaller. The original data can be restored by un-zipping the compressed file.

It's then converted to base64 bytes code so that it is easily shareable to anyone. You can send your GLQ file to anyone and they will be able to execute it as part of one new Graph, and modify it.

A graph has an hash which is from a SHA256 algorithm hashed with the base b64 bytes code + your public wallet identifier which makes it unique for everyone. It means that multiple people can deploy the same graph and manage their own states separately.

SHA-256 is used in some of the most popular authentication and encryption protocols, including SSL, TLS, IPsec, SSH, and PGP. In Unix and Linux, SHA-256 is used for secure password hashing. Cryptocurrencies such as Bitcoin use SHA-256 for verifying transactions.
