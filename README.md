# MyViewOfComputationalGraphs

![diagram-of-a-computatoinal-graph](https://github.com/lsc4719/MyViewOfComputationalGraphs/blob/main/view-of-data-structure-computational-graph.drawio.svg)

### my view

A computational graph is a data structure with states denoted by abow diagram.  

#### bolts and nuts
| item | description |
| - | - |
| in-degree=0 boxes | are input(inpendendent) nodes(variables). |
| in-degree>0 boxes | are dependent varaiables. |
| blue box | is the unique output variable. |
| yellow boxes | are variables to store gradients. |
| circles | are functions. |
| arrows | mean input/output relationship between variables and functions. |

#### supported operations
| operation | note |
| - | - |
| initialize inputs | |
| initialized gradients | |
| forward | calculate dependent variables by calculating functions in topological order |
| backward | calculate gradients in reverse-topological order from output variable's gradient(=1 always) |
| update | update some variables based on gradients (ex. variable = variable - learning_rate * gradient) |
| reversed-mode autodiff | apply forward and then backward sequentially |


### ref

zero-to-hero, Karpathy https://karpathy.ai/zero-to-hero.html
