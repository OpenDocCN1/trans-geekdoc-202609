Then, a while later in 2012, the whole AI research world was shocked by one method. At the world competition for image recognition, Imagenet Large Scale Visual Recognition Challenge (ILSVRC), a method using deep learning called SuperVision (strictly, that's the name of the team), which was developed by Professor Hinton and others from Toronto University, won the competition. It far surpassed the other competitors, with formidable precision. At this competition, the task was assigned for a machine to automatically distinguish whether an image was a cat, a dog, a bird, a car, a boat, and so on. 10 million images were provided as learning data and 150,000 images were used for the test. In this test, each method competes to return the lowest error rate (that is, the highest accuracy rate).

Let's look at the following table that shows the result of the competition:

| Rank | Team name | Error |
|---|---|---|
| 1 | SuperVision | 0.15315 |
| 2 | SuperVision | 0.16422 |
| 3 | ISI | 0.26172 |
| 4 | ISI | 0.26602 |
| 5 | ISI | 0.26646 |
| 6 | ISI | 0.26952 |
| 7 | OXFORD_VGG | 0.26979 |
| 8 | XRCE/INRIA | 0.27058 |

You can see that the difference in the error rate between SuperVision and the second position, ISI, is more than 10%. After the second position, it's just a competition within 0.1%. Now you know how greatly SuperVision outshone the others with precision rates. Moreover, surprisingly, it was the first time SuperVision joined this ILSVRC, in other words, image recognition is not their usual field. Until SuperVision (deep learning) appeared, the normal approach for the field of image recognition was machine learning. And, as mentioned earlier, a feature value necessary to use machine learning had to be set or designed by humans. They reiterated design features based on human intuition and experiences and fine-tuning parameters over and over, which, in the end, contributed to improving precision by just 0.1%. The main issue of the research and the competition before deep learning evolved was who was able to invent good feature engineering. Therefore, researchers must have been surprised when deep learning suddenly showed up out of the blue.