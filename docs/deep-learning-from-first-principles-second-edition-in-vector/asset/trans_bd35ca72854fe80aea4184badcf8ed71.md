

# 7.3 Octave

############################################################################################################
#
# File : DLfunctions7.R
# Author : Tinniam V Ganesh
# Date : 16 Apr 2018
#
##########################################################################################################

1;

# 定义 Sigmoid 函数
function [A,cache] = sigmoid(Z)
    A = 1 ./ (1 + exp(-Z));
    cache = Z;
end

# 定义 Relu 函数
function [A,cache] = relu(Z)
    A = max(0, Z);
    cache = Z;
end

# 定义 Tanh 函数
function [A,cache] = tanhAct(Z)
    A = tanh(Z);
    cache = Z;
end

# 定义 Softmax 函数
function [A,cache] = softmax(Z)
    # 获取未归一化的概率
    exp_scores = exp(Z');
    # 对每个样本进行归一化
    A = exp_scores ./ sum(exp_scores, 2);
    cache = Z;
end

# 定义稳定 Softmax 函数
function [A,cache] = stableSoftmax(Z)
    # 按每行的最大值进行归一化
    shiftZ = Z' - max(Z', [], 2);
    exp_scores = exp(shiftZ);
    # 对每个样本进行归一化
    A = exp_scores ./ sum(exp_scores, 2);
    # disp("sm")
    # disp(A);
    cache = Z;
end

# 定义 Relu 导数
function [dZ] = reluDerivative(dA, cache)
    Z = cache;
    dZ = dA;
    # 获取大于 0 的元素
    a = (Z > 0);
    # 仅选择 Z > 0 的那些元素
    dZ = dZ .* a;
end

# 定义 Sigmoid 导数
function [dZ] = sigmoidDerivative(dA, cache)
    Z = cache;
    s = 1 ./ (1 + exp(-Z));
    dZ = dA .* s .* (1 - s);
end

# 定义 Tanh 导数
function [dZ] = tanhDerivative(dA, cache)
    Z = cache;
    a = tanh(Z);
    dZ = dA .* (1 - a .^ 2);
end

# 用 1 填充 Y=1 所在行的矩阵
# 如果 K 不是 3 或 10，此函数可能需要修改
# 此函数用于计算 Softmax 导数
function [Y1] = popMatrix(Y, numClasses)
    Y1 = zeros(length(Y), numClasses);
    if (numClasses == 3) # 针对 3 个输出类别
        Y1(Y == 0, 1) = 1;
        Y1(Y == 1, 2) = 1;
        Y1(Y == 2, 3) = 1;
    elseif (numClasses == 10) # 针对 10 个输出类别
        Y1(Y == 0, 1) = 1;
        Y1(Y == 1, 2) = 1;
        Y1(Y == 2, 3) = 1;
        Y1(Y == 3, 4) = 1;
        Y1(Y == 4, 5) = 1;
        Y1(Y == 5, 6) = 1;
        Y1(Y == 6, 7) = 1;
        Y1(Y == 7, 8) = 1;
        Y1(Y == 8, 9) = 1;
        Y1(Y == 9, 10) = 1;
    endif
end

# 定义 Softmax 导数
function [dZ] = softmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # 获取未归一化的概率
    shiftZ = Z' - max(Z', [], 2);
    exp_scores = exp(shiftZ);
    # 对每个样本进行归一化
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi
    yi = popMatrix(Y, numClasses);
    dZ = probs - yi;
end

# 定义稳定 Softmax 导数
function [dZ] = stableSoftmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # 获取未归一化的概率
    exp_scores = exp(Z');
    # 对每个样本进行归一化
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi

