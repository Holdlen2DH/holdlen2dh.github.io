# 树形分类算法综述
## 1 决策树

### 1.1 ID3
ID3是决策树学习的典型实现，由澳大利亚计算机科学家罗斯$\cdot$昆兰(J. Ross Quinlan, 1943-)提出。
ID3: Induction of decision trees
### 1.2 C4.5
### 1.3 CART

### 1.4 节点划分
#### 1.4.1 信息增益
$$Ent(D) = -\sum_{k = 1}^{|y|}p_{k}log_2(p_{k})$$
$$Gain(D, a) = Ent(D) - \sum_{v = 1}^{V}\frac{|D^v|}{|D|}Ent(D^v)$$
#### 1.4.2 增益率
$$Gain\_ratio(D, a) = \frac{Gain(D, a)}{IV(a)}$$
$$IV(a) = -\sum_{v = 1}^{V}\frac{|D^v|}{|D|}log_{2}(\frac{|D^v|}{|D|})$$
#### 1.4.3 基尼系数
$$Gini(D) = \sum_{k = 1}^{|y|}\sum_{k^{'}\ne k}p_{k}p_{k^{'}} = 1 - \sum_{k = 1}^{|y|}p_{k}^2$$
$$Gini\_index(D, a) = \sum_{v = 1}^{V}\frac{|D^v|}{|D|}Gini(D^v)$$

#### 1.4.4 连续值节点划分

## 2 基于树的多分类系统
### 2.1 梯度提升决策树(GBDT)
### 2.2 随机森林(RF)
### 2.3 极度随机森林(ERT)
### 2.4 深度神经决策森林(DNDT)
### 2.5 XGBoost
$$\hat{y}_i = \sum\limits_{k = 1}^{K}f_k(\bm{x}_i), f_k \in \mathcal{F}$$
$$\mathcal{L} = \sum\limits_{i}l(\hat{y}_i, y_i) + \sum\limits_{k}\Omega(f_k), \quad where \quad \Omega(f) = \gamma T + \frac{1}{2}\lambda||w||^2$$
$$\mathcal{L}^{(t)} = \sum\limits_{i = 1}^{n}l(y_i, \hat{y}_{i}^{(t - 1)} + f_{t}(\bm{x}_i)) + \Omega(f_t)$$
$$\mathcal{L}^{(t)} \simeq \sum\limits_{i = 1}^{n}[l(y_i, \hat{y}_i^{(t - 1)}) + g_{i}f_{t}(\bm{x}_{i}) + \frac{1}{2}h_{i}f_t^2(\bm{x}_i)] + \gamma T + \frac{1}{2}\lambda\sum\limits_{j = 1}^{T}w_j^2$$
### 2.6 LightGBM


## 参考文献
1. J. R. Quinlan. [Induction of decision trees](https://link.springer.com/article/10.1007/BF00116251). *Machine Learning*, 1(1): 81-106, 1986.
1. J. R. Quinlan. C4.5: programs for machine learning. Morgan Kaufmann, San Meteo, CA, 1993.
1. L. Breiman, J. Fridman, C. J. Stone and R. A. Olshen. Classification and regression trees, Chapman & Hall/CRC, Boca Raton, FL, 1984.
1. L. Breiman. [Random forests](https://link.springer.com/article/10.1023/A:1010933404324). *Machine Learning*, 54(1): 5-32, 2001.
1. P. Geurts, D. Ernst, and L. Wehekel. [Extremely randomized trees](https://link.springer.com/article/10.1007/s10994-006-6226-1). *Machine Learning*, 63(1): 3-42, 2006.
1. Y. Freund and R. E. Schapire. [A Decision-Theoretic Generalization of On-Line Learning and an Application to Boosting](https://www.sciencedirect.com/science/article/pii/S002200009791504X). *Journal of Computer and System Sciences*, 55(1): 119-139, 1997.
1. J. H. Friedman. [Greedy function approximation: A gradient boosting machine](https://projecteuclid.org/euclid.aos/1013203451). *The Annals of Statistics*, 29(5): 1189-1232, 2001.
1. T. Chen and C. Guestrin. [XGBoost: A Scalable Tree Boosting System](https://arxiv.org/abs/1603.02754). *e-Print: arXiv*, 2016.
1. G. Ke, Q. Meng, T. Finley, T. Wang, W. Chen, W. Ma. Q. Ye, and T.-Y. Liu. [LightGBM: A Highly Efficient Gradient Boosting Decision Tree](https://papers.nips.cc/paper/6907-lightgbm-a-highly-efficient-gradient-boosting-decision-tree). *31st Conference on Neural Information Processing Systems (NIPS 2017)*, 3146-3154, 2017.
1. P. Kontschieder, M. Fiterau, A. Criminisi, and S. R. Bulo. [Deep Neural Decision Forests](https://ieeexplore.ieee.org/document/7410529/). *Computer Vision (ICCV), 2015 IEEE International Conference on*, Santiago, Chile, 7-13 Dec. 2015, 1467-1475, 2015.
1. 周志华. 机器学习. 清华大学出版社，北京，2016.
1. Z.-H. Zhou and J. Feng. [Deep Forest: Towards An Alternative to Deep Neural Networks](https://arxiv.org/abs/1702.08835). *e-Print: arXiv*, 2017. 
