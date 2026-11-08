
Numeric values are usually handled by assuming that they have a “normal” or “Gaussian” probability distribution. [Table 4.4](#Ch004_91-164_B9780443158889000054.xhtml#t0025) gives a summary of the weather data with numeric features from [Table 1.3.](#Ch001_3-42_B9780443158889000029.xhtml#t0020) For nominal attributes, we calculate counts as before, while for numeric ones we simply list the values that occur. Then, instead of normalizing counts into probabilities as we do for nominal attributes, we calculate the mean and standard deviation for each class and each numeric attribute. The mean value of `temperature` over the `yes` instances is 73, and its standard deviation is 6.2. The mean is simply the average of the values—the sum divided by the number of values. The standard deviation is the square root of the sample variance, which we calculate as follows: subtract the mean from each value, square the result, sum them together, and then divide by one less than the number of values. After we have found this “sample variance,” take its square root to yield the standard deviation. This is the standard way of calculating mean and standard deviation of a set of numbers (the “one less than” is to do with the number of degrees of freedom in the sample, a statistical notion that we don’t want to get into here).

### Table 4.4
The Numeric Weather Data With Summary Statistics

| Outlook  || Temperature || Humidity || Windy || Play |
| --- | --- | --- | --- | --- |
|   || `Yes` || `No` ||   || `Yes` || `No` ||   || `Yes` || `No` ||   || `Yes` || `No` || `Yes` || `No` |
| Sunny || 2 || 3 ||   || 83 || 85 ||   || 86 || 85 || False || 6 || 2 || 9 || 5 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Overcast || 4 || 0 ||   || 70 || 80 ||   || 96 || 90 || True || 3 || 3 ||   ||   |
| Rainy || 3 || 2 ||   || 68 || 65 ||   || 80 || 70 ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 64 || 72 ||   || 65 || 95 ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 69 || 71 ||   || 70 || 91 ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 75 ||   ||   || 80 ||   ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 75 ||   ||   || 70 ||   ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 72 ||   ||   || 90 ||   ||   ||   ||   ||   ||   |
|   ||   ||   ||   || 81 ||   ||   || 75 ||   ||   ||   ||   ||   ||   |
| Sunny || 2/9 || 3/5 || `Mean` || 73 || 74.6 || `Mean` || 79.1 || 86.2 || False || 6/9 || 2/5 || 9/14 || 5/14 |
| Overcast || 4/9 || 0/5 || `Std dev` || 6.2 || 7.9 || `Std dev` || 10.2 || 9.7 || True || 3/9 || 3/5 ||   ||   |
| Rainy || 3/9 || 2/5 ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   |

![Image](images/T000054tabt0025.png)

The probability density function for a normal distribution with mean `μ` and standard deviation `σ` is given by the rather formidable expression

$f\\left( x \\right) = \\frac{1}{\\sqrt{2\\pi}\\sigma}e^{- \\frac{{(x - \\mu)}^{2}}{2\\sigma^{2}}}.$<mml:math><mml:mi>f</mml:mi><mml:mo>(</mml:mo><mml:mi>x</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:msqrt><mml:mrow><mml:mn>2</mml:mn><mml:mi>&#960;</mml:mi></mml:mrow></mml:msqrt><mml:mi>&#963;</mml:mi></mml:mrow></mml:mfrac><mml:msup><mml:mrow><mml:mi>e</mml:mi></mml:mrow><mml:mrow><mml:mo>&#8722;</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mo>(</mml:mo><mml:mi>x</mml:mi><mml:mo>&#8722;</mml:mo><mml:mi>&#956;</mml:mi><mml:mo>)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup></mml:mrow><mml:mrow><mml:mn>2</mml:mn><mml:msup><mml:mrow><mml:mi>&#963;</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup></mml:mrow></mml:mfrac></mml:mrow></mml:msup><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000054si17.png)

But fear not! All this means is that if we are considering a `yes` outcome when `temperature` has a value, say, of 66; we just need to plug `x` = 66, `μ` = 73, and `σ` = 6.2 into the formula. So the value of the probability density function is

$f(\\mathit{temperature} = 66\\text{∣}\\mathit{yes}) = \\frac{1}{\\sqrt{2\\pi} \\cdot 6.2}e^{- \\frac{{(66 - 73)}^{2}}{2 \\cdot 6.2^{2}}} = 0.0340.$<mml:math><mml:mi>f</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="italic">temperature</mml:mi><mml:mo>=</mml:mo><mml:mn>66</mml:mn><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi mathvariant="italic">yes</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:msqrt><mml:mrow><mml:mn>2</mml:mn><mml:mi>&#960;</mml:mi></mml:mrow></mml:msqrt><mml:mo>&#8901;</mml:mo><mml:mn>6.2</mml:mn></mml:mrow></mml:mfrac><mml:msup><mml:mrow><mml:mi>e</mml:mi></mml:mrow><mml:mrow><mml:mo>&#8722;</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mo>(</mml:mo><mml:mn>66</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>73</mml:mn><mml:mo>)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup></mml:mrow><mml:mrow><mml:mn>2</mml:mn><mml:mo>&#8901;</mml:mo><mml:msup><mml:mrow><mml:mn>6.2</mml:mn></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup></mml:mrow></mml:mfrac></mml:mrow></mml:msup><mml:mo>=</mml:mo><mml:mn>0.0340</mml:mn><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000054si18.png)

And by the same token, the probability density of a `yes` outcome when `humidity` has a value, say, of 90 is calculated in the same way:

*f*(*h**u**m**i**d**i**t**y*\=90∣*y**e**s*) = 0.0221.<mml:math><mml:mi>f</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">humidity</mml:mi><mml:mo>=</mml:mo><mml:mn>90</mml:mn><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi mathvariant="italic">yes</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.0221</mml:mn><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000054si19.png)

The probability density function for an event is very closely related to its probability. However, it is not quite the same thing. If `temperature` is a continuous scale, the probability of the `temperature` being `exactly` 66—or `exactly` any other value, such as 63.14159262—is zero. The real meaning of the density function `f`(`x`) is that the probability that the quantity lies within a small region around `x`, say,between `x`−`ε`/2<mml:math><mml:mi>x</mml:mi><mml:mo>&#8722;</mml:mo><mml:mi>&#949;</mml:mi><mml:mo>&#8725;</mml:mo><mml:mn>2</mml:mn></mml:math>![Equation](images/F000054si20.png) and `x`+`ε`/2<mml:math><mml:mi>x</mml:mi><mml:mo>+</mml:mo><mml:mi>&#949;</mml:mi><mml:mo>&#8725;</mml:mo><mml:mn>2</mml:mn></mml:math>![Equation](images/F000054si21.png), is `ε` ⋅ `f`(`x`)<mml:math><mml:mi>&#949;</mml:mi><mml:mo>&#8901;</mml:mo><mml:mi>f</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>x</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000054si22.png). You might think we ought to factor in the accuracy figure `ε` when using these density values, but that’s not necessary. The same `ε` would appear in both the `yes` and `no` likelihoods that follow and cancel out when the probabilities were calculated.

Using these probabilities for the new day in [Table 4.5](#Ch004_91-164_B9780443158889000054.xhtml#t0030) yields
