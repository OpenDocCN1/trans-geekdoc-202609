```
for ae in self.hidden_layers:
self.params += ae.forward_params

# for momentum
self.dW = theano.shared(np.zeros(W0.shape))
self.db = theano.shared(np.zeros(K))
self.dparams = [self.dW, self.db]
for ae in self.hidden_layers:
self.dparams += ae.forward_dparams

X_in = T.matrix('X_in')
targets = T.vector('Targets')
pY = self.forward(X_in)

# squared_magnitude = [(p*p).sum(p) for p in self.params]
# reg_cost = T.sum(squared_magnitude)
cost = -T.mean(T.log(PY[T.arange(p.shape[0]), targets])) )+# reg*reg_cost
prediction = self.predict(X_in)
cost_predict_op = theano.function(
inputs=[X_in, targets],
outputs=[cost, prediction],
)

updates = [
(p, p + mu*dp - learning_rate*T.grad(cost, p)) for p, dp in zip(self.params, self.dparams)
] + [
(mu, mu*dp - learning_rate*T.grad(cost, p)) for p, dp in zip(self.params, self.dparams)
]

train_op = theano.function(
inputs=[X_in, targets],
```