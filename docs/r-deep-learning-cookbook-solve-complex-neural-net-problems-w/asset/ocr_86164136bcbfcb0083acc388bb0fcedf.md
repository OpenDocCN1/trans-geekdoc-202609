The output of the preceding command will contain details of the object. An illustration is shown in the following script:

```
> vc11
An object of class "fvclMatrix"
Slot "address":
<pointer: 0x0000000001822e180>

Slot ".context_index":
[1] 1

Slot ".platform_index":
[1] 1

Slot ".platform":
[1] "Intel(R) OpenCL"

Slot ".device_index":
[1] 1

Slot ".device":
[1] "Intel(R) HD Graphics 530"
```

3. Let's consider the evaluation of CPU vs GPU. As most of the deep learning will be using GPUs for matrix computation, the performance is evaluated by matrix multiplication using the following script:

```
# CPU vs GPU performance
DF <- data.frame()
evalSeq<-seq(1,2501,500)
for (dimpower in evalSeq){
  print(dimpower)
  Mat1 = matrix(rnorm(dimpower^2), nrow=dimpower)
  Mat2 = matrix(rnorm(dimpower^2), nrow=dimpower)
  now = Sys.time()
  Matfin = Mat1*%*Mat2
  cpu <- Sys.time()-now
  now <- Sys.time()
  vc11 = vclMatrix(Mat1)
  vc12 = vclMatrix(Mat2)
  vc1C = vc11 *%* vc12
  gpu <- Sys.time()-now
  DF <- rbind(DF,c(nrow(Mat1), cpu, gpu))
}
DF<-data.frame(DF)
colnames(DF) <- c("nrow", "CPU_time", "gpu_time")
```