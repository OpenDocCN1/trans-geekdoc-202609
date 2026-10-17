

```python
import numpy as np
from scipy.special import expit
import sys


class `MLPGradientCheck`(`object`):
    """ 前馈神经网络 / 多层感知器分类器。

    Parameters
    ------------
    `n_output` : int
      输出单元的数量，应等于
      唯一类别标签的数量。

    `n_features` : int
      目标数据集中的特征数（维度）。
      应等于 `X` 数组中的列数。

    `n_hidden` : int (default: 30)
      隐藏单元的数量。

    `l1` : float (default: 0.0)
      L1 正则化的 Lambda 值。
      如果 `l1`=0.0（默认值），则不进行正则化。

    `l2` : float (default: 0.0)
      L2 正则化的 Lambda 值。
      如果 `l2`=0.0（默认值），则不进行正则化。

    `epochs` : int (default: 500)
      遍历训练集的次数。

    `eta` : float (default: 0.001)
      学习率。

    `alpha` : float (default: 0.0)
      动量常数。乘以前一个时代 `t`-1 的梯度以提高
      学习速度
      `w(t)` := `w(t)` - (`grad(t)` + `alpha`*`grad(t)`-1)

    `decrease_const` : float (default: 0.0)
      递减常数。在每个时代后通过 `eta` / (1 + `epoch`*`decrease_const`) 缩小学习率。

    `shuffle` : bool (default: False)
      如果为 True，则在每个时代打乱训练数据以防止循环。

    `minibatches` : int (default: 1)
      将训练数据分为 `k` 个小批量以提高效率。
      如果 `k`=1（默认值），则为普通梯度下降学习。

    `random_state` : int (default: None)
      设置用于打乱和初始化权重的随机状态。

    Attributes
    -----------
    `cost_` : list
      每个时代后的平方误差之和。

    """
    def `__init__`(`self`, `n_output`, `n_features`, `n_hidden`=30,
                 `l1`=0.0, `l2`=0.0, `epochs`=500, `eta`=0.001, 
                 `alpha`=0.0, `decrease_const`=0.0, `shuffle`=True, 
                 `minibatches`=1, `random_state`=None):

        `np.random.seed`(`random_state`)
        `self.n_output` = `n_output`
        `self.n_features` = `n_features`
        `self.n_hidden` = `n_hidden`
        `self.w1`, `self.w2` = `self._initialize_weights`()
        `self.l1` = `l1`
        `self.l2` = `l2`
        `self.epochs` = `epochs`
        `self.eta` = `eta`
        `self.alpha` = `alpha`
        `self.decrease_const` = `decrease_const`
        `self.shuffle` = `shuffle`
        `self.minibatches` = `minibatches`

    def `_encode_labels`(`self`, `y`, `k`):
        """将标签编码为 one-hot 表示

        Parameters
        ------------
        `y` : array, shape = [`n_samples`]
            目标值。

        Returns
        -----------
        `onehot` : array, shape = (`n_labels`, `n_samples`)

        """
        `onehot` = `np.zeros`((`k`, `y.shape`[0]))
        for `idx`, `val` in `enumerate`(`y`):
            `onehot`[`val`, `idx`] = 1.0
        return `onehot`

    def `_initialize_weights`(`self`):
        """使用小随机数初始化权重。"""
        `w1` = `np.random.uniform`(-1.0, 1.0, size=`self.n_hidden`*(`self.n_features` + 1))
        `w1` = `w1.reshape`(`self.n_hidden`, `self.n_features` + 1)
        `w2` = `np.random.uniform`(-1.0, 1.0, size=`self.n_output`*(`self.n_hidden` + 1))
        `w2` = `w2.reshape`(`self.n_output`, `self.n_hidden` + 1)
        return `w1`, `w2`

    def `_sigmoid`(`self`, `z`):
        """计算逻辑函数（sigmoid）

        使用 `scipy.special.expit` 避免非常小的输入值 `z`
        时出现溢出错误。

        """
        # return 1.0 / (1.0 + `np.exp`(-`z`))
        return `expit`(`z`)

    def `_sigmoid_gradient`(`self`, `z`):
        """计算逻辑函数的梯度"""
        `sg` = `self._sigmoid`(`z`)
        return `sg` * (1 - `sg`)

    def `_add_bias_unit`(`self`, `X`, `how`='column'):
        """在索引 0 处向数组添加偏置单元（1 的列或行）"""
        if `how` == 'column':
            `X_new` = `np.ones`((`X.shape`[0], `X.shape`[1]+1))
            `X_new`[:, 1:] = `X`
        elif `how` == 'row':
            `X_new` = `np.ones`((`X.shape`[0]+1, `X.shape`[1]))
            `X_new`[1:, :] = `X`
        else:
            raise `AttributeError`('`how` must be `column` or `row`')
        return `X_new`

    def `_feedforward`(`self`, `X`, `w1`, `w2`):
        """计算前馈步骤

        Parameters
        -----------
        `X` : array, shape = [`n_samples`, `n_features`]
          带有原始特征的输入层。

        `w1` : array, shape = [`n_hidden_units`, `n_features`]
          输入层 -> 隐藏层的权重矩阵。

        `w2` : array, shape = [`n_output_units`, `n_hidden_units`]
          隐藏层 -> 输出层的权重矩阵。

        Returns
        ----------
        `a1` : array, shape = [`n_samples`, `n_features`+1]
          带有偏置单元的输入值。

        `z2` : array, shape = [`n_hidden`, `n_samples`]
          隐藏层的净输入。

        `a2` : array, shape = [`n_hidden`+1, `n_samples`]
          隐藏层的激活值。

        `z3` : array, shape = [`n_output_units`, `n_samples`]
          输出层的净输入。

        `a3` : array, shape = [`n_output_units`, `n_samples`]
          输出层的激活值。

        """
        `a1` = `self._add_bias_unit`(`X`, `how`='column')
        `z2` = `w1.dot`(`a1.T`)
        `a2` = `self._sigmoid`(`z2`)
        `a2` = `self._add_bias_unit`(`a2`, `how`='row')
        `z3` = `w2.dot`(`a2`)
        `a3` = `self._sigmoid`(`z3`)
        return `a1`, `z2`, `a2`, `z3`, `a3`

    def `_L2_reg`(`self`, `lambda_`, `w1`, `w2`):
        """计算 L2 正则化成本"""
        return (`lambda_`/2.0) * (`np.sum`(`w1`[:, 1:] ** 2) + `np.sum`(`w2`[:, 1:] ** 2))

    def `_L1_reg`(`self`, `lambda_`, `w1`, `w2`):
        """计算 L1 正则化成本"""
        return (`lambda_`/2.0) * (`np.abs`(`w1`[:, 1:]).sum() + `np.abs`(`w2`[:, 1:]).sum())

    def `_get_cost`(`self`, `y_enc`, `output`, `w1`, `w2`):
        """计算成本函数。

        `y_enc` : array, shape = (`n_labels`, `n_samples`)
          one-hot 编码的类别标签。

        `output` : array, shape = [`n_output_units`, `n_samples`]
          输出层的激活值（前馈）

        `w1` : array, shape = [`n_hidden_units`, `n_features`]
          输入层 -> 隐藏层的权重矩阵。

        `w2` : array, shape = [`n_output_units`, `n_hidden_units`]
          隐藏层 -> 输出层的权重矩阵。

        Returns
        ---------
        `cost` : float
          正则化成本。

        """
        `term1` = -`y_enc` * (`np.log`(`output`))
        `term2` = (1 - `y_enc`) * `np.log`(1 - `output`)
        `cost` = `np.sum`(`term1` - `term2`)
        `L1_term` = `self._L1_reg`(`self.l1`, `w1`, `w2`)
        `L2_term` = `self._L2_reg`(`self.l2`, `w1`, `w2`)
        `cost` = `cost` + `L1_term` + `L2_term`
        return `cost`

    def `_get_gradient`(`self`, `a1`, `a2`, `a3`, `z2`, `y_enc`, `w1`, `w2`):
        """使用反向传播计算梯度步骤。

        Parameters
        ------------
        `a1` : array, shape = [`n_samples`, `n_features`+1]
          带有偏置单元的输入值。

        `a2` : array, shape = [`n_hidden`+1, `n_samples`]
          隐藏层的激活值。

        `a3` : array, shape = [`n_output_units`, `n_samples`]
          输出层的激活值。

        `z2` : array, shape = [`n_hidden`, `n_samples`]
          隐藏层的净输入。

        `y_enc` : array, shape = (`n_labels`, `n_samples`)
          one-hot 编码的类别标签。

        `w1` : array, shape = [`n_hidden_units`, `n_features`]
          输入层 -> 隐藏层的权重矩阵。

        `w2` : array, shape = [`n_output_units`, `n_hidden_units`]
          隐藏层 -> 输出层的权重矩阵。

        Returns
        ---------

        `grad1` : array, shape = [`n_hidden_units`, `n_features`]
          权重矩阵 `w1` 的梯度。

        `grad2` : array, shape = [`n_output_units`, `n_hidden_units`]
            权重矩阵 `w2` 的梯度。

        """
        # backpropagation
        `sigma3` = `a3` - `y_enc`
        `z2` = `self._add_bias_unit`(`z2`, `how`='row')
        `sigma2` = `w2.T.dot`(`sigma3`) * `self._sigmoid_gradient`(`z2`)
        `sigma2` = `sigma2`[1:, :]
        `grad1` = `sigma2.dot`(`a1`)
        `grad2` = `sigma3.dot`(`a2.T`)

        # regularize
        `grad1`[:, 1:] += (`w1`[:, 1:] * (`self.l1` + `self.l2`))
        `grad2`[:, 1:] += (`w2`[:, 1:] * (`self.l1` + `self.l2`))

        return `grad1`, `grad2`

    def `_gradient_checking`(`self`, `X`, `y_enc`, `w1`, `w2`, `epsilon`, `grad1`, `grad2`):
        """ 应用梯度检查（仅用于调试）

        Returns
        ---------
        `relative_error` : float
          数值近似梯度与反向传播梯度之间的相对误差。

        """
        `num_grad1` = `np.zeros`(`np.shape`(`w1`))
        `epsilon_ary1` = `np.zeros`(`np.shape`(`w1`))
        for `i` in `range`(`w1.shape`[0]):
            for `j` in `range`(`w1.shape`[1]):
                `epsilon_ary1`[`i`, `j`] = `epsilon`
                `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`, `w1` - `epsilon_ary1`, `w2`)
                `cost1` = `self._get_cost`(`y_enc`, `a3`, `w1`-`epsilon_ary1`, `w2`)
                `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`, `w1` + `epsilon_ary1`, `w2`)
                `cost2` = `self._get_cost`(`y_enc`, `a3`, `w1` + `epsilon_ary1`, `w2`)
                `num_grad1`[`i`, `j`] = (`cost2` - `cost1`) / (2 * `epsilon`)
                `epsilon_ary1`[`i`, `j`] = 0

        `num_grad2` = `np.zeros`(`np.shape`(`w2`))
        `epsilon_ary2` = `np.zeros`(`np.shape`(`w2`))
        for `i` in `range`(`w2.shape`[0]):
            for `j` in `range`(`w2.shape`[1]):
                `epsilon_ary2`[`i`, `j`] = `epsilon`
                `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`, `w1`, `w2` - `epsilon_ary2`)
                `cost1` = `self._get_cost`(`y_enc`, `a3`, `w1`, `w2` - `epsilon_ary2`)
                `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`, `w1`, `w2` + `epsilon_ary2`)
                `cost2` = `self._get_cost`(`y_enc`, `a3`, `w1`, `w2` + `epsilon_ary2`)
                `num_grad2`[`i`, `j`] = (`cost2` - `cost1`) / (2 * `epsilon`)
                `epsilon_ary2`[`i`, `j`] = 0

        `num_grad` = `np.hstack`((`num_grad1.flatten`(), `num_grad2.flatten`()))
        `grad` = `np.hstack`((`grad1.flatten`(), `grad2.flatten`()))
        `norm1` = `np.linalg.norm`(`num_grad` - `grad`)
        `norm2` = `np.linalg.norm`(`num_grad`)
        `norm3` = `np.linalg.norm`(`grad`)
        `relative_error` = `norm1` / (`norm2` + `norm3`)
        return `relative_error`

    def `predict`(`self`, `X`):
        """预测类别标签

        Parameters
        -----------
        `X` : array, shape = [`n_samples`, `n_features`]
          带有原始特征的输入层。

        Returns:
        ----------
        `y_pred` : array, shape = [`n_samples`]
          预测的类别标签。

        """
        if `len`(`X.shape`) != 2:
            raise `AttributeError`('`X` must be a [`n_samples`, `n_features`] array.\n'
                                 'Use `X[:,None]` for 1-feature classification,'
                                 '\nor `X[[i]]` for 1-sample classification')

        `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`, `self.w1`, `self.w2`)
        `y_pred` = `np.argmax`(`z3`, `axis`=0)
        return `y_pred`

    def `fit`(`self`, `X`, `y`, `print_progress`=False):
        """从训练数据中学习权重。

        Parameters
        -----------
        `X` : array, shape = [`n_samples`, `n_features`]
          带有原始特征的输入层。

        `y` : array, shape = [`n_samples`]
          目标类别标签。

        `print_progress` : bool (default: False)
          将进度作为时代数打印到 stderr。

        Returns:
        ----------
        `self`

        """
        `self.cost_` = []
        `X_data`, `y_data` = `X.copy`(), `y.copy`()
        `y_enc` = `self._encode_labels`(`y`, `self.n_output`)

        `delta_w1_prev` = `np.zeros`(`self.w1.shape`)
        `delta_w2_prev` = `np.zeros`(`self.w2.shape`)

        for `i` in `range`(`self.epochs`):

            # adaptive learning rate
            `self.eta` /= (1 + `self.decrease_const`*`i`)

            if `print_progress`:
                `sys.stderr.write`('\rEpoch: %d/%d' % (`i`+1, `self.epochs`))
                `sys.stderr.flush`()

            if `self.shuffle`:
                `idx` = `np.random.permutation`(`y_data.shape`[0])
                `X_data`, `y_data` = `X_data`[`idx`], `y_data`[`idx`]

            `mini` = `np.array_split`(`range`(`y_data.shape`[0]), `self.minibatches`)
            for `idx` in `mini`:

                # feedforward
                `a1`, `z2`, `a2`, `z3`, `a3` = `self._feedforward`(`X`[`idx`], `self.w1`, `self.w2`)
                `cost` = `self._get_cost`(`y_enc`=`y_enc`[:, `idx`],
                                      `output`=`a3`,
                                      `w1`=`self.w1`,
                                      `w2`=`self.w2`)
                `self.cost_`.append(`cost`)

                # compute gradient via backpropagation
                `grad1`, `grad2` = `self._get_gradient`(`a1`=`a1`, `a2`=`a2`,
                                                  `a3`=`a3`, `z2`=`z2`,
                                                  `y_enc`=`y_enc`[:, `idx`],
                                                  `w1`=`self.w1`,
                                                  `w2`=`self.w2`)

                ## start gradient checking
                `grad_diff` = `self._gradient_checking`(`X`=`X`[`idx`], `y_enc`=`y_enc`[:, `idx`],
                                                  `w1`=`self.w1`, `w2`=`self.w2`,
                                                  `epsilon`=1e-5,
                                                  `grad1`=`grad1`, `grad2`=`grad2`)

                if `grad_diff` <= 1e-7:
                    print('Ok: %s' % `grad_diff`)
                elif `grad_diff` <= 1e-4:
                    print('Warning: %s' % `grad_diff`)
                else:
                    print('PROBLEM: %s' % `grad_diff`)

                # update weights; [`alpha` * `delta_w_prev`] for momentum learning
                `delta_w1`, `delta_w2` = `self.eta` * `grad1`, `self.eta` * `grad2`
                `self.w1` -= (`delta_w1` + (`self.alpha` * `delta_w1_prev`))
                `self.w2` -= (`delta_w2` + (`self.alpha` * `delta_w2_prev`))
                `delta_w1_prev`, `delta_w2_prev` = `delta_w1`, `delta_w2`

        return `self`
```

