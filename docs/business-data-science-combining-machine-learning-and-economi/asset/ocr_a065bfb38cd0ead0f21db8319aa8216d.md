> I normally would not revue a Waffle House but this one deserves it. The workers, Amanda, Amy, Cherry, James and J.D. were the most pleasant crew I have seen. While it was only lunch, B.L.T. and chili, it was great. The best thing was the 50's rock and roll music, not to loud not to soft. This is a rare exception to what you all think a Waffle House is. Keep up the good work.

Overall: 5, Atmosphere: 5, Food: 5, Service: 5, Value: 5.

Another user found Sartin's Seafood in Nassau Bay, Texas, to be all-around low quality (but it must have been cheap):

> Had a very rude waitress and the manager wasn't nice either. Overall: 1, Atmosphere: 1, Food: 1, Service: 1, Value: 5.

Intuitively, these reviews will be constructed from a number of underlying topics, for example, the type of food, the quality of the restaurant, or the geographic location. The hope is that we can uncover these topics via factorization.

After cleaning and Porter stemming, following the same procedure as for the `congress109` text tokenization, we are left with a vocabulary of 2640 bigrams. For example, the first review in the document-term matrix has nonzero counts on bigrams indicating a pleasant meal at a rib joint:

```
```
> x <- we8thereCounts
> x[1,x[1,]!=0]

even though    larg portion    mouth water    red sauc    babi back
    1               1               1               1               1
back rib    chocol    mounse    veri    satisfa
    1               1               1
```
```

We can apply PCA to get a factor representation of the review text. After digging through the biggest rotations in the first few factors, we find that PC1 looks like it will be big and positive for positive reviews, while PC4 will be big and negative for Italian (pizza).