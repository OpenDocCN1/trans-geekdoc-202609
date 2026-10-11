

## LSTM 类测试代码

```python
dH_next = dH_prev

grads = [dWi, dbi, dWf, dbf, dWo, dbo, dWc, dbc, dWy, dby]

grad_clipping(grads, 5.)

for i, _ in enumerate(self.grads):
    self.grads[i] += grads[i]

return [dWi, dbi, dWf, dbf, dWo, dbo, dWc, dbc, dWy, dby]

def parameters(self):
    return self.params
```

以下代码测试 `LSTM` 类：

```python
T = 3
input_dim, hidden_dim, output_dim = 4, 3, 4
batch_size = 2

Xs = np.random.randn(T, batch_size, input_dim)
Ys = np.random.randint(output_dim, size=(T, batch_size))
# print("Xs", Xs)
# print("Ys", Ys)

lstm = LSTM(input_dim, hidden_dim, output_dim)
Zs, Hs = lstm.forward(Xs)
loss_function = rnn_loss_grad
loss, dZs = loss_function(Zs, Ys)
grads = lstm.backward(dZs)

def rnn_loss():
    lstm.reset_state(batch_size)
    Zs, Hs = lstm.forward(Xs)
    loss_function = rnn_loss_grad
    loss, dZs = loss_function(Zs, Ys)
    return loss

params = lstm.parameters()
numerical_grads = util.numerical_gradient(rnn_loss, params, 1e-6)
diff_error = lambda x, y: np.max(np.abs(x - y))

print("loss", loss)
print("[Wi, bi, Wf, bf, Wo, bo, Wc, bc, Wy, by]")
for i in range(len(grads)):
    print(diff_error(grads[i], numerical_grads[i]))

print("grads", grads[0])
print("numerical_grads", numerical_grads[0])
```

### 测试输出结果

```
loss 4.15897570534243
[Wi, bi, Wf, bf, Wo, bo, Wc, bc, Wy, by]
4.0983714987404213e-10
4.804842887035274e-10
5.574688488332363e-10
5.962706955096197e-10
4.786088983281455e-10
3.3010982580892407e-10
5.250774498359589e-10
7.762481196021964e-10
5.116074152863859e-10
4.973363854077206e-08
grads [[-1.40953185e-06  1.39633673e-05  3.77862529e-05]
 [-2.05605688e-06 -6.94901972e-06 -9.72150550e-06]
 [-1.97703294e-06  2.14765528e-05 -6.23417436e-07]
 [ 2.38579566e-06  3.03502478e-05  5.32372144e-06]
 [-2.43351424e-10 -1.73915908e-09 -1.49094729e-08]
 [ 1.89104848e-08  1.69377027e-07  1.08468341e-07]
 [-6.11087686e-09 -6.70921838e-08 -7.03528265e-09]]
numerical_grads [[-1.40953915e-06  1.39630529e-05  3.77866627e-05]
 [-2.05613304e-06 -6.94910796e-06 -9.72155689e-06]
 [-1.97708516e-06  2.14761542e-05 -6.23501251e-07]
 [ 2.38564724e-06  3.03503889e-05  5.32374145e-06]
 [-4.44089210e-10 -1.77635684e-09 -1.46549439e-08]
 [ 1.86517468e-08  1.69197989e-07  1.08357767e-07]
 [-5.77315973e-09 -6.70574707e-08 -7.10542736e-09]]
```

## GRU 类实现

以下 `GRU` 实现了一个具有 GRU 结构的循环神经网络：

```python
class GRU(object):
    def __init__(self, input_dim, hidden_dim, output_dim, scale=0.01):
        super(GRU, self).__init__()
        self.input_dim, self.hidden_dim, self.output_dim, self.scale = input_dim, hidden_dim, output_dim, scale

        normal = lambda m, n: np.random.randn(m, n) * scale
        three = lambda: (normal(input_dim, hidden_dim), normal(hidden_dim, hidden_dim), np.zeros((1, hidden_dim)))

        Wxu, Whu, bu = three()  # 更新门参数
        Wxr, Whr, br = three()  # 重置门参数
        Wxh, Whh, bh = three()  # 候选隐藏状态参数
        Wy = normal(hidden_dim, output_dim)
        by = np.zeros((1, output_dim))

        self.Wxu, self.Whu, self.bu, self.Wxr, self.Whr, self.br, self.Wxh, self.Whh, self.bh, self.Wy, self.by = Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by
        self.params = [Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by]
        self.grads = [np.zeros_like(param) for param in self.params]
        self.H = None

    def reset_state(self, batch_size):
        self.H = np.zeros((batch_size, self.hidden_dim))

    def forward_step(self, X):
        Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by = self.params
        H = self.H  # previous state
        X = Xs[t]  # 注意：此处引用了外部变量 t 和 Xs，可能为代码片段遗留问题

        U = sigmoid(np.dot(X, Wxu) + np.dot(H, Whu) + bu)
        R = sigmoid(np.dot(X, Wxr) + np.dot(H, Whr) + br)
        H_tilda = np.tanh(np.dot(X, Wxh) + np.dot(R * H, Whh) + bh)
        H = U * H + (1 - U) * H_tilda
        Y = np.dot(H, Wy) + by

        Hs[t] = H
        Ys.append(Y)
        Rs.append(R)
        Us.append(U)
        H_tildas.append(H_tilda)

    def forward(self, Xs):
        Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by = self.params

        if self.H is None:
            self.reset_state(Xs[0].shape[0])

        H = self.H
        Hs = {}
        Ys = []
        Hs[-1] = np.copy(H)
        Rs = []
        Us = []
        H_tildas = []

        for t in range(len(Xs)):
            X = Xs[t]
            U = sigmoid(np.dot(X, Wxu) + np.dot(H, Whu) + bu)
            R = sigmoid(np.dot(X, Wxr) + np.dot(H, Whr) + br)
            H_tilda = np.tanh(np.dot(X, Wxh) + np.dot(R * H, Whh) + bh)
            H = U * H + (1 - U) * H_tilda
            Y = np.dot(H, Wy) + by
            Hs[t] = H
            Ys.append(Y)
            Rs.append(R)
            Us.append(U)
            H_tildas.append(H_tilda)

        self.Ys, self.Hs, self.Rs, self.Us, self.H_tildas = Ys, Hs, Rs, Us, H_tildas
        return Ys, Hs  # return Ys,Hs,(Rs,Us,H_tildas)

    def backward(self, dZs):  # Ys,loss_function):
        Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by = self.params
        Ys, Hs, Rs, Us, H_tildas = self.Ys, self.Hs, self.Rs, self.Us, self.H_tildas

        dWxu, dWhu, dWxr, dWhr, dWxh, dWhh, dWy = np.zeros_like(Wxu), np.zeros_like(Whu), np.zeros_like(Wxr), np.zeros_like(Whr), np.zeros_like(Wxh), np.zeros_like(Whh), np.zeros_like(Wy)
        dbu, dbr, dbh, dby = np.zeros_like(bu), np.zeros_like(br), np.zeros_like(bh), np.zeros_like(by)
        dH_next = np.zeros_like(Hs[0])
        input_dim = Xs[0].shape[1]
        T = len(Xs)

        for t in reversed(range(T)):
            R = Rs[t]
            U = Us[t]
            H = Hs[t]
            X = Xs[t]
            H_tilda = H_tildas[t]
            H_pre = Hs[t - 1]
            dZ = dZs[t]

            # output the idu of the model parameters of f
            dWy += np.dot(H.T, dZ)
            dby += np.sum(dZ, axis=0, keepdims=True)

            # The gradient of the hidden state h
            dH = np.dot(dZ, Wy.T) + dH_next

            # H = U * H_pre + (1 - U) * H_tildas
            dH_tilda = dH * (1 - U)
            dH_pre = dH * U
            dU = H_pre * dH - H_tilda * dH

            # H_tilda = tanh(X * Wxh + (R * H_) * Whh + bh)
            dH_tildaZ = (1 - np.square(H_tilda)) * dH_tilda
            dWxh += np.dot(X.T, dH_tildaZ)
            dWhh += np.dot((R * H_pre).T, dH_tildaZ)
            dbh += np.sum(dH_tildaZ, axis=0, keepdims=True)

            dR = np.dot(dH_tildaZ, Whh.T) * H_pre
            dH_pre += np.dot(dH_tildaZ, Whh.T) * R

            # U = σ(UZ)   R = σ(RZ)
            dUZ = U * (1 - U) * dU
            dRZ = R * (1 - R) * dR

            dH_pre += np.dot(dUZ, Whu.T)
            dH_pre += np.dot(dRZ, Whr.T)

            # R = σ(X * Wxr + H_ * Whr + br)
            dWxr += np.dot(X.T, dRZ)
            dWhr += np.dot(H_pre.T, dRZ)
            dbr += np.sum(dRZ, axis=0, keepdims=True)

            dWxu += np.dot(X.T, dUZ)
            dWhu += np.dot(H_pre.T, dUZ)
            dbu += np.sum(dUZ, axis=0, keepdims=True)

            if True:
                dX_RZ = np.dot(dRZ, Wxr.T)
                dX_UZ = np.dot(dUZ, Wxu.T)
                dX_H_tildaZ = np.dot(dH_tildaZ, Wxh.T)
                dX = dX_RZ + dX_UZ + dX_H_tildaZ

            dH_next = dH_pre

        grads = [dWxu, dWhu, dbu, dWxr, dWhr, dbr, dWxh, dWhh, dbh, dWy, dby]
        for i, _ in enumerate(self.grads):
            self.grads[i] += grads[i]

        return self.grads

    def get_states(self):
        return self.Hs

    def get_outputs(self):
        return self.Ys

    def parameters(self):
        return self.params
```

