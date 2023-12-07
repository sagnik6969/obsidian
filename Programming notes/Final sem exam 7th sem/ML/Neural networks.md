Characteristics of ANN  
→ Mathematical model  
→ Interconnections with weights, hold the informative knowledge.  
→ The training or learning rules adopted for updating and adjusting the connection weights.  
→ Activation functions

### Design a hebb net for AND Function
![[Pasted image 20231207113539.png]]
![[Pasted image 20231207113654.png]]
![[Pasted image 20231207113805.png]]

A neural network is a computational model inspired by the structure and functioning of the human brain. It is composed of interconnected nodes, often referred to as neurons or artificial neurons, organized into layers. Neural networks are a fundamental component of the field of machine learning and artificial intelligence.

Here are the key components of a neural network:

1. **Neurons (Nodes):**
    
    - Neurons are the basic units of a neural network. Each neuron receives input, processes it using a certain computation, and produces an output. In an artificial neural network, the neuron's operation is modeled after the functioning of biological neurons.
2. **Layers:**
    
    - Neurons are organized into layers. There are typically three types of layers in a neural network:
        - **Input Layer:** Neurons in this layer receive the initial input data.
        - **Hidden Layers:** These layers come between the input and output layers and are responsible for processing and learning complex patterns in the data.
        - **Output Layer:** Neurons in this layer produce the final output of the network.
3. **Connections (Weights):**

    - Neurons in one layer are connected to neurons in the next layer. Each connection is associated with a weight, which determines the strength of the connection. During training, these weights are adjusted to optimize the network's performance.
4. **Activation Function:**
    
    - Each neuron typically applies an activation function to the weighted sum of its inputs. This introduces non-linearity to the network, allowing it to learn and represent complex relationships in the data.
5. **Feedforward and Backpropagation:**
    
    - The process of passing input data through the network to produce an output is called feedforward. During training, the network's performance is evaluated using a loss function, and the backpropagation algorithm is used to update the weights of the connections. This iterative process helps the network learn from the data.
6. **Training Data:**
    
    - Neural networks require labeled training data to learn patterns and relationships. The training data consists of input-output pairs, and the network adjusts its weights to minimize the difference between predicted and actual outputs.
7. **Deep Learning:**
    
    - Neural networks with multiple hidden layers are referred to as deep neural networks. The term "deep learning" specifically applies to the training of deep neural networks, which have demonstrated exceptional performance in various tasks such as image recognition, natural language processing, and more.

Neural networks have proven to be powerful tools for solving complex problems and have achieved remarkable success in various domains. Different types of neural network architectures, such as convolutional neural networks (CNNs) for image processing and recurrent neural networks (RNNs) for sequential data, have been developed to address specific challenges in different application areas.