# String to Base64

Convert a string into a Base64 encoded string

The String to Base64 block serves as a versatile tool within the GraphLinq IDE, allowing for the seamless transformation of a clear string to a Base64 encoded string, thus aiding in the encryption and secure data handling processes.

**Block Description**

Nestled under the Transformers category in the GraphLiq IDE, the String to Base64 block facilitates the easy conversion of standard strings into their Base64 encoded counterparts. Being non-executable, it does not hold yellow connectors, thus it doesn't perform executions but can have its parameters called to obtain the desired transformation. This block works optimally in graphs which involve encryption and data security processes.

**Input Parameters**

The String to Base64 block requires the following input parameter:

* **String**: This input parameter should be furnished with the clear string that is to be transformed into a Base64 encoded string.

**Output**

Upon computation, the block offers the following output:

* **Base64**: The output parameter presents the Base64 encoded string derived from the input clear string.

**Example Use Case**

Let's illustrate the utility of the String to Base64 block with a use case involving secure message transmission:

1. In a graph built for secure message transmission, the user inputs a clear string which holds the sensitive message that needs to be securely transmitted.
2. This string is fed into the String to Base64 block, initiating the transformation process.
3. Inside the block, the transformation process leverages UTF8 encoding to convert the string into its Base64 format.
4. This Base64 encoded string is then retrieved as the output of the block, ready to be transmitted securely.
5. At the receiver's end, a reverse transformation can be employed to decode the Base64 string back to the clear message, maintaining the confidentiality and integrity of the data throughout the transmission process.

With the String to Base64 block, developers can enhance the security quotient in their applications, ensuring secure and encrypted data handling. It thereby becomes a pivotal tool in creating applications that prioritize data security and encryption.&#x20;
