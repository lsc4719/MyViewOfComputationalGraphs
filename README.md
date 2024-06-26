# MyViewOfComputationalGraphs

![diagram-of-a-computatoinal-graph](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/view-of-data-structure-computational-graph.drawio.svg)

### my view

A computational graph is a data structure with states denoted by abow diagram.  

#### background

We could always minimize output variable w.r.t. some input variables of a computation graph data structure   
by using reverse-mode autodiff and gradient-descent algorithm.

#### bolts and nuts
variables and functions form a connected directed-acyclic graph with unique sink output variable node.  
If we treat variables as tensors, then this datastructure includes not only scalars but also includes vectorization.  
But as far as I know, all oprations in computational graphs dealing with AI are scalar-wise operations.  
i.e., all operations could be reduced into scalar-wise operations.  

| item | description |
| - | - |
| in-degree=0 boxes | are input(inpendendent) nodes(variables). |
| in-degree>0 boxes | are dependent varaiables. |
| blue box | is the unique output variable. |
| yellow boxes | are node labels for variables to store gradients. |
| circles | are functions. |
| arrows | mean input/output relationship between variables and functions. |

#### supported operations
| operation | note |
| - | - |
| initialize inputs | |
| initialize gradients | |
| forward | calculate dependent variables by calculating functions in topological order |
| backward | calculate gradients of output-variable w.r.t. variables in reverse-topological order using chain-rule from output variable's gradient(=1 always)|
| update | update some variables based on gradients (ex. variable = variable - learning_rate * gradient) |
| reversed-mode autodiff | apply forward and then backward sequentially |
| **gradient descent** | apply reverse-mode autodiff and then update sequentially serveral times until output variable became sufficiently small. |

#### example: percpetron

##### neural network diagram
![neural network diagram of perceptron](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/neural-network-perceptron.drawio.svg)

##### computational graph diagram (w/o loss)
![computational graph diagram of perceptron](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/33c5fbc0aa38a64b4c4a3808615b31f4521024cc/perceptron.drawio.svg)

Actually this diagram does not strictly fit into the definition of computational graph what I defined above.  
Because this diagram do not have single output node explicitly.  
But if we give up some operations including backward, then we could implment this diagram also.  

#### example: MLP

##### neural network diagram
![neural network diagram of mlp](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/neural-network-mlp.drawio.svg)
 
##### computational graph diagram (vectorzation) (w/ loss)
![computational graph diagram of mlp with loss](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/mlp-with-loss-vectorization.drawio.png)


### ref

zero-to-hero, Karpathy https://karpathy.ai/zero-to-hero.html  
deep learning from scratch 1 https://www.yes24.com/Product/Goods/34970929
