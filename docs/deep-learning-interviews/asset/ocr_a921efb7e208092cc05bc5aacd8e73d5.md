# **PRB-231 ❓ CH. PRB- 8.55.**

*Referring the code snippet in Fig. ( 8.31 ), answer the following questions regarding the VGG11 architecture [ 25 ] :*

```
```python
import torchvision
import torch

def main ():
    vgg11=torchvision. models. vgg11(pretrained= True )
    vgg_layers = vgg11. features

    for param in vgg_layers. parameters():
        param. requires_grad = False


    example =[torch. rand(1 , 3 , 224 , 224 ),
        torch. rand(1 , 3 , 512 , 512 ),
        torch. rand(1 , 3 , 704 , 1024 )]

    vgg11. eval()

    for e in example:

        out= vgg_layers(e)

        print(out. shape)


if __name__ == "__main__" :

    main()
```
```

![](bbox=[0.3, 0.68, 0.72, 0.7])

+   1 *In each case for the input variable `example` , determine the dimensions of the tensor which is the output of applying the VGG11 CNN to the respective input .*
2 *Choose the correct option. The last layer of the VGG11 architecture is:*
    *i* Conv2d