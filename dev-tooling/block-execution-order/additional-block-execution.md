# Additional Block Execution

Here is an example Graph that shows the order of execution.

<figure><img src="../../.gitbook/assets/OrderOfOperationsGraph.jpg" alt=""><figcaption><p>Sample Graph (Click to enlarge)</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-08 162330.png" alt=""><figcaption><p>Connectors run first</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-08 162346.png" alt=""><figcaption><p>On Graph Start run second</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-08 162359.png" alt=""><figcaption><p>TriggerAtStart option on a Timer will run third</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-08 162418.png" alt=""><figcaption><p>Finally, the Entry Point is executed</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-08 162427.png" alt=""><figcaption><p>Example showing when a timer will trigger with 'TriggerAtStart' set to false</p></figcaption></figure>

Finally, let's inspect the output from the Graph



<figure><img src="../../.gitbook/assets/Terminal.jpg" alt=""><figcaption><p>Terminal output of the running Graph.</p></figcaption></figure>

