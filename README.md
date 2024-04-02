# MyViewOfComputationalGraphs

![diagram-of-a-computatoinal-graph](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/view-of-data-structure-computational-graph.drawio.svg)

### my view

A computational graph is a data structure with states denoted by abow diagram.  

#### bolts and nuts
variables and functions form a connected directed-acyclic graph with unique sink output variable node.  
If we treat variables as tensors, then this datastructure includes not only scalars but also includes vectorization.  

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

#### example: percpetron

##### neural network diagram
![neural network diagram of perceptron](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/neural-network-perceptron.drawio.svg)

##### computational graph diagram (scalar level) (w/o loss)
![computational graph diagram of perceptron](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/33c5fbc0aa38a64b4c4a3808615b31f4521024cc/perceptron.drawio.svg)

#### example: MLP

##### neural network diagram
![neural network diagram of mlp](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/neural-network-mlp.drawio.svg)
 
##### computational graph diagram (vectorization) (w/o loss)
![computational graph diagram of mlp without loss](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/mlp-vectorization.drawio.svg)

##### computational graph diagram (vectorzation) (w/ loss)
![computational graph diagram of mlp with loss](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/mlp-with-loss-vectorization.drawio.svg)


### ref

zero-to-hero, Karpathy https://karpathy.ai/zero-to-hero.html  
deep learning from scratch 1 https://www.yes24.com/Product/Goods/34970929
