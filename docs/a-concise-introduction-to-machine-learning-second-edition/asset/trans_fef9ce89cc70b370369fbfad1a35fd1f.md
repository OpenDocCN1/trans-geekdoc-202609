

```mat
function [idx,K,MU,SIGMA] = InferDP(V,alpha,lambda,m,Psi,nu,iter)
  % 输入:
  % V: 数据,
  % alpha: 先验浓度参数,
  % m: 先验均值向量,
  % lambda: 先验均值比例,
  % Psi: 先验逆尺度矩阵，
  % nu: 先验自由度,
  % iter: 迭代次数。
  % 输出:
  % idx: 聚类分配索引向量,
  % K: 聚类数量
  % MU: 从每个聚类的后验正态-逆Wishart 分布中采样的均值数组。
  % SIGMA: 从每个聚类的后验正态-逆Wishart 分布中采样的方差数组。
  % 样本数量。
  N = size(V,1); % 样本数
  K = 0; % 聚类数
  idx = -zeros(N,1); % 聚类分配向量
  nk = []; % 聚类大小向量
  % 对于每个聚类:
  M = []; % 后验位置向量
  LAMBDA = []; % 后验均值比例
  PSI = []; % 后验逆尺度矩阵的 Cholesky 分解
  NU = []; % 后验自由度
  SIGMA = []; %协方差矩阵
  MU = []; % 均值
  % 使用 Cholesky 分解确保正定性
  Psi = chol(Psi);
  % 随机顺序考虑样本
  order = randperm(N);
  % 初始化聚类分配
  for n = 1:N
    v = V(order(n),);
    % 计算聚类分配概率
    p = zeros(1,K);
    for k = 1:K
      p(k) = nk(k)/(n-1+alpha)*mvnpdf(v',MU(:,k),SIGMA(:,k));
    end
    p(K+1)=alpha/(n-1+alpha)*mvnpdf(v',m,Psi);
    p = p/sum(p);
    % 采样新的指示变量
    l = randrnd(K+1,true,p);
    idx(order(n)) = l;
```

列表 6.7: MATLAB 中的狄利克过程方法。Python 请访问 https://github.com/ACFoul/Clustering-Python。

```matlab
if l
    % 更新样本所属的聚类
    postlambda = LAMBDA(l);
    % 对 Cholesky 分解进行更新以保持正定性
    update = sqrt(LAMBDA(l)/postlambda) * (v' - M(l));
    PSI(:,l) = choldupate(PSI(:,l),update,'+');
    M(l,:) = LAMBDA(l)*M(:,l) + v(:)/postlambda;
    NU(l) = NU(l);
    LAMBDA(l) = postlambda;
    SIGMA(:,l) = iwishrnd(PSI(:,l),*PSI(:,l),NU(l));
    MU(l,:) = mvnrnd(M(l,:),SIGMA(:,l),LAMBDA(l));
    nk(l) = nk(l)+1;
else
    % 创建新聚类
    lambda = cat(2,LAMBDA,lambda+1);
    update = sqrt(lambda/(lambda+1)) * (v' - m);
    PSI = cat(3,PSI,choldupate(PSI,update,'+'));
    M = cat(2,M,lambda*m + v')/(lambda+1));
    NU = cat(2,NU,1);
    SIGMA = cat(3,SIGMA,iwishrnd(PSI(:,1),*PSI(:,1),NU(1)));
    MU = cat(2,MU,mvnrnd(M(:,1),SIGMA(:,1),LAMBDA(1)));
    nk = cat(2,nk,1);
    K = K+1;
end
for i=1:iter
    % 随机顺序考虑数据
    n = randperm(N);
    v = v(n);
    l = idx(n);
    % 从数据集中移除该样本并更新其所属的聚类
    nk(l) = nk(l)-1;
    if nk(l) == 0
        % 空聚类
        nk(l) = [];
        PSI(:,l) = [];
        M(l,:) = [];
        NU(l) = [];
        LAMBDA(:,l) = [];
        SIGMA(:,l) = [];
        MU(l,:) = [];
        % 调整聚类编号
        temp = idx(temp);
        idx(temp) = idx(temp)-1;
        K = K-1;
    end
```

列表 6.7: MATLAB 中的狄利克过程方法。Python 请访问 https://github.com/ACFaul/Clustering-Python.

