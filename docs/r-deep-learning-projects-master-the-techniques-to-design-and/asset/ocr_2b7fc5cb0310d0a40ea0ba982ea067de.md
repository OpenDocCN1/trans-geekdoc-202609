```
loss <- 0
for(idix in 1:seq_size){
xs[[idix]] <- matrix(0,self$vocab_size,1)
xs[[idix]][inputs[[idix]]] = 1
## Update the hidden state
if(idix==1){
hs[[idix]] <-
tanh(self$U%*%xs[[idix]]+self$W%*%s_prev)
} else {
hs[[idix]] <-
tanh(self$U%*%xs[[idix]]+self$W%*%hs[[(idix-1)]])
}
## calculate the probabilities for the next character
ys[[idix]] <- self$V%*%hs[[idix]]
ps[[idix]] <- softmax(ys[[idix]])
## Cross-entropy loss
loss <- loss-log(ps[[idix]][targets[[idix]], 1])
# Calculate gradients
dU <- zeros_like(self$U)
dW <- zeros_like(self$W)
dV <- zeros_like(self$V)
dhnext <- zeros_like(s_prev)
for(j in length(inputs):1){
## Gradient of the error vs output
dy <- ps[[j]]
dy[targets[[j]]] <- dy[targets[[j]]]-1
dV <- dV+dy%*%t(hs[[j]])
dh <- t(self$V)%*%dy + dhnext
## backprop through the tanh
dhraw <- (1 - hs[[j]] * hs[[j]]) * dh
## derivative of the error between input and hidden
layer
dU <- dU+dhraw%*%t(xs[[j]])
if(j==1){
dW <- dW+dhraw%*%t(s_prev)
} else {
dW <- dW+dhraw%*%t(hs[[(j-1)]])
}
dhnext <- t(self$W)%*%dhraw
}
return(list("loss"=loss, "dU"=dU, "dW"=dW, "dV"=dV,
"hs"=hs[length(inputs)-1]))
,
sample_char = function(h, seed_ix, n){
```

layer