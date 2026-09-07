   

Outfoxing Wall Street

![](images/00001.jpeg)

How to conquer the markets with these 7 lines of machine learning code

 

 

 

Dan Murphy

 

Copyright © 2023 by Dan Murphy .

All rights reserved.

No part of this publication may be reproduced, distributed, or transmitted in any form or by any means, including photocopying, recording, or other electronic or mechanical methods, without the prior written permission of the publisher, except in the case of brief quotations embodied in critical reviews and certain other noncommercial uses permitted by copyright law.

 

Contents

 

[Forward](#part0006.html#_Toc129880243)

[Chapter 1:  The Birth of a Simple Trading Strategy](#part0007.html#_Toc129880244)

[How the strategy came to be…](#part0007.html#_Toc129880245)

[Discovering the untold power of trading: How machine learning and supercomputers are revolutionizing the game](#part0007.html#_Toc129880246)

[Understanding the significance of seven lines of code](#part0007.html#_Toc129880247)

[Chapter 2:  Trading ETFs: Stocks vs Bonds](#part0008.html#_Toc129880248)

[Advantages and disadvantages of trading ETFs](#part0008.html#_Toc129880249)

[Why stock and bond ETFs are chosen for this strategy](#part0008.html#_Toc129880250)

[The Benefits of Stock and Bond ETFs](#part0008.html#_Toc129880251)

[The role of diversification](#part0008.html#_Toc129880252)

[Chapter 3:  The Power of Trend Following](#part0009.html#_Toc129880253)

[What is trend following and how it works](#part0009.html#_Toc129880254)

[Benefits of trend following in this strategy](#part0009.html#_Toc129880255)

[Chapter 4:  Mean Reversion: A Complement to Trend Following](#part0010.html#_Toc129880256)

[What is mean reversion and how it works](#part0010.html#_Toc129880257)

[How this strategy uses mean reversion](#part0010.html#_Toc129880258)

[The benefits of combining trend following and mean reversion](#part0010.html#_Toc129880259)

[Chapter 5:  A Track Record of Success](#part0011.html#_Toc129880260)

[How the strategy has performed over the past 20 years](#part0011.html#_Toc129880261)

[Average gains and risk management](#part0011.html#_Toc129880262)

[Comparison with other investment strategies](#part0011.html#_Toc129880263)

[Chapter 6:  Trading Systems vs Chart Patterns](#part0012.html#_Toc129880264)

[Debunking the pseudoscience of chart patterns](#part0012.html#_Toc129880265)

[Understanding the benefits of a systematic trading approach](#part0012.html#_Toc129880266)

[Why relying on intuition can be detrimental to investment success](#part0012.html#_Toc129880267)

[Chapter 7:  Applying the Simple Trading Strategy](#part0013.html#_Toc129880268)

[How to implement the strategy in practice](#part0013.html#_Toc129880269)

[Chapter 8:  Conclusion and Final Thoughts](#part0014.html#_Toc129880270)

[Summary of the strategy and its benefits](#part0014.html#_Toc129880271)

[Thoughts on the future of investing and trading strategies](#part0014.html#_Toc129880272)

[Encouragement to take action and start using the strategy today](#part0014.html#_Toc129880273)

[How to Grab Access to 100 Top Performing A.I Strategies…](#part0014.html#_Toc129880274)

 

What Others are Saying About this Book…

![](images/00002.jpeg)

\-         “Well written - speaks highly of the author who is well known for his rigorous back-testing. Builds on the concepts of spot pricing and machine learning to simplify the art of successful trading.”

\-         “Proves a lot of former theories WRONG!”

\-         “It’s a good clear detailed report - but only for those that are interested in applying these technical skills and have an interest in trading.”

\-         “The great value in it, is how you provide the code for a real system that people can program themselves.”

\-         “EVERYTHING DAN DOES HAS AN EDGE. THANK YOU.”

\-         “I think it is a very good book that cuts to the chase without a lot of excess verbal BS thrown in like you find in so many other books.”

 

Undeniable Proof that A.I Trading Works:

![](images/00003.gif)

 

About the Author

![](images/00004.gif)

Dan Murphy is a veteran trader with 26 years of experience in the financial markets. He hails from the stunning Napa Valley in California, and his passion for trading has driven him to become an accomplished author of three books on the topic, including the wildly popular The Relaxed Investor, which has been downloaded over 500,000 times.

In addition to being a successful trader and author, Dan is also the founder of PortfolioBoss Inc, an A.I company that has brought hedge fund level tools to everyday kitchen counter traders. His innovative venture has revolutionized the trading world, making advanced technology and trading strategies accessible to traders of all levels of experience.

Dan's dedication to helping others achieve financial freedom through trading is truly remarkable. He is a gifted teacher, and many of his students have gone on to achieve incredible results in the markets. One of his students even placed third out of 18,000 in the Fundseeder trading competition, a testament to Dan's ability to teach the strategies and techniques that lead to success in trading.

One of Dan's unique strengths is his ability to foresee the need for using rare and exclusive data. He has access to data that is not widely available to the public, and he uses this information to make well-informed trading decisions. Dan's focus on using data to drive his trading decisions has been key to his success as a trader and his ability to teach others to achieve similar results.

Dan currently lives in sunny Newport Beach, CA, where he continues to write and teach about trading. He is a highly respected figure in the trading community and has earned the admiration and respect of traders around the world.

In conclusion, Dan Murphy is a true master of his craft, with decades of experience, a wealth of knowledge, and an infectious enthusiasm for the markets. Through his books, company, and mentorship, he continues to inspire and guide traders around the world.

\-ChatGPT

![](images/00005.jpeg)

7 lines of machine learning code to beat the markets

 

Forward

Welcome to the world of systematic trading! It's an exciting place to be, full of opportunities and challenges, where fortunes can be made and lost in the blink of an eye. But don't worry, because with the right knowledge and tools, you can turn the odds in your favor and achieve success beyond your wildest dreams.

In this book, you're about to learn the secrets of the seven lines of code, a revolutionary trading strategy that has been proven to generate consistent profits in any market condition, from bull to bear and everything in between. It's a strategy that I've personally developed with the aid of The Boss SuperAi. A network of over 3,500 computers packed to the gills with machine learning. It has been used by my students and clients to achieve remarkable results.

With the seven lines of code, you'll be able to trade the S&P 500 (and bonds) with precision and confidence, thanks to a carefully crafted system that combines trend following and mean reversion techniques, along with advanced risk management and portfolio optimization strategies. This is not some "get rich quick" scheme, but a disciplined and scientific approach to investing that relies on data and evidence, not hunches and emotions. Here’s the 20-year backtest of this simple, yet powerful strategy:

![](images/00006.jpeg)

Throughout this book, you'll discover the principles and tools that make the seven lines of code so effective, from the basic concepts of trend following and mean reversion to the advanced techniques of ETF mispricing and big data analysis. You'll also learn how to implement the strategy step by step, from setting up your brokerage account to calculating the formulas and ETF prices, and how to interpret the signals and adjust your positions accordingly.

But more than that, you'll gain a deep understanding of how the markets work and how to navigate their complex dynamics. You'll learn how to identify and exploit patterns and anomalies that most traders overlook, and how to avoid the common pitfalls and mistakes that can ruin your account. You'll also learn the importance of discipline, patience, and perseverance, and how to maintain a winning mindset and a long-term perspective.

I'm not promising you overnight success, but I'm offering you a proven and reliable system that has withstood the test of time and the ups and downs of the markets. I'm also promising you a thrilling and rewarding journey, full of challenges and opportunities, where you'll not only make money but also gain knowledge and confidence that will serve you well in all areas of your life.

So, get ready to embark on a life-changing adventure, where you'll discover the power of the seven lines of code and unlock the secrets of the markets. As the Chinese proverb says, "The best time to plant a tree was 20 years ago. The second-best time is now." Don't wait any longer, take action today and start building your wealth and your future.

 

Chapter 1:  
  
The Birth of a Simple Trading Strategy

 

How the strategy came to be…

As a 26-year veteran trader, I am beyond excited to share the incredible story behind our innovative trading strategy. My journey began with a dream of creating a trading system that could outperform the market consistently. But I knew that I couldn't rely on gut instinct or guesswork. I had to find a way to leverage cutting-edge technology and data to develop a strategy that would stand the test of time.

That's when I began to explore the potential of machine learning and artificial intelligence. My team and I believed that this technology had the power to revolutionize the way we approach trading. However, we knew that it would take a significant investment of time, effort, and resources to build a system that could handle the complex data analysis required.

We started by gathering a massive amount of data from various sources, including price data on a wide variety of asset classes and global fund flow data. The sheer volume of data was mind-boggling, and we knew that we needed a powerful machine to analyze it all. So, I invested $4 million in building a supercomputer network in the cloud that would use machine learning to automatically design trading strategies from scratch.

Our programming team has been working on the project for over five years and counting, developing the algorithms and designing the architecture needed to make this vision a reality. The journey has been a long and challenging one, but I’m more excited than ever to see the potential of this technology.

The machine we created, nicknamed “The Boss”, uses data to write trading strategies in C code. The strategies are based on simple, yet powerful mathematical formulas. Much like Einstein’s equation for relativity: E= MC^2 is simple yet powerful. When combined together in the proper way, they can build the ultimate money-making strategy. The machine is constantly learning and adapting to the market. It monitors the performance of its strategies and makes adjustments as needed.

The results have been nothing short of amazing. The trading strategy has consistently outperformed the market, averaging 19% annual gains for the past 20 years. This is an incredible accomplishment in a field where many strategies and fund managers struggle to even match the performance of the market averages. But what makes our 7-lines strategy truly unique is how simple it is.

The strategy is only seven lines of computer code. It's so simple that anyone can follow it. I wanted to create a strategy that was easy to understand and easy to follow. I believe that everyone should have access to the benefits of our strategy, not just professional traders.

The strategy is not based on intuition or guesswork, but rather on hard data and mathematical models. I’m proud to have created a system that is based on rigorous analysis and can continue to learn and improve over time. But what excites me the most is how accessible this strategy is to everyone.

As a veteran trader, I know how unpredictable the market can be. But I also know that the potential for technology to transform the financial industry is significant. This trading strategy is just the beginning of what is possible when you combine financial data and technology.

The journey to creating this trading strategy has been long, challenging, and ongoing. But the result has been nothing short of amazing. The combination of machine learning and finance has produced a strategy that has consistently outperformed the market. I’m thrilled to see the potential of this technology to transform the entire industry, and am proud to be a part of the revolution. I believe that this is just the beginning, and I’m excited to see where this technology will take us in the future.

Discovering the untold power of trading: How machine learning and supercomputers are revolutionizing the game

The financial industry has been transformed by the use of machine learning and supercomputers in trading. These technologies have given hedge funds the ability to process vast amounts of data, analyze it, and make predictions with a level of accuracy that was previously impossible. As a result, hedge funds that use these advanced tools have been able to make billions, and many have become household names.

One of the most well-known hedge funds that use machine learning is Renaissance Technologies, which was founded by mathematician James Simons. Renaissance Technologies uses a wide range of machine learning techniques to analyze financial data and create trading strategies. The firm has been highly successful, with an average annual return of 66% before fees over the past 30 years. Renaissance Technologies' success has made Simons one of the richest people in the world, with an estimated net worth of $25 billion.

Another hedge fund that uses machine learning is Bridgewater Associates, which was founded by Ray Dalio. Bridgewater Associates uses a tool called the "Systematized Intelligence Lab," which uses machine learning to analyze financial data and create trading strategies. The firm has been highly successful, with an average annual return of 12% over the past 20 years. Dalio's success has made him one of the richest people in the world, with an estimated net worth of $20 billion.

Two Sigma Investments is another hedge fund that uses machine learning. The firm was founded by David Siegel and John Overdeck and has become one of the largest hedge funds in the world. Two Sigma Investments uses a combination of machine learning and human expertise to analyze financial data and create trading strategies. The firm has been highly successful, with an average annual return of 30% over the past 20 years.

The success of these hedge funds is a testament to the power of machine learning and supercomputers in trading. These technologies have given hedge funds the ability to analyze vast amounts of data and create trading strategies that consistently outperform the market. In the past, the cost of designing a supercomputer was in the tens of millions of dollars, making it difficult for all but the wealthiest hedge funds to afford them. However, the rise of cloud computing has made it possible for smaller firms to access the power of supercomputers at a fraction of the cost.

Cloud computing has made it possible for firms to rent supercomputers at spot pricing rates, which are significantly lower than the regular rates. This has made it possible for even smaller firms to compete with larger ones. The ability to rent a supercomputer for a short period of time means that firms can access the power of these advanced tools when they need them most, without having to make a long-term commitment.

Spot pricing is a game-changer in the world of finance. It allows firms to access the power of supercomputers at a fraction of the cost. This is an exciting time in the world of finance, and we can't wait to see what the future holds.

The role of machine learning and supercomputers in trading has transformed the financial industry. Hedge funds that use machine learning have been able to gain a competitive edge by analyzing vast amounts of data, identifying patterns, and making predictions based on that data. The success of hedge funds such as Renaissance Technologies, Bridgewater Associates, and Two Sigma Investments is a testament to the power of these technologies. The rise of cloud computing and spot pricing has made it possible for smaller firms like mine to access the power of these advanced tools, making it an exciting time for the industry.

Understanding the significance of seven lines of code

When it comes to trading strategies, there is a common misconception that the more complex a strategy is, the more effective it will be. However, the truth is that the best performing and longest-lasting strategies are often the simplest. This is where Occam's Razor comes into play.

Occam's Razor is a philosophical principle that states that, when presented with multiple explanations for a phenomenon, the simplest explanation is usually the correct one. This principle can also be applied to trading strategies, where the simplest strategies are often the most effective.

The reason for this is that simple strategies are easier to understand and easier to execute. This means that traders are more likely to stick to the strategy and less likely to make mistakes. Simple strategies are also less likely to be overfit to historical data, meaning that they are more likely to perform well in the future.

One example of a simple trading strategy is a trend following strategy. This strategy involves buying an asset when it is trending up and selling it when it is trending down. This strategy can be implemented using only a few lines of code, making it easy to understand and execute. Here’s an example of riding the trend with the seven lines of code strategy:

![](images/00007.jpeg)

Another example of a simple trading strategy is a mean reversion strategy. This strategy involves buying an asset when it is below its average price and selling it when it is above its average price. This strategy can also be implemented using only a few lines of code.

![](images/00008.jpeg)

The key to a successful trading strategy is not its complexity, but rather its ability to produce consistent results. This is where the importance of backtesting comes into play. Backtesting involves testing a trading strategy on historical data to see how it would have performed in the past. This can give traders an idea of how the strategy might perform in the future.

It is important to note that simple trading strategies are not always the best strategies. There are some situations where a more complex strategy may be necessary. For example, in highly volatile markets, a more complex strategy may be needed to take into account the rapid changes in prices.

However, in most cases, the best performing and longest lasting strategies are simple. This goes counter to what most traders think, as they often believe that strategies need to be complex in order to be effective. This misconception can lead to traders spending a lot of time and effort on strategies that ultimately do not perform well.

Understanding the significance of seven lines of code is important in the world of trading. Simple strategies are often the best performing and longest lasting strategies, as they are easier to understand, easier to execute, and less likely to be overfit to historical data. Occam's Razor is an important principle that can be applied to trading strategies, as the simplest explanation is usually the correct one. By focusing on simple strategies and backtesting them, traders can increase their chances of success in the market.

Chapter 2:  
  
Trading ETFs: Stocks vs Bonds

 

Advantages and disadvantages of trading ETFs

ETFs (Exchange Traded Funds) have become a popular investment vehicle in recent years, and for good reason. They offer many advantages over traditional mutual funds, including lower fees, increased flexibility, and tax efficiency. However, like any investment, there are also disadvantages to consider. In this section, we will explore the advantages and disadvantages of trading ETFs, with specific examples.

Advantages of Trading ETFs

1.  Lower Fees: One of the biggest advantages of trading ETFs is the lower fees compared to traditional mutual funds. ETFs are typically passively managed and have lower expenses than actively managed mutual funds. For example, the Vanguard S&P 500 ETF (VOO) has an expense ratio of just 0.03%, compared to the average mutual fund expense ratio of 0.64%.
2.  Increased Flexibility: ETFs are more flexible than mutual funds in terms of trading. ETFs can be traded throughout the day on an exchange, just like a stock. This makes it easier for investors to buy and sell shares quickly and take advantage of market opportunities.
3.  Diversification: ETFs provide investors with access to a diversified portfolio of securities with a single investment. This can help reduce risk and increase returns over the long-term. For example, the iShares Core MSCI EAFE ETF (IEFA) provides exposure to a broad range of international stocks.
4.  Tax Efficiency: ETFs are generally more tax-efficient than mutual funds. This is because ETFs have lower turnover and are structured in a way that allows for in-kind redemptions. This means that the ETF can redeem shares by transferring underlying securities instead of selling them. This can help to minimize capital gains tax.
5.  In recent years, the popularity of ETFs has soared, as investors have increasingly turned to these instruments as a cost-effective, low-maintenance way to gain exposure to a wide range of assets. One area where this trend has been particularly notable is in the realm of futures trading, where ETFs are increasingly replacing traditional futures contracts as the preferred instrument of choice.
6.  One of the main advantages of ETFs over futures contracts is that they are much more accessible to individual investors. Futures contracts typically require a substantial upfront investment, and in some cases, a 7-figure account is necessary to participate. This high barrier to entry has long been a major impediment for smaller investors, who have been effectively shut out of the futures market as a result.
7.  ETFs, on the other hand, are much more accessible, with low minimum investment requirements and no need for specialized trading accounts. This has made them an attractive alternative to futures contracts for investors of all sizes, including those with modest account sizes who are looking to gain exposure to a particular market or asset class.
8.  Another advantage of ETFs is that they are typically easier to trade than futures contracts, with no need to worry about the expiration of a contract or the delivery of physical commodities. This can be a major benefit for individual investors, who may not have the resources or expertise to manage a complex futures trading strategy.
9.  Furthermore, ETFs can offer a more diverse range of investment options than futures contracts, which are typically limited to a specific commodity or asset class. With ETFs, investors can gain exposure to a wide range of asset classes, from equities and fixed income to commodities and currencies.
10.                     Overall, the growing popularity of ETFs has made it possible for individual investors to participate in a wider range of markets and asset classes than ever before, without the need for a large trading account or specialized expertise. As a result, ETFs have become an increasingly attractive option for investors looking to diversify their portfolios and gain exposure to a variety of different markets and asset classes.

Disadvantages of Trading ETFs

1.  Trading Costs: While ETFs have lower fees than mutual funds, they do have trading costs associated with buying and selling shares. These costs can add up, especially for investors who are trading frequently. It is important to consider these costs when evaluating the overall expense of an ETF.
2.  Tracking Error: ETFs are designed to track an index or a specific benchmark. However, there can be tracking errors due to factors such as expenses, dividends, and other costs. This can result in an ETF's returns deviating from the benchmark it is meant to track.
3.  Market Volatility: ETFs are subject to market volatility, just like any other investment. During times of market turbulence, ETFs can experience sharp drops in value. For example, the SPDR S&P 500 ETF (SPY) experienced a significant drop in value during the market downturn in March 2020.
4.  Lack of Active Management: While lower fees are a benefit of ETFs, they also lack the active management provided by mutual funds (perhaps this should be put into the “advantages” category). This means that investors are responsible for making their own investment decisions and monitoring the performance of their investments. This can be a disadvantage for some investors who prefer to have professional management.
5.  European laws: Recently, many ETFs in the United States aren’t easily tradeable for citizens of the EU. You must be an accredited investor in some areas, which just seems silly. Many of our European clients simply get their income verification notarized and presented to their broker.

Conclusion

ETFs offer many advantages over traditional mutual funds, including lower fees, increased flexibility, diversification, and tax efficiency. ETFs are also acting as an alternative to the futures market. However, there are also disadvantages to consider, such as trading costs, tracking error, market volatility, and lack of active management. Ultimately, it is important for investors to evaluate their own investment goals and risk tolerance before deciding whether to invest in ETFs or other investment vehicles. By considering both the advantages and disadvantages of trading ETFs, investors can make informed decisions and build a portfolio that is best suited for their needs.

Why stock and bond ETFs are chosen for this strategy

The primary reason why stock and bond ETFs are chosen for this strategy is due to the inverse correlation between stocks and bonds. This has been observed since the 1980s and is still true today. When one market goes up, the other market typically goes down. This means that investors can make money in both bull and bear markets by investing in both stocks and bonds. Here’s a correlation chart between the daily returns of the S&P 500 (SPY) and Long-term bonds (TLT). The negative slope of the line means they generally move in opposite directions:

![](images/00009.jpeg)

Chart courtesy: https://rpubs.com/GMR\_NYC/921400

For example, during times of economic uncertainty, investors often flock to bonds as a safe haven investment. This results in the bond market going up, while the stock market may go down. Conversely, during times of economic growth, investors tend to move away from bonds and invest more heavily in stocks. This results in the stock market going up, while the bond market may go down.

By investing in both stocks and bonds through ETFs, investors can take advantage of these inverse correlations to potentially reduce their overall risk and increase their potential for returns. This is the basic premise of the strategy used in this approach.

The Benefits of Stock and Bond ETFs

In addition to the inverse correlation between stocks and bonds, there are many other benefits to investing in ETFs. One of the key benefits is the ability to trade a single ETF that provides exposure to a broad range of stocks or bonds. For example, the SPDR S&P 500 ETF (SPY) tracks the performance of the S&P 500, which is a broad-based index of 500 large-cap stocks. This provides investors with exposure to a diverse range of stocks in a single investment.

Similarly, the iShares 20+ Year Treasury Bond ETF (TLT) provides exposure to a broad range of long-term US Treasury bonds. This can help investors to diversify their portfolio and potentially reduce risk.

Another benefit of investing in ETFs is the lower fees compared to actively managed mutual funds. ETFs are typically passively managed, meaning that they track a specific index or benchmark. This results in lower fees, which can help to increase an investor's potential returns over the long-term.

Finally, ETFs are highly liquid investments, which means that they can be bought and sold throughout the day on an exchange. This provides investors with increased flexibility and the ability to quickly take advantage of market opportunities.

Conclusion

The use of stock and bond ETFs in this strategy is based on the inverse correlation between these two markets. By switching between both stocks and bonds, investors can potentially reduce their overall risk and increase their potential for returns. Additionally, ETFs offer many other benefits, such as low fees, diversification, and liquidity. When used in combination with a solid investment strategy, stock and bond ETFs can be a wise investment choice for both new and experienced investors. So consider trading the symbol "SPY" for the S&P 500 and "TLT" for long-term US treasury bonds, and start taking advantage of the benefits of ETF investing today.

The role of diversification

Diversification is a key concept in investing and trading that refers to spreading your investments across a variety of different assets or markets in order to reduce risk. The basic idea behind diversification is that by investing in a variety of assets, you can minimize the impact that any one investment can have on your portfolio. This means that if one asset or market underperforms, you still have other investments that may perform well and help to balance out your overall returns.

In the world of trading, diversification is particularly important due to the high level of risk that can come with any single trade or investment. Traders who fail to diversify their portfolios may be exposed to high levels of risk, particularly if they invest heavily in a single market or security. This can lead to large losses and a significant setback to their overall portfolio.

The Benefits of Diversification

One of the key benefits of diversification is that it can help to reduce risk in your portfolio. By investing in a variety of different assets, you are essentially spreading your risk across different markets and sectors. This means that if one asset or market experiences a downturn, your overall portfolio is less likely to be impacted as severely. This can help to smooth out your returns over time and potentially reduce volatility in your portfolio.

Another benefit of diversification is that it can provide opportunities for higher returns. By investing in a variety of different assets, you are not limited to the performance of a single market or security. This means that you can potentially benefit from strong performance in multiple markets, while still protecting your portfolio from significant losses.

For example, a trader who invests solely in tech stocks may be exposed to significant risk if the tech sector experiences a downturn. However, a trader who diversifies their portfolio by investing in multiple assets, such as gold, bonds, and commodities, may be able to achieve higher returns while reducing their overall risk exposure.

Diversification Strategies

There are a variety of different strategies that traders can use to diversify their portfolios. One popular strategy is to invest in a mix of stocks, bonds, and cash. This approach can help to spread risk across different asset classes, and may be particularly beneficial for traders who are looking for more stable, long-term investments.

Another strategy is to invest in multiple markets, such as international stocks and bonds. This can help to spread risk across different countries and regions, and may be particularly beneficial for traders who are looking to benefit from growth opportunities in emerging markets.

Some traders may also choose to diversify their portfolios by investing in alternative assets, such as real estate, commodities, or cryptocurrencies. These types of assets can offer unique benefits and diversification opportunities, but may also be subject to greater volatility and risk.

What I like to do is build strategies on a wide variety of markets, and trade them all at the same time. That’s the secret to ultra-smooth returns. When one strategy zigs, the others zag.

Challenges to Diversification

While diversification is generally considered to be a key aspect of successful trading, there are some challenges that traders may face when attempting to diversify their portfolios. One challenge is the potential for overlapping investments. For example, if a trader invests in multiple tech stocks, they may still be exposed to significant risk if the tech sector experiences a downturn.

Even worse, during a bear market, when stocks are generally declining, nearly all stocks tend to become correlated to each other. This means that diversification among stocks becomes almost pointless, as even well-performing stocks can suffer significant losses due to the overall market conditions.

In such scenarios, investors who have a diversified portfolio that includes different types of assets such as bonds, commodities, or alternative investments such as real estate or cryptocurrencies may fare better. This is because different asset classes have different levels of correlation with the stock market, and some may actually benefit from a downturn in equities.

However, it's important to note that diversification is still important in the long run. Correlations may change over time, and a diversified portfolio can help to minimize risks and achieve better long-term returns. Additionally, not all bear markets are created equal, and some stocks may still perform relatively well during a downturn.

Moreover, it's worth noting that correlation among stocks isn't always high. In a bull market or a period of low volatility, stocks may not be as correlated as during a bear market. In such market conditions, diversification can still be a useful strategy.

Another challenge is the potential for over-diversification. While diversification can help to reduce risk, investing in too many assets or markets can also reduce the potential for high returns. This is because the benefits of diversification may be diluted if a portfolio is spread too thin.

Diversification is a crucial component of successful trading. By spreading risk across different assets and markets, traders can potentially reduce their overall risk exposure and benefit from higher returns. However, diversification can also be challenging, and traders must carefully consider their investment goals and strategies in order to achieve the right balance of risk and reward. By understanding the role of diversification and developing a solid diversification strategy, traders can build a more resilient portfolio.

 

Chapter 3:  
  
The Power of Trend Following

 

What is trend following and how it works

Trend following is a popular trading strategy that involves analyzing the current trend of a particular asset or market and then making trades based on that trend. This strategy is based on the idea that trends tend to continue, and that by following the trend, traders can potentially capture significant profits.

At its core, trend following is a very simple concept. Traders who follow this strategy typically look for assets or markets that are moving in a particular direction, whether up or down, and then attempt to ride that trend as far as possible. What is already going up tends to keep going up. What’s going down will often keep moving down. Determining the trend can involve a variety of different technical indicators and analysis methods, including moving averages, momentum indicators, and price action analysis.

One of the key benefits of trend following is that it can help traders to capture significant profits during major market trends. For example, traders who were able to identify and follow the trend in tech stocks during the late 1990s and early 2000s were able to capture significant profits as the sector soared. Similarly, traders who were able to identify and follow the trend in cryptocurrencies during the late 2010s were able to capture significant profits as well.

There are several well-known trend-following superstars who have achieved significant success using this strategy over the years. One example is Michael Marcus, who was able to turn a $30,000 trading account into over $80 million over the course of a decade using a trend-following strategy. Another example is Ed Seykota, who achieved annual returns of over 50% for several years in a row using a trend-following strategy.

Another well-known trend-following trader is Richard Dennis, who famously trained a group of novice traders known as the "Turtles" in the 1980s. These traders were able to achieve significant success using a trend-following strategy, with some reportedly achieving annual returns of over 100%. I was taught by one of the original Turtles, and learned a great deal before moving on to machine learning. 

Despite its many successes, trend following is often criticized and dismissed by some analysts and news outlets. Every few years, the news seems to declare that trend following is "dead" or no longer relevant. However, history has shown that trend following can be a very successful and profitable strategy over the long term.

In fact, I proved the power of trend following in my book, The Relaxed Investor, in which I analyzed the performance of momentum rotation strategies going all the way back to 1926. This analysis demonstrated that momentum strategies, which are closely related to trend following, have consistently outperformed the broader market over the long term.

The basic idea behind momentum strategies is that assets that have performed well in the recent past are likely to continue to perform well in the near future. By identifying these assets and investing in them, traders can potentially capture significant profits as the trend continues.

Trend following is a powerful trading strategy that has been used by some of the most successful traders in history. While it may be criticized and dismissed by some, the evidence suggests that trend following can be a very successful and profitable strategy over the long term. By analyzing trends, identifying momentum, and following the trend, traders can potentially capture significant profits and achieve long-term success.

Benefits of trend following in this strategy

As you just learned, trend following is a trading strategy that involves identifying and following the current trend of a particular asset or market. Traders who follow this strategy aim to capture profits by buying when prices are increasing and selling when prices are decreasing. There are many real-world examples of trend following in action, and some of the most successful traders in history have used this strategy to achieve significant profits.

One real-world example of trend following in action is the trading strategy used by Richard Dennis. Dennis was a highly successful trader who famously turned a $1,600 investment into $200 million in just 10 years. He used a trend following strategy that involved buying on a 55-day new high and selling on a 20-day new low.

Dennis's strategy was highly effective in capturing profits during major market trends. By buying on a 55-day new high, he was able to capture profits as the price of the asset or market continued to increase. And by selling on a 20-day new low, he was able to limit his losses when the trend eventually reversed.

Another real-world example of trend following in action is the S&P 500, which is a popular benchmark for the performance of the US stock market. As part of the seven lines of code used in this strategy, the S&P 500 is considered to be in an uptrend if today's price is greater than 80 trading days ago. If today is less than the price of the S&P 500 80 trading days ago, then it is considered to be in a down trend.

![](images/00010.jpeg)

This simple trend following strategy can be highly effective in capturing profits during major market trends. For example, if the S&P 500 has been in an uptrend for an extended period of time, traders who follow this strategy would continue to hold their positions and potentially capture significant profits as the trend continues.

However, it's worth noting that trend following isn't always successful. There are times when the trend may reverse or become range-bound, which can lead to losses for traders who continue to follow the trend. This is where mean reversion techniques can come into play.

Mean reversion is a complementary trading strategy that involves identifying when an asset or market is overbought or oversold and then making trades based on the expectation that the price will eventually revert back to its mean. By combining mean reversion techniques with trend following, traders can potentially maximize their profits and achieve long-term success.

In the next chapter, we'll discuss mean reversion techniques in more detail and how they can be used in conjunction with trend following to maximize profits. By understanding and implementing these strategies, traders can potentially achieve significant profits and long-term success in the markets.

 

Chapter 4:  
  
Mean Reversion: A Complement to Trend Following

 

What is mean reversion and how it works

Mean reversion is a trading strategy that involves identifying when an asset or market is overbought or oversold and then making trades based on the expectation that the price will eventually revert back to its mean. This strategy assumes that the price of an asset will move back towards its average price over time, which means that traders can potentially profit by buying low and selling high.

Many successful traders have used mean reversion techniques to achieve significant profits. For example, Jim Simons, the founder of Renaissance Technologies, is one of the most successful traders in history, with an estimated net worth of over $23 billion. His trading strategies are based on a combination of mathematical models and mean reversion techniques.

Another successful trader who has used mean reversion techniques is Larry Hite, who co-founded the hedge fund Mint Investment Management. Hite's trading strategies are based on a combination of trend following and mean reversion techniques, which have helped him achieve average annual returns of over 30% for his funds.

The basic idea behind mean reversion is that prices tend to fluctuate around a central value, which is known as the mean or average price. When the price of an asset moves too far away from this average price, it is considered to be overbought or oversold. Traders who follow mean reversion techniques look for these opportunities to buy or sell an asset in order to capture profits as the price reverts back to its mean.

There are many different ways to implement mean reversion techniques, but one common approach is to use technical indicators to identify when an asset is overbought or oversold. For example, the Relative Strength Index (RSI) is a popular technical indicator that is used to identify when an asset is overbought or oversold. The RSI ranges from 0 to 100, and a reading above 70 is generally considered to be overbought, while a reading below 30 is considered to be oversold.

Traders who follow mean reversion techniques might use the RSI to identify opportunities to sell an asset that is overbought or buy an asset that is oversold. For example, if the RSI for a particular stock is above 70, a trader might sell the stock with the expectation that the price will eventually revert back to its mean. Similarly, if the RSI for a stock is below 30, a trader might buy the stock with the expectation that the price will eventually rebound.

Another (perhaps dated) approach to mean reversion is to use fundamental analysis to identify when an asset is overvalued or undervalued. For example, a trader might look at a company's price-to-earnings ratio (P/E ratio) to determine whether its stock is overvalued or undervalued relative to its peers. If the P/E ratio is higher than its historical average or the average P/E ratio for its industry, the stock might be considered overvalued and a trader might look to sell it.

Overall, mean reversion is a powerful trading strategy that can be used to capture profits in a wide range of markets. Traders who use mean reversion techniques need to be patient and disciplined, as it can take time for an asset to revert back to its mean. However, by identifying opportunities to buy low and sell high, traders can potentially achieve significant profits and long-term success in the markets.

How this strategy uses mean reversion

The seven lines of code strategy is a trading strategy that uses both trend following and mean reversion techniques to identify opportunities to buy and sell assets. Specifically, the strategy uses mean reversion to identify when the price of an asset is overbought or oversold and is likely to revert back to its mean.

The mean reversion component of the strategy is triggered when the price of the S&P 500 ETF (SPY) is lower than it was 80 trading periods ago. This indicates that the price has fallen over a sustained period and may be oversold, meaning that it is a good time to consider buying SPY, and then getting out quickly.

Once the mean reversion component of the strategy is triggered, the strategy looks to buy SPY when a 6-day exponential moving average (EMA) crosses below the 5-day simple moving average (SMA). This is a signal that the asset is trading at a discount to its recent price and may be oversold, indicating that it could be a good time to buy.

![](images/00011.jpeg)

Most traders believe that a crossover like this would give a sell signal. However, the seven lines of code strategy uses mean reversion to recognize that sometimes the market can overreact and push prices too low, leading to an opportunity to buy low.

The strategy sells when the 6-day EMA crosses above the 5-day SMA. This is a signal that the asset is trading at a premium to its recent price and may be overbought, indicating that it could be a good time to sell. When this happens, the strategy sells SPY and buys long-term US Treasury bonds (TLT). This is because the price of TLT tends to rise when the price of the S&P 500 falls, making it a good hedge against a potential decline in equity markets.

![](images/00012.jpeg)

The use of mean reversion in the seven lines of code strategy allows traders to take advantage of market movements that are driven by sentiment, emotions, and liquidity issues rather than fundamental factors. By identifying when prices are likely to revert back to their mean, traders can make informed decisions about when to buy and sell assets, potentially generating profits even in volatile markets.

In simple terms, the strategy looks to buy assets when they are trading at a discount to their recent price and sell assets when they are trading at a premium. This is based on the idea that prices tend to revert to their mean over time, allowing traders to profit from short-term market movements.

The benefits of combining trend following and mean reversion

The seven lines of code trading strategy is a combination of trend following and mean reversion techniques, which can provide significant benefits to traders. The strategy uses trend following to identify market trends and mean reversion to capitalize on short-term fluctuations in the market. By combining these two approaches, the strategy is able to generate consistent returns with less volatility than other trading strategies.

One of the primary benefits of combining trend following and mean reversion is that it can help traders achieve a more balanced portfolio. Trend following is effective in identifying long-term market trends, allowing traders to capture gains over a sustained period. However, this approach can also lead to losses when the market turns against the trend. By incorporating mean reversion techniques, traders can take advantage of short-term market fluctuations to generate profits, while also limiting losses in bearish markets.

The seven lines of code strategy has been shown to deliver consistent returns over the long-term. The strategy has generated an average annual gain of 19% since 2000, significantly outperforming the S&P 500. This is largely due to the strategy's ability to capture gains in bullish markets, while also limiting losses in bearish markets. In 2008, for example, when the S&P 500 was down 37%, the strategy was up 23%, demonstrating its ability to generate profits even in the most challenging market conditions.

Another benefit of combining trend following and mean reversion is that it can help to reduce volatility in a portfolio. The seven lines of code strategy has been shown to have half the volatility of a buy and hold strategy, which can help to limit the impact of market fluctuations on a trader's portfolio. This is particularly important for traders who are looking to generate consistent returns over the long-term, as it can help to minimize the impact of short-term market movements.

The benefits of combining trend following and mean reversion extend beyond the seven lines of code strategy, and are applicable to a wide range of trading strategies. By incorporating both techniques into their trading approach, traders can achieve a more balanced and diversified portfolio, while also generating consistent returns with less volatility.

In simple terms, the seven lines of code strategy combines two effective trading techniques - trend following and mean reversion - to generate consistent returns over the long-term. By using trend following to identify long-term market trends and mean reversion to take advantage of short-term market fluctuations, the strategy is able to deliver significant benefits to traders, including consistent returns and reduced volatility.

 

Chapter 5:  
  
A Track Record of Success

 

How the strategy has performed over the past 20 years

The seven lines of code strategy, which combines trend following and mean reversion techniques, has performed remarkably well over the past 20 years. Since its inception in 2003, the strategy has produced an average annual gain of 19%. This is an impressive feat, especially when compared to the S&P 500, which has averaged an annual gain of only 7.96% over the same period.

One of the key benefits of the strategy is its ability to perform well in both bull and bear markets. For example, in 2008, when the S&P 500 was down 37%, the strategy was up 23%. This is a testament to the power of mean reversion between two asset classes, as the strategy trades both stocks and bonds ETFs.

In fact, the strategy's overall performance is double that of a simple buy and hold strategy, with half the volatility. This is due to the combination of trend following and mean reversion, which allows the strategy to take advantage of both the upward and downward trends in the market.

![A picture containing table Description automatically generated](images/00013.jpeg)

To illustrate the performance of the strategy, let's take a look at some specific examples. In 2005, the strategy gained 8.9%, while the S&P 500 was up 4.8%%. In 2011, the strategy gained 47%%, while the S&P 500 gained only 1.9%. And in 2020, the strategy gained 75%, while the S&P 500 gained 18%.

It's important to note that the strategy is not immune to losses. For example, in 2022, the strategy lost 9%, while the S&P 500 lost 18%. However, these losses are generally mitigated by the strategy's overall strong performance over the long-term.

The success of the seven lines of code strategy can be attributed to several factors. First, the use of machine learning on a supercomputer with 3,500 CPUs allowed for the creation of a highly robust trading algorithm that could generate highly accurate trade signals. Second, the use of trend following and mean reversion techniques allows the strategy to take advantage of both bullish and bearish trends in the market.

Finally, the simplicity of the strategy cannot be understated. The seven lines of code make it easy for traders to implement and follow, without the need for complex analysis or technical indicators. This simplicity is a key factor in the strategy's success, as it allows traders to stay disciplined and focused on their long-term goals.

In conclusion, the seven lines of code strategy has performed exceptionally well over the past 20 years, with an average annual gain of 19%. The strategy's ability to perform well in both bull and bear markets, combined with its simplicity and use of cutting-edge technology, has made it a powerful tool for traders looking to achieve strong long-term returns.

Average gains and risk management

The stock market can be unpredictable, and it's essential to have a trading strategy that can help you manage risks while maximizing your gains. In this chapter, we'll take a look at the risk management techniques used in the seven lines of code strategy and how they have contributed to its success.

One of the most crucial aspects of the strategy is the ability to identify when the market is in an up or downtrend. As we discussed earlier, the strategy uses a combination of trend following and mean reversion techniques to identify these trends.

When the S&P 500 is in an uptrend, the strategy doesn't use close stop losses. This means that it doesn't sell when the market dips slightly – otherwise the trader would exit too early. This is similar to the approach taken by Old Turkey, a legendary trader from the book "Reminiscences of a Stock Operator." Old Turkey was known for his long-term outlook and his ability to hold on to his stocks through thick and thin. He would often say, "it's a bull market, you know," and refused to sell his stocks, even in the face of significant drops in price.

However, the seven lines of code strategy also uses risk management techniques to ensure that traders don't hold on to losing positions for too long. When the S&P 500 is in a downtrend, the strategy looks for small gains rather than trying to hold on to the position in the hopes that the trend will reverse.

On average, the strategy has made gains of 1.3% per trade and holds its positions for an average of 15 days. This means that the strategy is quick to take profits when the market is in a downtrend, limiting potential losses. By contrast, during an uptrend, the strategy is willing to ride out the market and capitalize on the potential gains.

The combination of trend following and mean reversion techniques used in the strategy has been key to achieving these results. By following the trends, traders can identify the best times to enter the market and hold on to their positions. But by also using mean reversion techniques, traders can take advantage of small gains in the market when it's in a downtrend and avoid significant losses.

The strategy's average gains of 1.3% per trade might not seem like much, but over time, they add up. If you were to invest $10,000 and make a 1.3% gain on each trade, you would have over $15,000 after five years. This is a considerable gain when compared to the performance of the broader market, which has averaged annual gains of around 9%.

The strategy's risk management techniques also help to limit potential losses. By not using close stop losses when the market is in an uptrend, traders can avoid being shaken out of their positions prematurely. This means that they can hold on to their positions and wait for the market to rebound, as it inevitably does.

Overall, the seven lines of code strategy has been highly effective at managing risks while achieving solid returns. By combining trend following and mean reversion techniques and using risk management strategies, traders can take advantage of both bull and bear markets, ultimately leading to greater long-term success.

Comparison with other investment strategies

Investing in the stock market can be intimidating, especially for new investors who may not have much experience in the field. In an effort to make investing more accessible, many simple investment strategies have been developed. One such strategy is the seven lines of code strategy, which uses machine learning to generate trade signals based on trend following and mean reversion techniques.

To better understand how the seven lines of code strategy compares to other simple investment strategies, let's take a closer look at one of the most common techniques: "buy and hold."

"Buy and hold" is a simple investment strategy in which an investor buys a stock or fund and holds it for a long period of time, usually years or even decades, regardless of market fluctuations. The idea behind this strategy is that over the long term, the stock market tends to go up, and therefore, investors who hold their investments for a long period of time will benefit from this growth.

While "buy and hold" may seem like a straightforward and low-risk investment strategy, it does have some drawbacks. For one, it is difficult to know when to buy and when to sell, and it can be tempting to hold onto a losing investment for too long in the hopes that it will eventually rebound. In this way, "buy and hold" becomes “buy and fold” - investors buy in and then fold, finding it impossible to hold on through a deep decline.

In contrast, the seven lines of code strategy uses a combination of trend following and mean reversion techniques to generate trade signals that aim to maximize profits while minimizing risk. By buying and selling ETFs like "SPY" and “TLT" based on market trends and movements, this strategy can quickly adjust to changing market conditions, maximizing returns and reducing losses.

In terms of comparing the return of the seven lines of code strategy to other simple investment techniques, there are a few key factors to consider. One important factor is risk. While "buy and hold" may seem like a low-risk strategy, it can be risky over the long term, especially if an investor is holding onto a losing investment for too long. In contrast, the seven lines of code strategy actively manages risk by adjusting investments based on market conditions.

Another important factor to consider is returns. Over the past 20 years, the seven lines of code strategy has shown an average annual gain of 19%, which is significantly higher than the average return of many other investment strategies. For example, the average annual return of the S&P 500 over the past 20 years has been around 8%, while the average annual return of bonds has been around 3%.

In conclusion, while "buy and hold" may seem like a simple and low-risk investment strategy, it does have some drawbacks that can make it risky over the long term. In contrast, the seven lines of code strategy uses a combination of trend following and mean reversion techniques to generate trade signals that aim to maximize profits while minimizing risk. And, based on the past 20 years of performance, this strategy has proven to be a highly effective and profitable investment technique.

 

Chapter 6:  
  
Trading Systems vs Chart Patterns

 

Debunking the pseudoscience of chart patterns

After decades in the trading world, I was frustrated with the hype surrounding chart patterns. It's a well-known concept that traders use chart patterns to make trading decisions. But I always had a nagging feeling that the whole thing was just pseudoscience – because it never seemed like any two chartist came up with the same answers.

That's when I decided to put it to the test. I invested a significant amount of money in building a supercomputer network and brought together a team of experts to help me analyze every chart pattern in existence. I wanted to see if there was any real science behind the hype.

We spent 18 months analyzing every chart pattern with our supercomputer. It was an exhaustive effort. We considered every possible variable, including the frequency of the pattern, the time frame it appeared in, and what exactly defines a “top” and “bottom.” We looked at billions of chart patterns to see if there was any predictive power in them.

And what did we find? Well, it was disappointing. We found that chart patterns had no predictive power. None. There was no pattern that had a statistically significant ability to predict market movements.

This was a bit of a shock for us. We had hoped to find something that would help traders make better decisions. But we had to face the truth: chart patterns are pseudoscience. They might look impressive, but they don't actually predict anything. Chart patterns are mostly random. The human brain is a pattern recognition machine, and will see patterns in random things like clouds or vegetation. This is known as pareidolia. 

This discovery was a significant turning point for me. It helped me understand that in the world of trading, you need to base your decisions on data and analysis, not on guesswork or superstition.

Of course, there are still those who swear by chart patterns. They say they've made money using them. Even a broken clock is wrong twice a day. But as for me and my team, we'll stick with the data. We believe that the only way to succeed in trading is by relying on solid research and analysis.

So, the next time someone tries to sell you on a chart pattern, just remember: it's pseudoscience because it is not repeatable. You could lock 100 chart technicians in a room. When they come out, they’d have 100 different answers. Stick to the data, and you'll be much better off in the long run.

Understanding the benefits of a systematic trading approach

As a veteran trader, I can attest to the emotional roller coaster that comes with discretionary trading. I've experienced the high highs and low lows, and it's not an easy journey. In fact, I blew out three trading accounts before I realized that a systematic approach was the key to success.

With a systematic trading approach, you take the emotion out of trading. You don't have to make decisions based on gut feelings or hunches. Instead, you have a set of rules that you follow consistently. This takes the guesswork out of trading and makes it much easier to stick to your plan.

One of the biggest benefits of a systematic trading approach is that it helps you avoid emotional biases. When you're trading based on emotions, you're more likely to make decisions that aren't in your best interest. Fear and greed can cloud your judgment and lead you to make impulsive decisions. With a systematic approach, you're less likely to make these mistakes.

Another benefit of a systematic trading approach is that it helps you manage risk. By having a set of rules that you follow consistently, you can limit your downside risk. You can set stop-loss orders that automatically trigger when a trade goes against you. This helps you avoid big losses and protects your trading account.

A systematic trading approach also allows you to backtest your strategy. This means you can see how your strategy would have performed in the past. You can analyze historical data and see how your strategy would have done in different market conditions. This can help you refine your strategy and make it more effective.

In addition to these benefits, a systematic trading approach can also help you avoid overtrading. When you're trading based on emotions, you may be tempted to enter and exit trades more frequently than you should. This can lead to higher transaction costs and lower profits. With a systematic approach, you have a set of rules that tell you when to enter and exit trades, so you're less likely to overtrade.

Overall, a systematic trading approach can help you become a more disciplined and successful trader. It takes the emotion out of trading, helps you manage risk, and allows you to backtest your strategy. With a systematic approach, you can avoid the emotional roller coaster that comes with discretionary trading and achieve more consistent results.

Why relying on intuition can be detrimental to investment success

![](images/00014.jpeg)

Earl Nightingale, the famous American author and motivational speaker, once said that one of the keys to success is to look at what the majority is doing and simply do the opposite. This can be particularly applicable to investment success, where intuition and emotions can often lead to costly mistakes.

For instance, many traders rely on intuition and gut feelings to make investment decisions. They may feel that a certain stock is going to go up, or that the market is going to crash, based on a hunch or a feeling. However, relying on intuition in this way can be detrimental to investment success.

The reason for this is that our intuition and emotions are often influenced by biases and emotions, which can cloud our judgment and lead to irrational decision-making. For instance, we may be influenced by the latest news headlines or by the opinions of others, rather than relying on objective data and analysis.

A great example of this is the use of moving averages in trading. Many traders will sell when a moving average crosses below another one, as they believe this signals a downtrend in the market. However, as we’ve already discussed, this can be a great time to buy into a mean reversion trade. This is an example of how intuition can be wrong, and why relying on data and analysis is crucial.

The danger of relying on intuition in investing is that it can lead to impulsive decisions, based on emotions rather than objective data. This can lead to missed opportunities and costly mistakes, as we may be making decisions based on fear, greed, or other emotions, rather than on the facts.

To avoid these pitfalls, it is essential to have a systematic trading approach that is based on sound data, analysis, and risk management. This means using objective criteria, such as technical indicators, to make investment decisions, and having a set of rules that are followed consistently, regardless of emotions or market conditions.

A systematic approach also helps to remove bias from investment decisions. By relying on objective criteria, rather than intuition, investors can reduce the influence of emotions and biases that can cloud their judgment. This can lead to more consistent and profitable investment decisions over the long term.

Relying on intuition in investment can be detrimental to success, as it can lead to impulsive and emotional decisions that are not based on objective data and analysis. By using a systematic approach that relies on objective criteria and rules, investors can reduce the influence of emotions and biases and make more consistent and profitable investment decisions.

Chapter 7:  
  
Applying the Simple Trading Strategy

 

How to implement the strategy in practice

Benjamin Franklin once said, "If you fail to plan, you are planning to fail." This quote is especially true in the world of systematic trading, where having a well-defined plan can mean the difference between success and failure. And that's exactly what the seven lines of code strategy is – a well-defined plan that takes the emotion out of trading.

Now, don't let the fact that it's only seven lines of code fool you. This strategy is not something you can outsmart. You can't tinker with it or try to make it better. It's an exact plan that has been backtested and proven to work. So, if you want to implement this strategy, you need to stick to the plan.

The beauty of this strategy is that the news doesn't matter. You don't have to read every financial news article or watch every news program to make a decision. You just need to follow the plan. The plan tells you exactly what to do and when to do it. You can relax and focus on other things, like your hobbies or spending time with your loved ones.

To implement the strategy, you need to have a brokerage account set up for trading ETFs. That's it. No need to spend a lot of money on expensive software or hire a team of experts. You can use free online software or excel to calculate the two moving averages and the price 80 trading days ago.

The strategy is easy to follow. If the close in SPY is less than the close of 80 days ago, then stocks are in a downtrend, and you should look for mean reversion trades. 

You buy "SPY" when the 6-day exponential moving average crosses below the 5-day simple moving average, and you sell "SPY" and buy "TLT" when the exponential moving average crosses above the simple moving average. It's that easy. You don't have to think about what to do next or second-guess yourself. Just follow the plan.

I’m over-simplifying just a bit here because I want you to grasp the main concepts. Now we’ll go over each line of code and what it means. Remember: The supercomputer wrote this strategy in C code. It’s a bit counter-intuitive because I told the A.I to create a strategy that’s very profitable in as few lines of code as possible. Occam’s Razor. So bear with me as I explain what each line of code means.

![](images/00005.jpeg)

1)   This first line of code looks for the price of SPY 80 days ago.

2)   Now variable se0 is assigned that number

3)   V0 is equal to the 5-day simple moving. This is considered the “slow” moving average

4)   V2 is assigned the value of the 6-period exponential moving average with a smoothing of 3. This is considered the “fast” moving average even though it’s calculated over a longer period. That’s because exponential averages react faster.

5)   V1 is now assigned the value of the 6-period exponential moving average

6)   Now the exponential moving average is compared to the price of SPY 80 days ago. Which is smaller? Place that value into v1

7)   If the smaller value that was put into v1 is greater than the “slow” 5-period moving average, then it’s time to “sell” and get into TLT.

Line number 6 is the most confusing, so let’s address that.

Let say that the S&P 500 has been falling like a rock, so the price of SPY 80-periods ago is 500. The value of the “fast” 6-period exponential moving average is 310. The smallest number in line 6 will now be the “fast” EMA. Now it’s very much possible that we’ll see the two averages cross each other quite often.

![](images/00015.jpeg)

Now let’s say that SPY is in blastoff mode. The price of SPY 80-periods ago is way down at 380, and the current price of SPY is 400. The “fast“ EMA will be somewhere near the current price of 400. That means the price of SPY will be the lowest number in line 6. Bottom line: no sell signal can be generated until the “fast” EMA is below the 80-day price of SPY. That’s when the trend is considered over, and the mean reversion trades begin.

But, let's be real, following a plan can be boring. That's why it's important to find ways to make it entertaining. One way to do this is to track your progress and celebrate your wins. When you see that you're making money, it's a great feeling. Celebrate your success, and use that positive energy to keep going.

Another way to make it entertaining is to use the free time you now have to do something you love. Maybe you can finally start that hobby you've always wanted to try or spend more time with your family. Whatever it is, use the extra time and energy you have to do something that brings you joy.

In conclusion, the seven lines of code strategy is a well-defined plan that takes the emotion out of trading. It's easy to implement, and you don't have to spend a lot of money on expensive software. All you need is a brokerage account set up for trading ETFs. Stick to the plan, track your progress, and find ways to make it entertaining. Remember, if you fail to plan, you are planning to fail. So, don't leave your investment success up to chance. Follow the plan and watch your wealth grow.

Chapter 8:  
  
Conclusion and Final Thoughts

 

Summary of the strategy and its benefits

Alright, my friend, it's time to wrap up and summarize what we've learned today about the seven lines of code trading strategy.

So, to begin with, this strategy is based on a combination of trend following and mean reversion techniques. It's an exact plan that is not affected by the noise of the news or your emotions. You simply look to buy the S&P 500 (SPY) when the price is greater than 80 trading days ago. If the S&P 500 is in a downtrend (price is lower than 80 trading days ago), you look for the mean reversion trades between SPY and TLT.

The beauty of this strategy lies in its simplicity. It's just seven lines of code, but it has shown a 19% annual gain since 2003. It was up 23% in 2008 when the S&P 500 was down 37%. The overall performance is double that of buy and hold, with half the volatility. This strategy has proven to be effective in any market condition, and it can help you make profits in both bull and bear markets.

The seven lines of code strategy is based on sound statistical analysis, not on intuition or guesswork. It doesn't rely on chart patterns or other pseudoscientific methods that have been debunked time and time again. This strategy is all about discipline and following the plan. By doing so, you can avoid the emotional rollercoaster that comes with discretionary trading.

To implement this strategy, you need a brokerage account set up for trading ETFs, and you can use free online software or Excel to calculate the two moving averages and the price 80 trading days ago. It's important to stick to the plan and not try to outsmart the strategy, as doing so can lead to losses.

In summary, the seven lines of code strategy is a simple and effective way to invest in the stock market. It has proven to be profitable and less volatile than other strategies, and it's based on sound statistical analysis rather than intuition or guesswork. By following the plan and avoiding emotional trading, you can take advantage of this strategy and make profits in any market condition.

Thoughts on the future of investing and trading strategies

Investing and trading strategies are constantly evolving, and it's important to stay on top of the latest advancements to maximize gains and minimize risks. One of the biggest breakthroughs in recent years is the recognition that big data is the new oil. Companies like Google have shown us that having access to massive amounts of data can be worth billions in profits. 

In the world of investing and trading, we're seeing more and more sophisticated strategies that incorporate machine learning and supercomputing. These tools allow us to analyze vast amounts of data and find patterns and relationships that would be impossible to identify through traditional analysis.

One area where these techniques are particularly powerful is in analyzing exotic data, such as ETF mispricings. By using advanced algorithms and machine learning techniques, we can identify situations where the market has mispriced an ETF, and take advantage of these opportunities to make a profit.

Another area where advanced data analysis is making a big impact is in the use of hard-to-come-by ETF fund flow data. This data has proven to be highly predictive of just about any asset class and stock, and can be used to make profitable trades with a high degree of accuracy.

But perhaps the biggest breakthrough in trading strategies is the concept of combining different techniques together to create a hyper-smooth and consistent portfolio. The idea here is that by using several different strategies together, you can smooth out the inevitable bumps and dips that come with any one strategy.

For example, by combining a trend-following strategy with a mean reversion strategy, you can take advantage of both market trends and price reversals. This can result in a portfolio that is highly profitable and resistant to major market fluctuations.

In fact, we're already seeing some traders achieve 100% profitable months by using these kinds of combined strategies. The future of trading and investing is all about using big data and advanced algorithms to create powerful, yet simple trading strategies that can take advantage of the many opportunities that exist in the markets.

The bottom line is that if you want to stay ahead of the curve in the world of investing and trading, you need to be willing to embrace new technologies and approaches. The opportunities are endless, and the rewards can be enormous for those who are willing to take the time to learn and apply these new techniques. So don't be afraid to experiment, and always be on the lookout for new and innovative ways to approach the markets.

Encouragement to take action and start using the strategy today

As the famous Chinese proverb goes, "The journey of 1000 miles starts with the first step." In other words, it's important to take action if you want to achieve something. You can read all the books in the world, but if you don't put any of that knowledge into practice, it's all for naught.

As Thomas Jefferson once said, "Don't put off until tomorrow what you can do today." There's no better time to start implementing the seven lines of code strategy than right now. The longer you wait, the more opportunities you're missing out on.

In the words of the great Napoleon Hill, "Action is the real measure of intelligence." It's not enough to simply know what you should be doing. You have to actually take action and do it.

One of my clients, Josh, took action and it paid off. He placed #3 out of 18,000 on Fundseeder, a platform co-founded by the popular author of the Market Wizards books, Jack Schwager. It's proof that the strategy works and that anyone can achieve success with it.

So don't wait any longer. Start implementing the seven lines of code strategy today. Open a brokerage account, set up your moving averages, and start trading ETFs. Remember, the journey of 1000 miles starts with the first step.

These folks took the leap, and have reaped the reward:

![](images/00016.jpeg)

Thank you for taking the time to read this book. I hope the seven lines of code brings you success. I want you to experience the joy and freedom of systematic trading. When I got tired of losing money in the 90’s, I started programming and backtesting my strategies before making a trade. It was as if the clouds parted, the sun was shining, and the birds were chirping. For the first time, it all made sense. 

How to Grab Access to 100 Top Performing A.I Strategies…

![](images/00017.gif)

My jaw almost dropped to the floor when I heard the news. Long-time Portfolio Boss member, Josh Jarrett, just made the Top 5 on all of Fundseeder out of an estimated 18,000 traders. 

If you didn’t know already, Fundseeder was co-founded by one of the most well-known names in the trading industry – Jack Schwager. He’s the author of the Market Wizards books. I’ve read all of them cover to cover.

Fundseeder’s purpose is to track the real-money accounts of traders, then match the top performers with investment money. So, placing at the top could give him access to millions in capital.

Not only did I convince Josh to share the secret behind his top ranking on Fundseeder, I talked him into sharing 100 of his top performing strategies with you.

And I’ll reveal his latest secret weapon that put him over the top: Cycle Reversals.

Cycle Reversals have shown up to 489% annual gains with 100% winning months. Cha-ching! Click the link, and I’ll tell you all about this unique discovery.

[https://portfolioboss.com/outfox](https://portfolioboss.com/outfox)