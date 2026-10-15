
## Valuation techniques for traditional common stocks

> ... it used to be the rule of thumb that you shouldn’t have a higher P/E on a growth stock than its growth rate ... Ultimately 12%–15% growth doesn’t hold up 50% multiples ... I don’t understand how you get a 23 market P/E with no growth in profits.
>
> — Scott Black, *Barron’s*, 6 June 1998

In order to gain a feel for the process of valuing Internet and technology stocks it is essential to start with how one values what could be referred to as traditional stocks. When analysing stock markets the starting point is not to confuse price with value. Price is what you pay: value is what you get. Investors do not (or should not) buy financial assets for emotional reasons – they buy them for profit. Value itself is directly related to the level and expected growth of those cash flows. The founding father of investment analysis, Ben Graham, in writing *The Intelligent Investor* (1949), neatly summed up the valuation dilemma: ‘In the short term, the stock market is a voting machine: in the long term it’s a weighing machine.’

While day-to-day market prices are largely driven by investors’ emotions, long term they are based on the fundamental values of profits, earnings and cash flows.

Most analysts rely on the fundamental building blocks of stock value – the dividends and earnings of firms – to make stock valuation decisions. Stocks have value because of the potential cash flows, called dividends, which a stockholder expects to receive from ownership of the firm. Stocks also have value if, in the future, other stockholders may decide that the valuation of these future dividends is not fully reflected in the future share price. It is by forecasting and valuing potential future dividends and earnings and deciding whether someone will, in the future, value these differently, that enables one to judge the investment value of shares.

The uncertainty of future cash flows makes the pricing of stocks according to the system of applying net present values more difficult. In this chapter we examine the valuation principles applicable to common stocks. Two basic approaches of stock valuation when using security analysis are:

- (1) the present value approach, or capitalization of income method; and
- (2) fundamental analysis.

### Present value analysis: capitalization of income method

The classic method of calculating intrinsic value applies present value analysis. This technique is often referred to as the capitalization of income method. The present value process involves the capitalization (discounting) of future cash flows. That is, the intrinsic value of a stock is equal to the present value of the future stream of cash flows an investor expects to receive from the asset. These cash flows could be periodic, such as dividends, or simply a terminal price or redemption value, or a combination of these. Since these cash flows occur in the future, they must be discounted at an appropriate rate to determine their present value. The sum of these discounted cash flows is the estimated intrinsic value of the stock. This is illustrated with Equation 4.1.

```
Value_{t=0} = Σ_{t=1}^{n} Cash flows / (1 + k)^t      (Eq 4.1)
```

where

- `Value_{t=0}` = the value of the asset now (time period 0)
- `Cash flows` = the future cash flows resulting from ownership of the stock
- `k` = the appropriate discount rate of return required by an investor for an investment of this type
- `n` = number of periods over which the cash flows are expected

To derive the intrinsic value using this model an investor must:

1. Estimate an appropriate required rate of return.
2. Estimate the amount and timing of the future stream of cash flows.
3. Use these two components in a present value model to estimate the value of the stock. This is then compared to the current market price of the stock.

Figure 4.1 summarizes the present value process used. This emphasizes the factors that go into valuing common stocks. The exact present value process used by investors in the market place depends on assumptions made about the growth rate in the expected stream of cash flows, as explained later in this chapter.

![Figure 4.1 The present value approach to valuation](img/67ce553842aa835a611c7cbbbb028358_56_0.png)

*Figure 4.1 The present value approach to valuation*

### The required rate of return

An investor who is considering the purchase of a common stock must assess its risk and, given its risk, the *minimum expected rate of return* that will be required to induce the investor to make the purchase. This minimum expected return, or *required rate of return*, is an opportunity cost.

The required rate of return, capitalization rate and discount rate are interchangeable terms in valuation analysis. While in theory we know what this variable is, in practice it is not easy to determine the precise number to use. Because of this complexity, we will generally assume that we know the capitalization rate and concentrate here on the other issues involved in the valuation of stocks.

### The expected cash flows

The other component that goes into the present value framework is the expected stream of cash flows. The value of common stock is the present value of all the cash flows to be received from the issuer. The questions that then arise are as follows:

1. What are the cash flows to use in valuing a stock?
2. What are the expected amounts of the cash flows?
3. When will the expected cash flows be received?

Stockholders may plan to sell their shares at some time in the future, resulting in a cash flow from the sales price. As shown later, however, even if investors think of the total cash flows from common stocks as a combination of dividends and a future price at which the stock can be sold, this is equivalent to using the stream of all dividends to be received on the stock as the key valuation principle.

What about earnings? Are they important? Can they be used in valuing a stock? The answer to both questions is a clear Yes. Dividends are paid out of earnings, so earnings are clearly important. The second stock valuation approach, fundamental analysis, to be considered later, uses earnings and a P/E ratio to determine intrinsic value. Therefore, earnings are an important part of fundamental analysis: in fact, earnings receive more attention from investors than any other single variable.

If all earnings are paid out as dividends, they will be accounted for as dividends. If the company retains earnings they presumably will be reinvested, thereby enhancing future earnings and, ultimately, dividends. The present value analysis should not count the earnings reinvested currently and also count them again paid later as dividends. If they are properly defined and separated, these two variables produce the same results. This means that more than one present value model is possible. However, it is always correct to use dividends in the present value analysis, and this is what is almost always done when investors use the present value approach to stock valuation.

Because dividends are the only cash flow stream to be received directly by investors under normal conditions, it is appropriate to have a stock valuation model based on dividends. It is now important to consider such a model, the dividend discount model, which is the basis for understanding the fundamental valuation of common stocks.

### The dividend discount model (DDM)

Since dividends are the only cash payment a stockholder receives directly from a firm, *they provide the foundation of valuation for common stocks*. Applying Equation 4.1 specifically to value common stocks, the cash flows are the dividends *expected* to be paid in each future period. An investor or analyst using this approach carefully studies the future prospects for a company and estimates the likely dividends to be paid. In addition, the analyst estimates an appropriate required rate of return or discount rate based on the risk foreseen in the dividends, taking account of the alternatives available. Finally, the investor would discount to the present the entire stream of estimated future dividends, properly identified as to amount and timing.

Equation 4.1 adapted for common stocks where dividends are the cash flows results in Equation 4.2. This equation, known as the dividend discount model (DDM), states that the value of a stock today is the discounted value of all future dividends:

\[
\hat{P}_{cs}=\frac{D_1}{(1+k_{cs})}+\frac{D_2}{(1+k_{cs})^2}+\frac{D_3}{(1+k_{cs})^3}+\frac{D_{\infty}}{(1+k_{cs})^{\infty}}
\]

\[
=\sum_{t=1}^{n}\frac{D_t}{(1+k_{cs})^t}\qquad\text{Eq 4.2}
\]

\[
=\textit{dividend discount model}
\]
