It can be shown that

$$\lim_{T\to\infty}\varphi = \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}}= \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta+\theta}{\theta(1-\theta)}}}= \theta.$$ 
(102.55)

Similarly, we have

$$\sqrt{T}(\theta-\varphi)=\sqrt{T}\left(\theta-\frac{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\right)$$ 

$$=\frac{\theta\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}\right)-\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}\right)}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\.$$
(102.56)

We also expand Taylor's series in $\frac{1}{\sqrt{T}}$, and we can obtain

$$\sqrt{T}(\theta-\varphi)=\frac{\theta\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+O\left(\frac1T\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}-\frac{\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}\right)-\left(\frac{\mu-r}{T}+\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}+\frac{\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)^2+O\left(\frac1T\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}$$ 

$$=\frac{\frac12\theta\frac{\sigma^2}{\sqrt{T}}\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+\frac{\mu-r}{\sqrt{T}}+\frac12\frac{\sigma^2}{\sqrt{T}}\left(\frac{\theta}{1-\theta}-2\right)+O\left(\frac1{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}.$$
(102.57)