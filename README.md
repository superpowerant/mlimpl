# mlimpl
### Machine Learning Implementation
<img src="./pic/logo.jpg" width="400" height="300" alt="mlimpl">

![author: vincen (shields.io)](https://img.shields.io/badge/author-vincen-brightgreen) ![email](https://img.shields.io/badge/email-vincen.nwu%40gmail.com-red) ![build: passing (shields.io)](https://img.shields.io/badge/build-passing-brightgreen) ![python: >= 3.6 (shields.io)](https://img.shields.io/badge/python-%3E%3D3.6-blue) ![NumPy version](https://img.shields.io/badge/NumPy-%3E%3D1.19.2-brightgreen) ![Pandas version](https://img.shields.io/badge/Pandas-%3E%3D1.1.3-brightgreen)

## Introduction
This repository collects some codes that encapsulates commonly used algorithms in the field of machine learning. Most of them are based on Numpy, Pandas or Torch. You can deepen your understanding to related model and algorithm or revise it to get the customized code belongs yourself by referring to this repository. I'm very glad that it can give you a bit of inspiration.
## Why choose my repository?
- Detailed documentation and annotation.
- Guidance for difficulty of algorithm: I will write down the guidance with code comments in the place that there are some difficulties encountered when i implemented it.
## How to use it?
Most implementation of algorithms in this repository are encapsulated to be a class, whose structure is same as sklearn that contains three methods, i.e., fit, predict, score. Here is an instance shown as below:
```python
from Multiple_linear_regression import LinearRegression
from sklearn.datasets import load_boston

X, y = load_boston(return_X_y=True)

reg = LinearRegression()
reg.fit(X, y)
y_pred = reg.predict(X)
score = reg.score(X, y)
```
As your seen, it is same as sklearn.

## Contents
***1. Deep Learning***

This part contains the code about deep learning algorithm. Most of them are implemented by torch or tensorflow. Here are some brief introduction about this guys.
- **1. Gan**
    - Generative Adversarial Networks(Gan). I implemented it using tensorflow 1 and applied it to generate mnist dataset.
- **2. Cnn**
    - Convolutional Neural Network implemented by tensorflow 1 to recognize digital verification code.
- **3. ann_by_matlab**
    - A toy example that implementation of artificial neural network using matlab which is applied to mnist classification problem.
    - It worth mentioning that the program for reading mnist dataset to memory is comes from the internet.
- **4. High Confidence Predictions for Unrecognizable Images**
    - A simple demo about adversarial examples. More precisely, Using genetic algorithm to generate some adversarial examples.
    - Reference: *Anh Nguyen, Jason Yosinski and Jeff Clune. Deep Neural Networks are Easily Fooled: High Confidence Predictions for Unrecognizable Images. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2015, pp. 427-436.*
- **autograd without torch**
    - A simpy system which to calculate gradient automatically without torch. You can use this item to understand the automatic derivation mechanism in torch. Each tensor is represented as a node in computational graph. The edges built by forward propagation decide the path of derivation and the direction of derivation is from top to bottom. You can rewrite more operations and elementary functions if you want to build exclusive autograd system.
- **lstm**
  - lstm is a common neural network which is to tackle serialized data. Compared with RNN, It can handle vanishing
      gradient problem by preserving long-term memory.
  - Reference:
      1. *https://pytorch.org/docs/stable/generated/torch.nn.LSTM.html?highlight=lstm#torch.nn.LSTM*
      2. *2022 Summer Short Course in TianYuan Mathematical Center in Central China:
              Mathematical Theory and Applications of Deep Learning
              Prof. Haizhao Yang (University of Maryland,CollegePark)
              Course Video :Course(2) replay in http://tmcc.whu.edu.cn/info/1262/2052.htm*
      3. *https://www.bilibili.com/video/BV1zq4y1m7aH?spm_id_from=333.337.search-card.all.click*
- **VAE**
  - VAE is abbreviation of Variational Auto Encoder, which combine the variational inference and autoencoder to creat a great method of representation learning. I implemented the demo mentioned in original paper.
  - Reference: *Diederik P Kingma and Max Welling. Auto-encoding variational bayes, 2022.*
- **resnet50**
  - In my project, I was required to convert Imagenet1K into 1000 HDF5 files due to the file quantity restrictions imposed by the Supercomputing Center of Wuhan University. These files were named in accordance with their respective classes. Following this, I had to customize a dataloader for training, as demonstrated in `train_reader.py`. In addition, I encountered a CPU bottleneck issue. However, I successfully resolved it by allocating more CPU cores and setting `num_works` and `prefetch_factor` to larger values. Furthermore, I set `pin_memory` to true during the construction of the dataloader, which kept the Volatile GPU-Util busier. One potential pitfall to be aware of is that the Imagenet1K training dataset contains a small number of grayscale images and images with four channels. This is an important consideration when customizing your own dataloader.
  - The model's code draws inspiration from the original ResNet code, authored by Kaiming He. But maybe due to the optimization policy, I only achieve 68.1% validation accuracy after training 64 epochs. which is far from 78% mentioned in paper. Don't forget to create folder named `res` when you use my code to train model and save it. 
  - Reference:
    - *Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. Deep residual learning for image recognition. CoRR, abs/1512.03385, 2015. URL http://arxiv.org/abs/1512.03385.*
- **TransferLearning**
  - In this implementation, I employ transfer learning technique to address the challenge posed by the APTOS 2019 Blindness Detection competition on Kaggle, which aims to detect diabetic retinopathy early enough to prevent blindness. Transfer Learning allows you to leverage a smaller dataset and reduce training time, while achieving comparable or even superior performance compared to training from scratch.  
  - The competition details can be found at *https://www.kaggle.com/competitions/aptos2019-blindness-detection/overview*. 
  - The backbone of my solution is the ResNet50 architecture. It can be available through https://download.pytorch.org/models/resnet50-0676ba61.pth. You can also use the weights pretraining by yourself.

***2. Reinforcement Learning*** 
- **1. Env**
    - Some basic reinforcement learning environments.
- **2. EpsilonGreedy**
    - EpsilonGreedy is an implement class of the simplest reinforcement learning method which
    is suitable for single state and finite action(denoted as k in here). It is a revising version
    of greedy method. Its creation is used to avoid Local maximizer problem. Here is a simplest demo which apply this algorithm to the multi-armed bandit problem.
    - Reference: 
        1. *2022 Summer Short Course in TianYuan Mathematical Center in Central China:
        Mathematical Theory and Applications of Deep Learning
        Prof. Haizhao Yang (University of Maryland,CollegePark)
        Course Video :Course(3) replay in http://tmcc.whu.edu.cn/info/1262/2052.htm*
        2. *https://hrl.boyuai.com/chapter/1/%E5%A4%9A%E8%87%82%E8%80%81%E8%99%8E%E6%9C%BA#24-%CF%B5-%E8%B4%AA%E5%BF%83%E7%AE%97%E6%B3%95*
- **3. UCB**
    - In multi-armed bandit problem, the greater the uncertainty of a bandit, the more valuable it is to explore, because it is possible to find that its expected reward is very large after exploration. UCB use Hoeffding's Inequality to formulate the uncertainty of bandit and use a upper bound of value function to identify policy. 
    - Reference: *https://hrl.boyuai.com/chapter/1/%E5%A4%9A%E8%87%82%E8%80%81%E8%99%8E%E6%9C%BA#24-%CF%B5-%E8%B4%AA%E5%BF%83%E7%AE%97%E6%B3%95*
- **4. Markov Decision Process**
  - MRP: Markov Reward process is the simple version of markov decision process which without make action according to π(a|s) at each step.
      agent only needs to change its state and get a deterministic reward expectation E(r|s) at each space according to
      the given state transition matrix(declared as state_trans_matrix in following code).
    - Reference:*https://hrl.boyuai.com/chapter/1/%E9%A9%AC%E5%B0%94%E5%8F%AF%E5%A4%AB%E5%86%B3%E7%AD%96%E8%BF%87%E7%A8%8B*
  - MDP: Markov Decision process is the most general framework in Reinforcement Learning. it is the more complex version of MRP, which consider how to choose the action at each step. I have implemented model-based reinforcement learning and monte carlo method which is model-free reinforcement learning related to offline dataset in this code.
    - Reference:*https://hrl.boyuai.com/chapter/1/%E9%A9%AC%E5%B0%94%E5%8F%AF%E5%A4%AB%E5%86%B3%E7%AD%96%E8%BF%87%E7%A8%8B*
- **5. PolicyGradient**
  - PolicyGradient is another method whose idea is different from Value Function Method.
        It optimizes the action distribution to maximize E_{A~π}[E(R|A)].
        we use softmax function to simplify this constrained optimization problem.
  - Reference: *2022 Summer Short Course in TianYuan Mathematical Center in Central China:
            Mathematical Theory and Applications of Deep Learning
            Prof. Haizhao Yang (University of Maryland,CollegePark)
            Course Video :Course(3) replay in http://tmcc.whu.edu.cn/info/1262/2052.htm*
- **6. PolicyIter**
    - This class is the implementation of policy iteration to solve model based reinforcement learning problem, thus u
    need to pass the transition matrix of mdp, of the form which same as gym's. This program will rely on following
    process to find a great policy what ur need.
    policy evaluation -> policy improve -> policy evaluation -> policy improve -> .... (until convergence)
    - Reference: 
        1. *2022 Summer Short Course in TianYuan Mathematical Center in Central China:
            Mathematical Theory and Applications of Deep Learning
            Prof. Haizhao Yang (University of Maryland,CollegePark)
            Course Video :Course(3) replay in http://tmcc.whu.edu.cn/info/1262/2052.htm*
       2. Reference:*https://hrl.boyuai.com/chapter/1/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%E7%AE%97%E6%B3%95#433-%E7%AD%96%E7%95%A5%E8%BF%AD%E4%BB%A3%E7%AE%97%E6%B3%95*
- **7. TemporalDifference**
  - You can view temporal difference as a method which is used to revise the estimation of Q(s,a) by online data. Sarsa use temporal difference evaluate action value function, and reset the greedy policy as ε-greedy in policy improvement.
  - Reference:*https://hrl.boyuai.com/chapter/1/%E6%97%B6%E5%BA%8F%E5%B7%AE%E5%88%86%E7%AE%97%E6%B3%95#53-sarsa-%E7%AE%97%E6%B3%95*
- **8. DQN**
  - Above Reinforcement Learning algorithm can not handle the case that the cardinality of state space is an infinite, which causes that action set cannot be recorded as tabular form. A common solution is to use neural networks to approximate the action value function. More precisely, we want to train a neural network whose input is state s and its output is a vector that contains (Q(s,a1), Q(s,a2), ..., Q(s, an)). A natural question raised is how to tackle the problem that the cardinalities of state space and action space are both infinite. There are two ways to answer this question, one is discrete action space to make DQN adapt to this case and the other guy is altering the structure of neural network. In our code, we will illustrate the first under the environment named Pendulum in the part of Double DQN.
  - Reference: 
    - *https://www.bilibili.com/video/BV1mB4y1g77R/?spm_id_from=333.999.0.0&vd_source=8c6dbad02305a4d2c6919e458c8c03b5*
    - *https://hrl.boyuai.com/chapter/2/dqn%E7%AE%97%E6%B3%95*
- **9. DoubleDQN**
  - Double DQN is a improved method based on DQN to fix the problem that the process of training DQN is unstable. It imports target network to achieve better performance.
  - Reference:
    - *https://www.youtube.com/watch?v=X2-56QN79zc&list=PLvOO0btloRntS5U8rQWT9mHFcUdYOUmIC&index=2&ab_channel=ShusenWang*
    - *https://hrl.boyuai.com/chapter/2/dqn%E6%94%B9%E8%BF%9B%E7%AE%97%E6%B3%95*
- **10. DualingDQN**
  - Dualing DQN revise a detail in TD target to achieve better performance than DQN and Double DQN. 
  - Reference:
    - *https://www.youtube.com/watch?v=DBux6cA0EoM&list=PLvOO0btloRntS5U8rQWT9mHFcUdYOUmIC&index=3&ab_channel=ShusenWang*
    - *https://hrl.boyuai.com/chapter/2/dqn%E6%94%B9%E8%BF%9B%E7%AE%97%E6%B3%95#84-dueling-dqn*
- **11. PolicyGradient**
  - Policy Gradient is a policy based algorithm in reinforcement learning, which use a neural network to encode policy directly. I have implemented REINFORCE algorithm in my code.
  - Reference:
    - Richard S Sutton, David McAllester, Satinder Singh, and Yishay Mansour. Policy gradient methods for reinforcement learning with function approximation. In S. Solla, T. Leen, and K. Müller, editors, Advances in Neural Information Processing Systems, volume 12. MIT Press, 1999. URL https://proceedings.neurips.cc/paper_files/paper/1999/file/464d828b85b0bed98e80ade0a5c43b0f-Paper.pdf.
    - *https://www.youtube.com/watch?v=qI0vyfR2_Rc&list=PLvOO0btloRnsiqM72G4Uid0UWljikENlU&index=3&ab_channel=ShusenWang*
    - *https://hrl.boyuai.com/chapter/2/%E7%AD%96%E7%95%A5%E6%A2%AF%E5%BA%A6%E7%AE%97%E6%B3%95*
- **12. Actor-Critic**
  - Actor-Critic learns both value network and policy network. Value network serves as the referee to determine the quality of actor. Actor plays the role of an athlete that caters to the preferences of the referee. 
  - Reference:
    - *https://www.youtube.com/watch?v=yNEqbptitZs&list=PLvOO0btloRnujjKTwoC5fOJxC7nmiQ4c4&ab_channel=ShusenWang*
    - *https://hrl.boyuai.com/chapter/2/actor-critic%E7%AE%97%E6%B3%95*

***3. Statistical Learning***

This part records the classic Statistical Learning, most of them are implemented in my undergraduate.
- **1. linear_model**
    - Linear Regression
      - I have implemented a linear regression model which is the simplest machine learning algorithm used various algorithm including analytical formula, gradient descent and adam optimizer.
      - Reference: *Sebastian Ruder. An overview of gradient descent optimization algorithms. CoRR, abs/1609.04747,2016.*
    - Ridge
        - Using the same method as above to complete the implementation of ridge.
    - Lasso
      - Coordinate descent and Iterated Ridge Regression is used in here to solve lasso model.
      - Iterated Ridge Regression.
        - Use approximation of *L1* norm mentioned in following paper to transform the optimization problem of lasso to be an iterated ridge question.
        - Reference: *Mark Schmidt. Least squares optimization with l1-norm regularization. CS542B Project Report,504:195–221, 2005.*
- **2. DecisionTree**
    - I have implemented ID3, which uses information gain as its criterion for building decision tree model; C4.5, which improves the performance of ID3 by changing the criterion to be information gain ratio.
      - ***Note that above two implementation only support discrete features/labels.***
    - Cart
        - CartRegressor aims for solving regression problem using tree model. This implementation can handle both continuous and discrete feature.
        - For more details, please refer to *统计学习方法—李航*.
    - ***There exists some decision tree implementation in ipynb file,which hasn't been encapsulated as class.***
- **3. NaiveBayes**
    - MultinomialNB
        -  Naive Bayes to solve discrete labels whose priori obey multinomial distribution.
         - You need to ensure the incoming features are discrete to make this implementation effective.
       -  For more details refer to *统计学习方法—李航*.
    - GaussianNB
        -  Similar method as above but supposing the priori and likelihood are obey Gaussian. Therefore, this implementation can handle continuous features/label.
        -  For more details refer to *机器学习—周志华*.
- **4. SVM**
   - Support vector machine solved by sequential minimal optimization algorithm for classification task.
   - Reference:
       - [1] *John Platt. Sequential minimal optimization: A fast algorithm for training support vector machines. Technical Report MSR-TR-98-14, Microsoft, April 1998.*
       - [2] *统计学习方法—李航*.
- **5. KMeans++**
     - Common unsupervised algorithm for cluster improved from kmeans.
    - *For more details refer to KMeans documentation in sklearn.*
- **6. rejection_sampling**
    - Rejection sampling method.A effective method to sample from a complex distribution.
- **7. l1/2**
    - l1/2 algorithm is a improved variant algorithm of lasso.
        - Similar with the method for solving lasso, i.e., iterated ridge regression.The way for solving this non-convex regularization framework is to transform it to iterated lasso or ridge regression.
        - Reference: *Xu, Z., Chang, X., Xu, F., & Zhang, H. (2012). L1/2 regularization: a thresholding representation theory and a fast solver. IEEE transactions on neural networks and learning systems, 23(7), 1013–1027. https://doi.org/10.1109/TNNLS.2012.2197412*
    - the file named energy_predict.py is the distributed application on Energy Consumption Field of CNC Machine Tools.Distributed platform using here is Spark.
- **8. xgboost**
    - eXtreme Gradient Boosting(xgboost) is a class that implement a scalable tree boosting system proposed by TianQi Chen.
        - i have implemented the exact greedy and approximate algorithm for split finding.
        - Reference: *Tianqi Chen and Carlos Guestrin. Xgboost: A scalable tree boosting system. CoRR,abs/1603.02754, 2016.*
- **9. RandomForest**
    - A random forest classifier.A random forest is a meta estimator that fits a number of decision tree classifiers on various sub-samples of the dataset and uses averaging to improve the predictive accuracy and control over-fitting.
- **10. GMM**
    - Gaussian Mixture Model(single dimension) solved by EM.
    - Reference: *[Expectation Maximization-Yi Da Xu](https://github.com/roboticcam/machine-learning-notes/blob/master/files/em.pdf)*
- **11. MCMC**
    - Markov Chain Monte Carlo.
        -  Metropolis–Hastings Algorithm
        -  Gibbs Sampling(To Be Completed).
    - Reference: *[Markov Chain Monte Carlo-Yi Da Xu](https://github.com/roboticcam/machine-learning-notes/blob/master/files/markov_chain_monte_carlo.pdf.)*
- **12. Spectral Clustering**
  - Spectral clustering is a technique with roots in graph theory, where the approach is used to identify communities of nodes in a graph based on the edges connecting them. The method is flexible and allows us to cluster non graph data as well.
Spectral clustering uses information from the eigenvalues (spectrum) of special matrices built from the graph or the data set.
  - Reference: *https://www.cnblogs.com/pinard/p/6221564.html*
