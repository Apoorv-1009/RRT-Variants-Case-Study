# RRT Variants Case Study

This repository contains case studies on different versions of the Rapidly-exploring Random Tree (RRT) algorithm, including RRT*, RRT*-SMART, and Informed RRT*. These algorithms are widely used in the field of robotics for motion planning. </br>
Rapidly-exploring Random Trees (RRT) are a popular family of algorithms used for path planning in robotics and other fields. They are particularly useful for navigating complex spaces with obstacles. This repository explores three advanced variants of RRT: RRT*, RRT*-SMART, and Informed-RRT*.

## RRT*

RRT* (Rapidly-exploring Random Tree Star) is an extension of the RRT algorithm that guarantees asymptotic optimality. This means that as the number of samples increases, the path found by RRT* converges to the optimal path. RRT* improves upon RRT by rewiring the tree to ensure that the path to each node is optimal, resulting in shorter and more efficient paths.

## RRT*-SMART

RRT*-SMART (RRT*-Short Memory Adaptive Random Tree) is a variant of RRT* that aims to further enhance path quality and convergence speed. It introduces a "smart" sampling technique that biases the sampling around key points around obstacles (called beacons) and a short memory mechanism that helps in maintaining a balance between exploration and exploitation. This results in faster convergence to high-quality paths compared to standard RRT*.

## Informed RRT*

Informed RRT* is an extension of RRT* that focuses on improving the efficiency of the search process. It introduces an ellipsoidal sampling space that is informed by the first path returned by RRT*, effectively reducing the sampling space as the algorithm progresses. This allows Informed RRT* to focus the search on the most promising regions, leading to faster convergence to the optimal path.

## Usage
Notebooks containing the code for RRT, RRT*, RRT*-SMART, and Informed RRT* are included in the repository. </br>
Open the Jupyter notebooks to explore the different RRT algorithms:
   - `RRT.ipynb`
   - `RRTstar.ipynb`
   - `RRTstar-SMART.ipynb`
   - `Informed-RRTstar.ipynb`

To compare these algorithms, an `Algorithm_Testbench.ipynb` notebook has been included, where you can generate random maps and perform a side-by-side comparison of the paths generated by each of the algorithms.

## RRT* vs RRT*-SMART vs Informed RRT*

Random maps were generated and the following images are the results of the RRT*, RRT*-SMART, and Informed RRT* algorithms:

### Map 1

| RRT* | RRT*-SMART | Informed RRT* |
|:---:|:---:|:---:|
| ![RRT* Map 1](images/RRT_star1.png) | ![RRT*-SMART Map 1](images/RRT_star-SMART1.png) | ![Informed RRT* Map 1](images/Informed-RRT_star1.png) |

### Map 2

| RRT* | RRT*-SMART | Informed RRT* |
|:---:|:---:|:---:|
| ![RRT* Map 2](images/RRT_star2.png) | ![RRT*-SMART Map 2](images/RRT_star-SMART2.png) | ![Informed RRT* Map 2](images/Informed-RRT_star2.png) |

### Map 3

| RRT* | RRT*-SMART | Informed RRT* |
|:---:|:---:|:---:|
| ![RRT* Map 3](images/RRT_star3.png) | ![RRT*-SMART Map 3](images/RRT_star-SMART3.png) | ![Informed RRT* Map 3](images/Informed-RRT_star3.png) |

### Map 4

| RRT* | RRT*-SMART | Informed RRT* |
|:---:|:---:|:---:|
| ![RRT* Map 4](images/RRT_star4.png) | ![RRT*-SMART Map 4](images/RRT_star-SMART4.png) | ![Informed RRT* Map 4](images/Informed-RRT_star4.png) |

### Map 5

| RRT* | RRT*-SMART | Informed RRT* |
|:---:|:---:|:---:|
| ![RRT* Map 5](images/RRT_star5.png) | ![RRT*-SMART Map 5](images/RRT_star-SMART5.png) | ![Informed RRT* Map 5](images/Informed-RRT_star5.png) |



## Results
Informed RRT* has a significantly shorter time to compute paths compared to RRT* and RRT*-SMART. This efficiency is evident in the above maps where the paths generated by Informed RRT* are not only computed faster but also exhibit smoother and more direct routes. These paths appear closer to optimal, avoiding unnecessary detours and better navigating through the obstacles. The reduced computational time, lesser sampling points and improved path quality make Informed RRT* a good choice for scenarios requiring quick and efficient path planning.

## Warning
When implementing these algorithms, it is crucial to update the cost of the children nodes whenever a parent node is rewired. This step ensures that the path costs are accurate and the resulting paths are truly optimal. The importance of this update is highlighted in this issue. </br>
This issue is explained here: https://github.com/AtsushiSakai/PythonRobotics/issues/208 </br>
This cost update step is often overlooked, or not mentioned altogether in various explanations of RRT* algorithms but is vital for the correct functioning of any RRT* variant. Failing to update the costs of children nodes can lead to incorrect path costs, severely impacting the quality and accuracy of the generated paths. 
