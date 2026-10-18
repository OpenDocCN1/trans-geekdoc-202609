...[/content].

We need to translate everything, preserving line breaks. Also need to handle inline code (backticks) and code blocks (triple backticks) not translated. Also need to keep links: translate the link text but keep URL.

We must be careful: any bold (**text**) should be translated content and keep **...**. Italic (*text*) also translate content and keep *...*. Inline code `code` not translated. Code block not translated.

List items: keep list markers and translate content.

Tables: keep format.

Quotation blocks: keep format.

Also need to ensure we don't miss any lines. The given content includes many lines, images (![](...)), source lines, figure caption, etc. Those are not part of translation? They are part of content, need to translate the textual parts, but image placeholder likely remains as is (since it's not text). The image line is `![](img/ab11be88faa3a9baf1bf1607f21e9805_116_0.png)`. That's not text, but we can keep it unchanged (since no translation needed). The source line: "*Source: https://dune.com/hildobby/ethereum-nfts*". The asterisks indicate italic? Actually it's "*Source: ..." which is italic. The rule: italic need to translate content and keep symbols. So we need to translate "Source:" to Chinese "来源:" and keep the URL unchanged. Also keep the asterisks. So we need to translate the whole line: "*Source: https://dune.com/hildobby/ethereum-nfts*". So becomes "*来源: https://dune.com/hildobby/ethereum-nfts*". Keep the asterisks.

Figure caption: "Figure 4.6 SuperRare adoption by artists and collectors". That's a caption; we need to translate "SuperRare adoption by artists and collectors" to Chinese. So "图 4.6 SuperRare 艺术家和收藏家的采用". But need to keep "Figure 4.6" maybe translate "Figure" to "图". Keep the number. So "图 4.6 SuperRare 艺术家和收藏家的采用". However maybe better: "图 4.6 SuperRare 艺术家和收藏家的采用". The phrase "adoption" -> "采用". So final: "图 4.6 SuperRare 艺术家和收藏家的采用". Keep the rest.

Now we need to translate the main body. Let's go line by line.

First line after image: "*Source: https://dune.com/hildobby/ethereum-nfts*". We'll translate.

Then "*Figure 4.6 SuperRare adoption by artists and collectors*". Translate.

Then text: "trading overall. This proposition is partially supported by Vasan et al. (2022), demonstrating that at the Foundation art marketplace, “successful artists receive disproportional, repeated investment from a small group of collectors,” indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces."

We need to translate. Keep quotes? The quotes are curly quotes “ ” which are part of the text; we need to translate the content inside quotes, preserving the quotes? The rule: translate content and keep symbols. The quotes are typographic quotes; they are part of the content. Should we keep them? Probably keep them as they are, but translate the inner text. So “successful artists receive disproportional, repeated investment from a small group of collectors,” becomes “成功艺术家获得不成比例、重复的投资来自少数收藏家”. Keep the curly quotes.

Also "trading overall." maybe part of previous sentence? It seems "trading overall." is a fragment; maybe it's part of previous sentence. We'll translate as "整体交易". But need to see context: The preceding line is a figure caption; maybe the sentence continues. We'll translate "trading overall." as "整体交易". Keep punctuation.

Next: "In addition, the presented data does not include NFT art from traditional auction houses, like Sotheby's,⁸ Christie's,⁹ and Phillips,¹⁰ which have all recently begun trading digital art, especially the more pricey artworks."

Translate: "此外，所展示的数据未包括来自传统拍卖行的 NFT 艺术，例如苏富比、⁸ 佳士得、⁹ 和 Phillips、¹⁰，它们最近都开始交易数字艺术，尤其是更昂贵的作品。" Need to keep superscript numbers? They are footnote markers. Should we translate them? They are part of text; we can keep them as is (the numbers). The footnote markers are superscript numbers; they are not to be translated. So keep "⁸", "⁹", "¹⁰". Also "Sotheby's" -> "苏富比", "Christie's" -> "佳士得", "Phillips" -> "Phillips". Keep the apostrophe? It's part of name; we can keep as is.

Next: "Furthermore, NFT art transactions can be accomplished on a P2P basis between trusted individuals."

Translate: "此外，NFT 艺术交易可以在可信个人之间以点对点（P2P）方式完成。"

Next: "Outside observers can observe the transfer of NFTs, but it is impossible to determine the nature of these trades."

Translate: "外部观察者可以观察 NFT 的转移，但无法确定这些交易的性质。"

Next: "Therefore, the overall NFT art market might be larger than the volume of new art-focused NFT marketplaces suggests."

Translate: "因此，整体 NFT 艺术市场可能大于新兴的以艺术为导向的 NFT 市场的交易量。"

Now the next section header: "### 4.4.4 Price Dynamics". That's a heading; we need to translate the heading? The rule: headings are part of content; we need to translate content but keep formatting. So "### 4.4.4 Price Dynamics" -> "### 4.4.4 价格动态". Keep the "###". So "### 4.4.4 价格动态".

Next paragraph: "Understanding the determinants of price fluctuations in the market for NFT art is especially challenging given that it is new and, at least historically, has been heavily influenced by speculative investments and the presence of “whales,” or large NFT holders."

Translate: "理解 NFT 艺术市场中价格波动的决定因素尤其具有挑战性，因为它是新兴的，且在历史上主要受到投机投资和“鲸鱼”（即大额 NFT 持有者）的存在的影响。" Need to keep quotes around “whales”. The quotes are curly quotes; we need to translate the word "whales" to Chinese "鲸鱼" and keep the quotes. So “whales” -> “鲸鱼”. Keep the curly quotes.

Next: "We apply insights from other asset markets and break down the price determinants into the following categories:" Translate: "我们从其他资产市场汲取灵感，并将价格决定因素分为以下类别："

Now list items:

- **Artist’s Reputation:** Much like in the traditional art market, the reputation and popularity of the artist can play a significant role in the value of an NFT. Works by well-known and respected artists generally command higher prices.

We need to translate the bold label and the text. The bold label "**Artist’s Reputation:**" should be translated but keep the bold markup. So "**艺术家声誉:**". Then the text: "Much like in the traditional art market, the reputation and popularity of the artist can play a significant role in the value of an NFT. Works by well-known and respected artists generally command higher prices."

Translate: "much like 在传统艺术市场中，艺术家的声誉和知名度在 NFT 的价值中可以发挥重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。" Need to keep the period.

But we need to preserve the bold markup and colon. So:

- **艺术家声誉:** Much like 在传统艺术市场中，艺术家的声誉和知名度在 NFT 的价值中可以发挥重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。

But maybe better Chinese: "Much like 在传统艺术市场中，艺术家的声誉和知名度在 NFT 的价值中起着重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。" Keep the English "Much like" maybe translate? The rule: translate content, but keep symbols. The phrase "Much like" is English; we should translate it to Chinese. So we can translate entire sentence.

Thus:

- **艺术家声誉:** 与传统艺术市场类似，艺术家的声誉和知名度在 NFT 的价值中起着重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。

Make sure to keep the colon after the bold label.

Next list item:

- **Scarcity:** The value of an NFT can increase if it is a rare or limited edition. This is a basic principle of supply and demand: prices tend to increase when supply is limited and demand is high. This concept also applies to NFT traits within one collection, resulting in NFTs with more scarce traits being more valuable than other NFTs from the same collection (see Mekacher et al., 2022).

Translate: "稀缺性: NFT 的价值可以在它是罕见或限量版时增加。这是供需的基本原则：当供应有限且需求高时，价格倾向于上涨。该概念也适用于同一集合内的 NFT 特征，这使得拥有更稀缺特征的 NFT 比同一集合中的其他 NFT 更有价值（见 Mekacher et al., 2022）。"

Need to keep bold label: **稀缺性:**.

Next:

- **Quality of the Artwork:** The artwork’s perceived aesthetic or conceptual quality can impact its price. However, this can be highly subjective and can change over time.

Translate: "艺术作品的质量: 作品的感知美学或概念质量可以影响其价格。然而，这可能高度主观，并且会随时间而变化。"

Bold label: **艺术作品的质量:**.

Next:

- **Provenance:** The history and ownership of the NFT can affect its value. An NFT with a notable history or owned by a famous person could potentially command a higher price.

Translate: "来源: NFT 的历史和所有权可以影响其价值。拥有显著历史或由知名人物拥有的 NFT 可能会获得更高的价格。"

Bold label: **来源:**.

Next:

- **Market Sentiment:** The NFT market, like the cryptocurrency market, is heavily influenced by market sentiment. Hype, media coverage, and celebrity endorsements can all significantly impact prices.

Translate: "市场情绪: NFT 市场与加密货币市场一样，受市场情绪 heavily 影响。炒作、媒体报道和名人效应都能显著影响价格。" Need to translate "heavily influenced" -> "受...强烈影响". So Chinese: "NFT 市场与加密货币市场一样，受市场情绪的强烈影响。炒作、媒体报道和名人效应都能显著影响价格。"

Bold label: **市场情绪:**.

Next:

- **Utility:** Some NFTs come with additional benefits or utilities, such as exclusive access to events, physical goods, or additional digital content. These utilities can increase the value of the NFT.

Translate: "实用性: 部分 NFT 附带额外的好处或实用功能，例如独家活动访问、实物商品或额外的数字内容。这些实用功能可以提升 NFT 的价值。"

Bold label: **实用性:**.

Now next paragraph: "The most comprehensive research to date on the price dynamics of NFTs is Bori et al.’s (2023) study, which collected a large-scale dataset of NFTs and broke down the determinants of the prices, finding that the time component explains 41 percent of the variation in log prices. While artist idiosyncratic factors explain the majority, momentum and timing in the market play a major role. Bori et al. (2023) reaffirm the role that rarity plays, which is consistent with Kong and Lin (2021) and Dobrynskaya and Bianchi (2023), but show that the relationship between rarity and price is particularly strong for those with a fixed supply."

Translate: "到目前为止关于 NFT 价格动态的最全面研究是 Bori 等人 (2023) 的研究，他们收集了大规模的 NFT 数据集并分析了价格决定因素，发现时间因素解释了日志价格变化的 41%。虽然艺术家特有因素解释了大部分差异，但市场的动量和时机在其中发挥了重要作用。Bori 等人 (2023) 再次确认了稀缺性的作用，这与 Kong and Lin (2021) 与 Dobrynskaya and Bianchi (2023) 保持一致，但表明稀缺性与价格的关系在供应固定的情况下尤为强烈。"

Need to keep the citation format (2023) etc. Keep parentheses.

Next: "Other studies examining the price dynamics of NFTs include Goetzmann and Nozari (2022), Nadini et al. (2021), and Kräussl and Tugnetti (2023)."

Translate: "其他研究 NFT 价格动态的作品包括 Goetzmann 和 Nozari (2022)、Nadini 等人 (2021) 以及 Kräussl 和 Tugnetti (2023)。"

Next: "Like stocks, cryptocurrencies, and other tradable assets, the value of NFTs can be influenced by broader market trends, economic indicators, and investor sentiment."

Translate: "与股票、加密货币和其他可交易资产一样，NFT 的价值可以受到更广泛的市场趋势、经济指标和投资者情绪的影响。"

Next paragraph: "However, the NFT market also has unique characteristics that make it quite different from traditional asset markets."

Translate: "然而，NFT 市场也具有使其与传统资产市场相当不同的独特特征。"

Now list items:

- **Volatility:** The NFT market has shown itself to be highly volatile, with prices that can rise and fall dramatically in a short period. This is partly because it is a relatively new market with a lot of speculative investing.

Translate: "波动性: NFT 市场表现出高度波动性，价格在短时间内可以大幅上升或下降。这部分原因是该市场相对新颖，且充斥着大量投机投资。"

Bold label: **波动性:**.

- **Illiquidity:** Unlike stocks and cryptocurrencies, which can usually be sold relatively quickly if there’s enough trading volume, NFTs can sometimes be harder to sell, especially those from unknown artists or collections.

Translate: "缺乏流动性: 与股票和加密货币不同，后者在交易量足够时通常可以快速出售，NFT 有时难以出售，尤其是来自不知名艺术家或收藏的 NFT。"

Bold label: **缺乏流动性:**.

- **Regulation:** The NFT market is less regulated than traditional financial markets. This has led some critics to argue that it can lead to increased risk, including the risk of fraud, although the traditional finance sector has also experienced substantial fraud and risk-taking.

Translate: "监管: NFT 市场的监管程度低于传统金融市场。这导致一些批评者认为它可能增加风险，包括欺诈风险，尽管传统金融行业也经历了大量欺诈和风险行为。"

Bold label: **监管:**.

- **Decentralization:** NFTs are typically bought and sold on decentralized platforms, which can lead to additional complexities, including potential technical issues or vulnerabilities.

Translate: "去中心化: NFT 通常在去中心化平台上买卖，这可能导致额外的复杂性，包括技术问题或漏洞。"

Bold label: **去中心化:**.

Next paragraph: "As a result of illiquidity, transparency regarding high-value targets, and challenging (international) law enforcement, there is a potential risk for illicit behavior, such as elaborate scams, price manipulations, and money laundering."

Translate: "由于缺乏流动性、对高价值目标的透明度以及跨国执法的困难，NFT 市场存在滥用行为的潜在风险，如复杂的诈骗、价格操纵和洗钱。"

Next: "Furthermore, Huang and Goetzmann (2023) highlight a behavioral phenomenon that can emerge where potential NFT buyers focus on a censored set of NFTs selling for high prices that influence their expectations on future returns – that is, investors focus their attention on high-ticket NFT sales during a bull market and extrapolate future price movements from the past."

Translate: "此外，Huang 和 Goetzmann (2023) 指出一种行为现象，即潜在的 NFT 购买者会关注一组被 censored（被限制）的高价 NFT，这会影响他们对未来回报的预期——也就是说，投资者在牛市期间专注于高价 NFT 的销售，并据此 extrapolate（ extrapolate?）未来的价格走势。" Need to translate "extrapolate" to Chinese "推算". Also "censored" maybe "被限制" or "被审查". The original says "censored set of NFTs". Could be "被审查的". We'll translate as "被审查的". So: "Huang 和 Goetzmann (2023) 指出，潜在的 NFT 购买者会关注一组被审查的高价 NFT，这会影响他们对未来回报的预期——即投资者在牛市期间专注于高价 NFT 的销售，并据此推算未来的价格走势。"

Next: "However, once the NFT market began to collapse, these investors were slow to respond."

Translate: "然而，当 NFT 市场开始崩溃时，这些投资者反应迟缓。"

Next: "These lead-lag relationships between trading" - the sentence seems incomplete; maybe continues later. We'll keep as is but need to translate. The phrase "These lead-lag relationships between trading" is incomplete; maybe it's part of a larger sentence. We'll translate as "这些交易的先后关系". But maybe we need to keep the phrase as is? The rule: translate content, not leave English. So translate: "这些交易的先后关系". But maybe we need to continue: "between trading" maybe "between trading and ..."? Not enough context. We'll translate the part we have: "这些交易的先后关系". Keep punctuation.

Next paragraph: "No central agency currently enforces the return of stolen assets on public blockchains. Victims rely on the bad actor to return the NFTs. However, some marketplaces have established a system whereby stolen NFTs are flagged and sometimes even removed from their marketplace. Flagging stolen NFTs raises awareness to potential buyers not to purchase stolen NFTs. A registry might help to establish transparency and potentially hinder the distribution of stolen NFTs, for example, if protocols block interactions with stolen NFTs."

Translate: "目前没有中央机构强制执行公共区块链上被盗资产的返还。受害者依赖恶意行为者归还 NFT。然而，一些市场已建立系统，在被盗 NFT 被标记并有时甚至从其市场中移除后，可以提高潜在买家对购买被盗 NFT 的警惕性。登记册可能有助于建立透明度，并可能阻碍被盗 NFT 的分发，例如，如果协议阻止与被盗 NFT 的交互。"

Next section header: "### 4.5.4 Money Laundering and Price Manipulations". Translate: "### 4.5.4 洗钱和价格操纵". Keep "###".

Next paragraph: "As discussed, blockchains might make it harder to profit from stolen assets. However, money laundering and potential price manipulation schemes are harder to uncover, even in transparent settings."

Translate: "如前所述，区块链可能使从被盗资产中获利变得更加困难。然而，洗钱和潜在的价格操纵方案即使在透明环境下也更难被发现。"

Next: "In this regard, we deemed wash trading illegal for traditional asset settings (Liu et al., 2023) because it is often related to price manipulation and other illicit behaviors."

Translate: "在这方面，我们认为传统资产环境下的洗钱行为是非法的（Liu et al., 2023），因为它通常与价格操纵和其他非法行为相关。"

Next: "Capital controls, where capital holders have to prove the origin of the money, might help to restrict the influx of illegal money and increase the difficulty of money laundering."

Translate: "资本管制，即持有者必须证明资金来源的措施，可能有助于限制非法资金的流入并增加洗钱的难度。"

Next: "However, bad actors will find ways and means to circumvent these controls, like in any market setting."

Translate: "然而，恶意行为者会想尽办法规避这些控制，就像在任何市场环境中一样。"

Next: "Price manipulation schemes are equally hard to uncover and prove, especially since the NFT market is relatively illiquid."

Translate: "价格操纵方案同样难以发现和证明，尤其是因为 NFT 市场相对缺乏流动性。"

Next: "Thus, any trade has a higher likelihood of creating a price impact."

Translate: "因此，任何交易都更有可能产生价格影响。"

Next: "Regulators and law enforcement agencies should ensure that the same rules apply to all markets and settings, including the NFT market, which might include new rules for marketplaces regarding Know-Your-Customer (KYC) or Proof-of-Funds."

Translate: "监管机构和执法机构应确保所有市场和环境（包括 NFT 市场）适用相同的规则，这可能包括为市场制定新的 Know-Your-Customer（KYC）或 Proof-of-Funds 规则。"

Now next section header: "## 4.6 CONCLUSION". Translate: "## 4.6 结论". Keep "##".

Next paragraph: "The arts sector has been struggling for decades, and the sudden shock of the pandemic and the closure of arts institutions in 2020 led to an especially big blow to artists."

Translate: "艺术行业已为数十年 struggled（struggling）", but translate: "艺术行业已为数十年 struggled（struggling）" Actually need Chinese: "艺术行业已为数十年 struggled（struggling）" Let's translate: "艺术行业已为数十年 struggled（struggling）" No, we need Chinese: "艺术行业已为数十年 struggled（struggling）" Let's do: "艺术行业已为数十年 struggled（struggling）" That's not good. Better: "艺术行业已为数十年 struggled（struggling）" Hmm.

Let's translate: "艺术行业已为数十年 struggled（struggling）" Not correct. Let's do proper Chinese: "艺术行业已为数十年 struggled（struggling）" Actually "struggling" translates to "挣扎". So: "艺术行业已为数十年挣扎不已，2020 年疫情的突发冲击以及艺术机构的关闭给艺术家带来了尤其巨大的打击。" Let's translate accurately.

Sentence: "The arts sector has been struggling for decades, and the sudden shock of the pandemic and the closure of arts institutions in 2020 led to an especially big blow to artists."

Translate: "艺术行业已为数十年挣扎不已，2020 年疫情的突发冲击以及艺术机构的关闭给艺术家带来了尤其巨大的打击。"

Next: "However, these headwinds converged with the popularization of distributed ledger technology, and blockchain natives and creatives began using art as one of its main and easiest-to-understand use cases."

Translate: "然而，这些逆风与分布式账本技术的流行相结合，区块链原生和创作者开始将艺术作为其主要且最易理解的使用案例之一。"

Next: "Art NFTs began to surge in 2020 and 2021, capturing the attention of major media headlines and generating significant trading fees for the new NFT exchanges."

Translate: "艺术 NFT 在 2020 和 2021 年开始迅速增长，吸引了主要媒体标题的关注，并为新兴 NFT 交易所产生了大量交易费用。"

Next: "This chapter has addressed three aspects of the art NFT market. First, we provided background on the formation of the NFT market in the arts with a focus on the factors that have created confusion and stifled growth due to the absence of legal clarity on ownership."

Translate: "本章讨论了艺术 NFT 市场的三个方面。首先，我们提供了艺术领域 NFT 市场形成的背景，重点关注那些因缺乏所有权法律 clarity 而造成混乱并阻碍增长的因素。" Need to translate "legal clarity on ownership" -> "法律对所有权的明确性". So: "首先，我们提供了艺术领域 NFT 市场形成的背景，重点关注因缺乏法律对所有权的明确性而导致的混乱和阻碍增长的因素。"

Next: "In particular, most NFTs never clarified what ownership of them conferred; rarely did ownership of the NFT confer ownership over the artwork."

Translate: "特别是，大多数 NFT 从未明确其所有权所代表的内容；很少有 NFT 的所有权直接赋予对艺术品的所有权。"

Next: "Furthermore, there is still little judicial precedent for the enforcement of NFT contracts. There is still growing interest and legal work underway to improve the standard for NFT contracts."

Translate: "此外，关于 NFT 合同执行的司法先例仍然很少。目前仍有大量兴趣和法律工作在进行，以改进 NFT 合同的标准。"

Next: "Second, we presented evidence on the rise of NFT trading, the phenomenon of wash trading – that is, fraudulent selling of NFTs often characterized by one user who held several wallets and traded an NFT to give the impression of activity and, thus, scarcity and value."

Translate: "其次，我们提供了 NFT 交易增长的证据，以及洗钱现象——即通过持有多个钱包的用户进行欺诈性 NFT 销售，以营造活动和稀缺性的假象。"

Next: "The NFT trading market exhibited enormous growth in 2021, but this has cooled off significantly since the end of 2022."

Translate: "NFT 交易市场在 2021 年呈现出巨大的增长，但自 2022 年底以来已显著降温。"

Next: "Yet, the often-postulated price and volume bubble seems to have been at least partially caused by wash trading activity."

Translate: "然而，经常被假设的价格和交易量泡沫似乎至少部分是由洗钱活动引起的。"

Next: "Furthermore, wash trading activity seemed to be related to or driven by competition between NFT exchanges or marketplaces; for example, users might have engaged in wash trading activities to farm incentives on various marketplaces."

Translate: "此外，洗钱活动似乎与 NFT 交易所或市场之间的竞争有关或被驱动；例如，用户可能进行洗钱活动以在各种市场中获取激励。"

Next: "Third, we provided a" - incomplete. The text ends with "Third, we provided a". Probably continues later but we have to translate what's there. So "第三，我们提供了" but incomplete. Maybe we need to translate "Third, we provided a" as "第三，我们提供了". But maybe there is more after that in the original but truncated. We'll translate exactly as given: "第三，我们提供了". Keep as is.

Now after that, there is a picture line: "![](img/ab11be88faa3a9baf1bf1607f21e9805_116_0.png)". That's an image placeholder; we keep it unchanged.

Then "*Source: https://dune.com/hildobby/ethereum-nfts*". Translate as earlier: "*来源: https://dune.com/hildobby/ethereum-nfts*". Keep asterisks.

Then "*Figure 4.6 SuperRare adoption by artists and collectors*". Translate: "图 4.6 SuperRare 艺术家和收藏家的采用". Keep asterisks.

Now after that, there is a paragraph starting "trading overall." which we already translated earlier. But note that after the figure caption, there is "trading overall." which is part of the text after figure caption. We need to ensure we include that translation as well. Let's re-evaluate the ordering.

The content after figure caption: "trading overall. This proposition is partially supported by Vasan et al. (2022), demonstrating that at the Foundation art marketplace, “successful artists receive disproportional, repeated investment from a small group of collectors,” indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces."

We need to ensure we translate "trading overall." as part of the text. It appears after the figure caption line. So we need to include that sentence in translation.

Let's reconstruct the order:

- Image line (unchanged)
- Source line (translated)
- Figure caption line (translated)
- Then "trading overall." (the word "trading" maybe part of previous sentence? It might be continuation of figure caption? Actually figure caption is "Figure 4.6 SuperRare adoption by artists and collectors". Then next line is "trading overall." So maybe the figure caption is incomplete; maybe the original text had "Figure 4.6 SuperRare adoption by artists and collectors trading overall." So "trading overall." is part of caption? But we treat it as separate sentence. We'll translate "trading overall." as "整体交易". Keep punctuation.

Then the next paragraph about Vasan et al. We'll translate.

Now we need to ensure we include all lines, not missing any.

Let's go through the entire original content again to ensure we capture everything.

Original content (including line breaks) as given:

[content]

![](img/ab11be88faa3a9baf1607f21e9805_116_0.png)

*Source: https://dune.com/hildobby/ethereum-nfts*

*Figure 4.6 SuperRare adoption by artists and collectors*

trading overall. This proposition is partially supported by Vasan et al. (2022), demonstrating that at the Foundation art marketplace, “successful artists receive disproportional, repeated investment from a small group of collectors,” indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces.

In addition, the presented data does not include NFT art from traditional auction houses, like Sotheby's,⁸ Christie's,⁹ and Phillips,¹⁰ which have all recently begun trading digital art, especially the more pricey artworks. Furthermore, NFT art transactions can be accomplished on a P2P basis between trusted individuals. Outside observers can observe the transfer of NFTs, but it is impossible to determine the nature of these trades. Therefore, the overall NFT art market might be larger than the volume of new art-focused NFT marketplaces suggests.

### 4.4.4 Price Dynamics

Understanding the determinants of price fluctuations in the market for NFT art is especially challenging given that it is new and, at least historically, has been heavily influenced by speculative investments and the presence of “whales,” or large NFT holders. We apply insights from other asset markets and break down the price determinants into the following categories:

- **Artist’s Reputation:** Much like in the traditional art market, the reputation and popularity of the artist can play a significant role in the value of an NFT. Works by well-known and respected artists generally command higher prices.
- **Scarcity:** The value of an NFT can increase if it is a rare or limited edition. This is a basic principle of supply and demand: prices tend to increase when supply is limited and demand is high. This concept also applies to NFT traits within one collection, resulting in NFTs with more scarce traits being more valuable than other NFTs from the same collection (see Mekacher et al., 2022).
- **Quality of the Artwork:** The artwork’s perceived aesthetic or conceptual quality can impact its price. However, this can be highly subjective and can change over time.
- **Provenance:** The history and ownership of the NFT can affect its value. An NFT with a notable history or owned by a famous person could potentially command a higher price.
- **Market Sentiment:** The NFT market, like the cryptocurrency market, is heavily influenced by market sentiment. Hype, media coverage, and celebrity endorsements can all significantly impact prices.
- **Utility:** Some NFTs come with additional benefits or utilities, such as exclusive access to events, physical goods, or additional digital content. These utilities can increase the value of the NFT.

The most comprehensive research to date on the price dynamics of NFTs is Bori et al.’s (2023) study, which collected a large-scale dataset of NFTs and broke down the determinants of the prices, finding that the time component explains 41 percent of the variation in log prices. While artist idiosyncratic factors explain the majority, momentum and timing in the market play a major role. Bori et al. (2023) reaffirm the role that rarity plays, which is consistent with Kong and Lin (2021) and Dobrynskaya and Bianchi (2023), but show that the relationship between rarity and price is particularly strong for those with a fixed supply. Other studies examining the price dynamics of NFTs include Goetzmann and Nozari (2022), Nadini et al. (2021), and Kräussl and Tugnetti (2023).

Like stocks, cryptocurrencies, and other tradable assets, the value of NFTs can be influenced by broader market trends, economic indicators, and investor sentiment.

However, the NFT market also has unique characteristics that make it quite different from traditional asset markets.

- **Volatility:** The NFT market has shown itself to be highly volatile, with prices that can rise and fall dramatically in a short period. This is partly because it is a relatively new market with a lot of speculative investing.
- **Illiquidity:** Unlike stocks and cryptocurrencies, which can usually be sold relatively quickly if there’s enough trading volume, NFTs can sometimes be harder to sell, especially those from unknown artists or collections.
- **Regulation:** The NFT market is less regulated than traditional financial markets. This has led some critics to argue that it can lead to increased risk, including the risk of fraud, although the traditional finance sector has also experienced substantial fraud and risk-taking.
- **Decentralization:** NFTs are typically bought and sold on decentralized platforms, which can lead to additional complexities, including potential technical issues or vulnerabilities.

As a result of illiquidity, transparency regarding high-value targets, and challenging (international) law enforcement, there is a potential risk for illicit behavior, such as elaborate scams, price manipulations, and money laundering. Furthermore, Huang and Goetzmann (2023) highlight a behavioral phenomenon that can emerge where potential NFT buyers focus on a censored set of NFTs selling for high prices that influence their expectations on future returns – that is, investors focus their attention on high-ticket NFT sales during a bull market and extrapolate future price movements from the past. However, once the NFT market began to collapse, these investors were slow to respond. These lead-lag relationships between trading

No central agency currently enforces the return of stolen assets on public blockchains. Victims rely on the bad actor to return the NFTs. However, some marketplaces have established a system whereby stolen NFTs are flagged and sometimes even removed from their marketplace. Flagging stolen NFTs raises awareness to potential buyers not to purchase stolen NFTs. A registry might help to establish transparency and potentially hinder the distribution of stolen NFTs, for example, if protocols block interactions with stolen NFTs.

### 4.5.4 Money Laundering and Price Manipulations

As discussed, blockchains might make it harder to profit from stolen assets. However, money laundering and potential price manipulation schemes are harder to uncover, even in transparent settings. In this regard, we deemed wash trading illegal for traditional asset settings (Liu et al., 2023) because it is often related to price manipulation and other illicit behaviors.

Capital controls, where capital holders have to prove the origin of the money, might help to restrict the influx of illegal money and increase the difficulty of money laundering. However, bad actors will find ways and means to circumvent these controls, like in any market setting. Price manipulation schemes are equally hard to uncover and prove, especially since the NFT market is relatively illiquid. Thus, any trade has a higher likelihood of creating a price impact. Regulators and law enforcement agencies should ensure that the same rules apply to all markets and settings, including the NFT market, which might include new rules for marketplaces regarding Know-Your-Customer (KYC) or Proof-of-Funds.

## 4.6 CONCLUSION

The arts sector has been struggling for decades, and the sudden shock of the pandemic and the closure of arts institutions in 2020 led to an especially big blow to artists. However, these headwinds converged with the popularization of distributed ledger technology, and blockchain natives and creatives began using art as one of its main and easiest-to-understand use cases. Art NFTs began to surge in 2020 and 2021, capturing the attention of major media headlines and generating significant trading fees for the new NFT exchanges.

This chapter has addressed three aspects of the art NFT market. First, we provided background on the formation of the NFT market in the arts with a focus on the factors that have created confusion and stifled growth due to the absence of legal clarity on ownership. In particular, most NFTs never clarified what ownership of them conferred; rarely did ownership of the NFT confer ownership over the artwork. Furthermore, there is still little judicial precedent for the enforcement of NFT contracts. There is still growing interest and legal work underway to improve the standard for NFT contracts. Second, we presented evidence on the rise of NFT trading, the phenomenon of wash trading – that is, fraudulent selling of NFTs often characterized by one user who held several wallets and traded an NFT to give the impression of activity and, thus, scarcity and value. The NFT trading market exhibited enormous growth in 2021, but this has cooled off significantly since the end of 2022. Yet, the often-postulated price and volume bubble seems to have been at least partially caused by wash trading activity. Furthermore, wash trading activity seemed to be related to or driven by competition between NFT exchanges or marketplaces; for example, users might have engaged in wash trading activities to farm incentives on various marketplaces. Third, we provided a

[/content]

We need to translate everything, preserving line breaks. Also need to keep list items, headings, etc.

Let's go step by step.

1. Image line: `![](img/ab11be88faa3a9baf1bf1607f21e9805_116_0.png)` - keep unchanged.

2. Source line: `*Source: https://dune.com/hildobby/ethereum-nfts*` -> translate to `*来源: https://dune.com/hildobby/ethereum-nfts*` (keep asterisks).

3. Figure caption line: `*Figure 4.6 SuperRare adoption by artists and collectors*` -> translate to `*图 4.6 SuperRare 艺术家和收藏家的采用*` (keep asterisks). Note: "adoption" -> "采用". Might be "采用" or "使用". We'll use "采用".

4. Next line: `trading overall.` -> translate to `整体交易.` (maybe add period). Keep as is.

5. Next sentence: `This proposition is partially supported by Vasan et al. (2022), demonstrating that at the Foundation art marketplace, “successful artists receive disproportional, repeated investment from a small group of collectors,” indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces.`

We need to translate. Let's break:

"This proposition is partially supported by Vasan et al. (2022)" -> "这一命题部分得到 Vasan 等人 (2022) 的支持". Keep "proposition" maybe "命题". Keep "Vasan et al." as is (maybe translate "Vasan" to Chinese? Usually keep names unchanged). So "Vasan et al. (2022)" stays.

"demonstrating that at the Foundation art marketplace," -> "表明在 Foundation 艺术市场". Keep "Foundation" maybe as is (it's a name). So "表明在 Foundation 艺术市场". Could also translate "Foundation" to "基金会". But it's likely a proper name "Foundation". Keep as is.

"“successful artists receive disproportional, repeated investment from a small group of collectors,”" -> translate inside quotes: “成功艺术家获得不成比例、重复的投资来自少数收藏家”. Keep curly quotes.

"indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces." -> "表明 NFT 艺术市场的 patronage 可能比一般艺术市场的投机交易更稳定。" But need to translate "indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces." So: "表明 NFT 艺术市场的 patronage 可能比一般艺术市场的投机交易更稳定。" Keep "patronage" maybe translate as " patronage" but better Chinese " patronage" -> " patronage" is English; we can translate as " patronage" maybe " patronage" is not needed; we can say " NFT 艺术市场的 patronage" but maybe better " NFT 艺术市场的 patronage" is ambiguous. Let's translate: "表明 NFT 艺术市场的 patronage 可能比一般艺术市场的投机交易更稳定。" But "patronage" means " patronage" (赞助). So maybe "表明 NFT 艺术市场的 patronage（赞助）可能比一般艺术市场的投机交易更稳定。" However to keep it simple: "表明 NFT 艺术市场的 patronage 可能比一般艺术市场的投机交易更稳定。" But we need to translate "patronage" to Chinese " patronage" maybe " patronage" is " patronage" but we can use " patronage" as " patronage" or " patronage" -> " patronage" is " patronage" but Chinese term " patronage" is " 赞助". So we could say "表明 NFT 艺术市场的赞助可能比一般艺术市场的投机交易更稳定。" Let's do that.

Thus full translation:

"这一命题部分得到 Vasan 等人 (2022) 的支持，表明在 Foundation 艺术市场，“成功艺术家获得不成比例、重复的投资来自少数收藏家”，表明 NFT 艺术市场的赞助可能比一般艺术市场的投机交易更稳定。"

But we need to keep punctuation. Let's rewrite:

"这一命题部分得到 Vasan 等人 (2022) 的支持，表明在 Foundation 艺术市场，“成功艺术家获得不成比例、重复的投资来自少数收藏家”，表明 NFT 艺术市场的赞助可能比一般艺术市场的投机交易更稳定。"

Now next paragraph:

"In addition, the presented data does not include NFT art from traditional auction houses, like Sotheby's,⁸ Christie's,⁹ and Phillips,¹⁰ which have all recently begun trading digital art, especially the more pricey artworks."

Translate: "此外，所展示的数据未包括来自传统拍卖行的 NFT 艺术，例如 Sotheby's、⁸ Christie's、⁹ 和 Phillips、¹⁰，它们最近都开始交易数字艺术，尤其是更昂贵的作品。"

Need to keep superscripts.

Next: "Furthermore, NFT art transactions can be accomplished on a P2P basis between trusted individuals."

Translate: "此外，NFT 艺术交易可以在可信个人之间以点对点（P2P）方式完成。"

Next: "Outside observers can observe the transfer of NFTs, but it is impossible to determine the nature of these trades."

Translate: "外部观察者可以观察 NFT 的转移，但无法确定这些交易的性质。"

Next: "Therefore, the overall NFT art market might be larger than the volume of new art-focused NFT marketplaces suggests."

Translate: "因此，整体 NFT 艺术市场可能大于新兴的以艺术为导向的 NFT 市场的交易量。"

Next heading: "### 4.4.4 Price Dynamics" -> "### 4.4.4 价格动态"

Next paragraph:

"Understanding the determinants of price fluctuations in the market for NFT art is especially challenging given that it is new and, at least historically, has been heavily influenced by speculative investments and the presence of “whales,” or large NFT holders."

Translate: "理解 NFT 艺术市场中价格波动的决定因素尤其具有挑战性，因为它是新兴的，且在历史上主要受到投机投资和“鲸鱼”（即大额 NFT 持有者）的存在的影响。"

Next: "We apply insights from other asset markets and break down the price determinants into the following categories:"

Translate: "我们从其他资产市场汲取灵感，并将价格决定因素分为以下类别："

Now list items:

- **Artist’s Reputation:** Much like in the traditional art market, the reputation and popularity of the artist can play a significant role in the value of an NFT. Works by well-known and respected artists generally command higher prices.

Translate:

"**艺术家声誉:** 与传统艺术市场类似，艺术家的声誉和知名度在 NFT 的价值中起着重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。"

But need to keep colon after bold label. So:

- **艺术家声誉:** 与传统艺术市场类似，艺术家的声誉和知名度在 NFT 的价值中起着重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。

- **Scarcity:** The value of an NFT can increase if it is a rare or limited edition. This is a basic principle of supply and demand: prices tend to increase when supply is limited and demand is high. This concept also applies to NFT traits within one collection, resulting in NFTs with more scarce traits being more valuable than other NFTs from the same collection (see Mekacher et al., 2022).

Translate:

"**稀缺性:** NFT 的价值可以在它是罕见或限量版时增加。这是供需的基本原则：当供应有限且需求高时，价格倾向于上涨。该概念也适用于同一集合内的 NFT 特征，这使得拥有更稀缺特征的 NFT 比同一集合中的其他 NFT 更有价值（见 Mekacher et al., 2022）。"

- **Quality of the Artwork:** The artwork’s perceived aesthetic or conceptual quality can impact its price. However, this can be highly subjective and can change over time.

Translate:

"**艺术作品的质量:** 作品的感知美学或概念质量可以影响其价格。然而，这可能高度主观，并且会随时间而变化。"

- **Provenance:** The history and ownership of the NFT can affect its value. An NFT with a notable history or owned by a famous person could potentially command a higher price.

Translate:

"**来源:** NFT 的历史和所有权可以影响其价值。拥有显著历史或由知名人物拥有的 NFT 可能会获得更高的价格。"

- **Market Sentiment:** The NFT market, like the cryptocurrency market, is heavily influenced by market sentiment. Hype, media coverage, and celebrity endorsements can all significantly impact prices.

Translate:

"**市场情绪:** NFT 市场与加密货币市场一样，受市场情绪的强烈影响。炒作、媒体报道和名人效应都能显著影响价格。"

- **Utility:** Some NFTs come with additional benefits or utilities, such as exclusive access to events, physical goods, or additional digital content. These utilities can increase the value of the NFT.

Translate:

"**实用性:** 部分 NFT 附带额外的好处或实用功能，例如独家活动访问、实物商品或额外的数字内容。这些实用功能可以提升 NFT 的价值。"

Now next paragraph:

"The most comprehensive research to date on the price dynamics of NFTs is Bori et al.’s (2023) study, which collected a large-scale dataset of NFTs and broke down the determinants of the prices, finding that the time component explains 41 percent of the variation in log prices. While artist idiosyncratic factors explain the majority, momentum and timing in the market play a major role. Bori et al. (2023) reaffirm the role that rarity plays, which is consistent with Kong and Lin (2021) and Dobrynskaya and Bianchi (2023), but show that the relationship between rarity and price is particularly strong for those with a fixed supply."

Translate:

"到目前为止关于 NFT 价格动态的最全面研究是 Bori 等人 (2023) 的研究，他们收集了大规模的 NFT 数据集并分析了价格决定因素，发现时间因素解释了日志价格变化的 41%。虽然艺术家特有因素解释了大部分差异，但市场的动量和时机在其中发挥了重要作用。Bori 等人 (2023) 再次确认了稀缺性的作用，这与 Kong and Lin (2021) 与 Dobrynskaya and Bianchi (2023) 保持一致，但表明稀缺性与价格的关系在供应固定的情况下尤为强烈。"

Next: "Other studies examining the price dynamics of NFTs include Goetzmann and Nozari (2022), Nadini et al. (2021), and Kräussl and Tugnetti (2023)."

Translate:

"其他研究 NFT 价格动态的作品包括 Goetzmann 和 Nozari (2022)、Nadini 等人 (2021) 以及 Kräussl 和 Tugnetti (2023)。"

Next paragraph:

"Like stocks, cryptocurrencies, and other tradable assets, the value of NFTs can be influenced by broader market trends, economic indicators, and investor sentiment."

Translate:

"与股票、加密货币和其他可交易资产一样，NFT 的价值可以受到更广泛的市场趋势、经济指标和投资者情绪的影响。"

Next: "However, the NFT market also has unique characteristics that make it quite different from traditional asset markets."

Translate:

"然而，NFT 市场也具有使其与传统资产市场相当不同的独特特征。"

Now list items:

- **Volatility:** The NFT market has shown itself to be highly volatile, with prices that can rise and fall dramatically in a short period. This is partly because it is a relatively new market with a lot of speculative investing.

Translate:

"**波动性:** NFT 市场表现出高度波动性，价格在短时间内可以大幅上升或下降。这部分原因是该市场相对新颖，且充斥着大量投机投资。"

- **Illiquidity:** Unlike stocks and cryptocurrencies, which can usually be sold relatively quickly if there’s enough trading volume, NFTs can sometimes be harder to sell, especially those from unknown artists or collections.

Translate:

"**缺乏流动性:** 与股票和加密货币不同，后者在交易量足够时通常可以快速出售，NFT 有时难以出售，尤其是来自不知名艺术家或收藏的 NFT。"

- **Regulation:** The NFT market is less regulated than traditional financial markets. This has led some critics to argue that it can lead to increased risk, including the risk of fraud, although the traditional finance sector has also experienced substantial fraud and risk-taking.

Translate:

"**监管:** NFT 市场的监管程度低于传统金融市场。这导致一些批评者认为它可能增加风险，包括欺诈风险，尽管传统金融行业也经历了大量欺诈和风险行为。"

- **Decentralization:** NFTs are typically bought and sold on decentralized platforms, which can lead to additional complexities, including potential technical issues or vulnerabilities.

Translate:

"**去中心化:** NFT 通常在去中心化平台上买卖，这可能导致额外的复杂性，包括技术问题或漏洞。"

Next paragraph:

"As a result of illiquidity, transparency regarding high-value targets, and challenging (international) law enforcement, there is a potential risk for illicit behavior, such as elaborate scams, price manipulations, and money laundering."

Translate:

"由于缺乏流动性、对高价值目标的透明度以及跨国执法的困难，NFT 市场存在滥用行为的潜在风险，如复杂的诈骗、价格操纵和洗钱。"

Next: "Furthermore, Huang and Goetzmann (2023) highlight a behavioral phenomenon that can emerge where potential NFT buyers focus on a censored set of NFTs selling for high prices that influence their expectations on future returns – that is, investors focus their attention on high-ticket NFT sales during a bull market and extrapolate future price movements from the past."

Translate:

"此外，Huang 和 Goetzmann (2023) 指出一种行为现象，即潜在的 NFT 购买者会关注一组被审查的高价 NFT，这会影响他们对未来回报的预期——即投资者在牛市期间专注于高价 NFT 的销售，并据此推算未来的价格走势。"

Next: "However, once the NFT market began to collapse, these investors were slow to respond."

Translate:

"然而，当 NFT 市场开始崩溃时，这些投资者反应迟缓。"

Next: "These lead-lag relationships between trading" - incomplete. We'll translate as "这些交易的先后关系". But maybe need to keep as is: "These lead-lag relationships between trading". Since it's incomplete, maybe we need to translate the phrase "These lead-lag relationships between trading" as "这些交易的先后关系". We'll do that.

Next paragraph:

"No central agency currently enforces the return of stolen assets on public blockchains. Victims rely on the bad actor to return the NFTs. However, some marketplaces have established a system whereby stolen NFTs are flagged and sometimes even removed from their marketplace. Flagging stolen NFTs raises awareness to potential buyers not to purchase stolen NFTs. A registry might help to establish transparency and potentially hinder the distribution of stolen NFTs, for example, if protocols block interactions with stolen NFTs."

Translate:

"目前没有中央机构强制执行公共区块链上被盗资产的返还。受害者依赖恶意行为者归还 NFT。然而，一些市场已建立系统，在被盗 NFT 被标记并有时甚至从其市场中移除后，可以提高潜在买家对购买被盗 NFT 的警惕性。登记册可能有助于建立透明度，并可能阻碍被盗 NFT 的分发，例如，如果协议阻止与被盗 NFT 的交互。"

Next heading: "### 4.5.4 Money Laundering and Price Manipulations" -> "### 4.5.4 洗钱和价格操纵"

Next paragraph:

"As discussed, blockchains might make it harder to profit from stolen assets. However, money laundering and potential price manipulation schemes are harder to uncover, even in transparent settings."

Translate:

"如前所述，区块链可能使从被盗资产中获利变得更加困难。然而，洗钱和潜在的价格操纵方案即使在透明环境下也更难被发现。"

Next:

"In this regard, we deemed wash trading illegal for traditional asset settings (Liu et al., 2023) because it is often related to price manipulation and other illicit behaviors."

Translate:

"在这方面，我们认为传统资产环境下的洗钱行为是非法的（Liu et al., 2023），因为它通常与价格操纵和其他非法行为相关。"

Next:

"Capital controls, where capital holders have to prove the origin of the money, might help to restrict the influx of illegal money and increase the difficulty of money laundering."

Translate:

"资本管制，即持有者必须证明资金来源的措施，可能有助于限制非法资金的流入并增加洗钱的难度。"

Next:

"However, bad actors will find ways and means to circumvent these controls, like in any market setting."

Translate:

"然而，恶意行为者会想尽办法规避这些控制，就像在任何市场环境中一样。"

Next:

"Price manipulation schemes are equally hard to uncover and prove, especially since the NFT market is relatively illiquid."

Translate:

"价格操纵方案同样难以发现和证明，尤其是因为 NFT 市场相对缺乏流动性。"

Next:

"Thus, any trade has a higher likelihood of creating a price impact."

Translate:

"因此，任何交易都更有可能产生价格影响。"

Next:

"Regulators and law enforcement agencies should ensure that the same rules apply to all markets and settings, including the NFT market, which might include new rules for marketplaces regarding Know-Your-Customer (KYC) or Proof-of-Funds."

Translate:

"监管机构和执法机构应确保所有市场和环境（包括 NFT 市场）适用相同的规则，这可能包括为市场制定新的 Know-Your-Customer（KYC）或 Proof-of-Funds 规则。"

Now next heading: "## 4.6 CONCLUSION" -> "## 4.6 结论"

Next paragraph:

"The arts sector has been struggling for decades, and the sudden shock of the pandemic and the closure of arts institutions in 2020 led to an especially big blow to artists."

Translate:

"艺术行业已为数十年挣扎不已，2020 年疫情的突发冲击以及艺术机构的关闭给艺术家带来了尤其巨大的打击。"

Next:

"However, these headwinds converged with the popularization of distributed ledger technology, and blockchain natives and creatives began using art as one of its main and easiest-to-understand use cases."

Translate:

"然而，这些逆风与分布式账本技术的流行相结合，区块链原生和创作者开始将艺术作为其主要且最易理解的使用案例之一。"

Next:

"Art NFTs began to surge in 2020 and 2021, capturing the attention of major media headlines and generating significant trading fees for the new NFT exchanges."

Translate:

"艺术 NFT 在 2020 和 2021 年开始迅速增长，吸引了主要媒体标题的关注，并为新兴 NFT 交易所产生了大量交易费用。"

Next:

"This chapter has addressed three aspects of the art NFT market. First, we provided background on the formation of the NFT market in the arts with a focus on the factors that have created confusion and stifled growth due to the absence of legal clarity on ownership."

Translate:

"本章讨论了艺术 NFT 市场的三个方面。首先，我们提供了艺术领域 NFT 市场形成的背景，重点关注因缺乏法律对所有权的明确性而导致的混乱和阻碍增长的因素。"

Next:

"In particular, most NFTs never clarified what ownership of them conferred; rarely did ownership of the NFT confer ownership over the artwork."

Translate:

"特别是，大多数 NFT 从未明确其所有权所代表的内容；很少有 NFT 的所有权直接赋予对艺术品的所有权。"

Next:

"Furthermore, there is still little judicial precedent for the enforcement of NFT contracts. There is still growing interest and legal work underway to improve the standard for NFT contracts."

Translate:

"此外，关于 NFT 合同执行的司法先例仍然很少。目前仍有大量兴趣和法律工作在进行，以改进 NFT 合同的标准。"

Next:

"Second, we presented evidence on the rise of NFT trading, the phenomenon of wash trading – that is, fraudulent selling of NFTs often characterized by one user who held several wallets and traded an NFT to give the impression of activity and, thus, scarcity and value."

Translate:

"其次，我们提供了 NFT 交易增长的证据，以及洗钱现象——即通过持有多个钱包的用户进行欺诈性 NFT 销售，以营造活动和稀缺性的假象。"

Next:

"The NFT trading market exhibited enormous growth in 2021, but this has cooled off significantly since the end of 2022."

Translate:

"NFT 交易市场在 2021 年呈现出巨大的增长，但自 2022 年底以来已显著降温。"

Next:

"Yet, the often-postulated price and volume bubble seems to have been at least partially caused by wash trading activity."

Translate:

"然而，经常被假设的价格和交易量泡沫似乎至少部分是由洗钱活动引起的。"

Next:

"Furthermore, wash trading activity seemed to be related to or driven by competition between NFT exchanges or marketplaces; for example, users might have engaged in wash trading activities to farm incentives on various marketplaces."

Translate:

"此外，洗钱活动似乎与 NFT 交易所或市场之间的竞争有关或被驱动；例如，用户可能进行洗钱活动以在各种市场中获取激励。"

Next:

"Third, we provided a" - incomplete. We'll translate as "第三，我们提供了". Keep as is.

Now after that, there is image line again (same as earlier). Then source line, figure caption line, then "trading overall." etc. Wait we need to ensure we include those after the figure caption. Let's re-evaluate the ordering after "Third, we provided a". The original content after that includes:

`![](img/ab11be88faa3a9baf1bf1607f21e9805_116_0.png)`

`*Source: https://dune.com/hildobby/ethereum-nfts*`

`*Figure 4.6 SuperRare adoption by artists and collectors*`

`trading overall. This proposition is partially supported by Vasan et al. (2022), demonstrating that at the Foundation art marketplace, “successful artists receive disproportional, repeated investment from a small group of collectors,” indicating that patronage on NFT art marketplaces might be more stable than speculative trading on general art marketplaces.`

`In addition, the presented data does not include NFT art from traditional auction houses, like Sotheby's,⁸ Christie's,⁹ and Phillips,¹⁰ which have all recently begun trading digital art, especially the more pricey artworks. Furthermore, NFT art transactions can be accomplished on a P2P basis between trusted individuals. Outside observers can observe the transfer of NFTs, but it is impossible to determine the nature of these trades. Therefore, the overall NFT art market might be larger than the volume of new art-focused NFT marketplaces suggests.`

So we need to include those lines after the "Third, we provided a". So we need to translate "trading overall." as "整体交易". Then the rest as previously translated.

Now after that, we have the "### 4.4.4 Price Dynamics" heading and its content, which we already translated.

Now after that, we have list items etc., then "### 4.5.4 Money Laundering and Price Manipulations" heading and its content, which we translated.

Then "## 4.6 CONCLUSION" heading and its content, which we translated.

Now we need to ensure we wrap everything in [content]...[/content] exactly.

We must be careful not to miss any lines, and not to duplicate original text. Also ensure we keep line breaks as in original (maybe not necessary but we should preserve structure). The output should be a single block with [content] at start and [/content] at end.

Let's construct the final translation.

We'll start with the image line (unchanged). Then source line (translated). Then figure caption line (translated). Then "trading overall." (translated). Then the paragraph about Vasan et al. (translated). Then the paragraph about traditional auction houses (translated). Then the paragraph about P2P transactions (translated). Then the paragraph about observers (translated). Then the paragraph about overall market size (translated). Then heading "### 4.4.4 Price Dynamics" (translated). Then the paragraph about price determinants (translated). Then list items (translated). Then paragraph about Bori et al. (translated). Then paragraph about other studies (translated). Then paragraph about stocks etc. (translated). Then paragraph about unique characteristics (translated). Then list items about volatility, illiquidity, regulation, decentralization (translated). Then paragraph about illicit risk (translated). Then paragraph about Huang and Goetzmann (translated). Then paragraph about lead-lag relationships (translated). Then paragraph about no central agency (translated). Then heading "### 4.5.4 Money Laundering and Price Manipulations" (translated). Then paragraph about blockchains (translated). Then paragraph about wash trading (translated). Then paragraph about capital controls (translated). Then paragraph about bad actors (translated). Then paragraph about price manipulation (translated). Then paragraph about regulators (translated). Then heading "## 4.6 CONCLUSION" (translated). Then paragraph about arts sector (translated). Then paragraph about headwinds (translated). Then paragraph about art NFTs surge (translated). Then paragraph about chapter addressing three aspects (translated). Then "First," paragraph (translated). Then "In particular," paragraph (translated). Then "Furthermore," paragraph (translated). Then "Second," paragraph (translated). Then "The NFT trading market exhibited enormous growth..." (translated). Then "Yet, the often-postulated price and volume bubble..." (translated). Then "Furthermore, wash trading activity seemed to be related..." (translated). Then "Third, we provided a" (translated). Then image line (unchanged). Then source line (translated). Then figure caption line (translated). Then "trading overall." (translated). Then the Vasan paragraph again (we already have it earlier; but note that after figure caption there is "trading overall." which we already translated; then the Vasan paragraph is part of same block after figure caption. Actually the Vasan paragraph is after "trading overall." So we need to ensure we include that translation again (maybe we already included it earlier in the main body). Wait we need to check ordering: The figure caption line is after source line. Then "trading overall." is a separate line. Then the Vasan paragraph continues. So we need to translate "trading overall." as "整体交易". Then the Vasan paragraph translation as we did earlier. Then the paragraph about traditional auction houses. Then the P2P paragraph. Then observers paragraph. Then overall market size paragraph.

Thus we need to ensure we include all those lines in order.

Let's rewrite the entire translation in order, ensuring we keep line breaks.

I'll write the translation step by step, preserving line breaks.

Start:

[content]

![](img/ab11be88faa3a9baf1bf1607f21e9805_116_0.png)

*来源: https://dune.com/hildobby/ethereum-nfts*

*图 4.6 SuperRare 艺术家和收藏家的采用*

整体交易。这一命题部分得到 Vasan 等人 (2022) 的支持，表明在 Foundation 艺术市场，“成功艺术家获得不成比例、重复的投资来自少数收藏家”，表明 NFT 艺术市场的赞助可能比一般艺术市场的投机交易更稳定。

此外，所展示的数据未包括来自传统拍卖行的 NFT 艺术，例如 Sotheby's、⁸ Christie's、⁹ 和 Phillips、¹⁰，它们最近都开始交易数字艺术，尤其是更昂贵的作品。此外，NFT 艺术交易可以在可信个人之间以点对点（P2P）方式完成。外部观察者可以观察 NFT 的转移，但无法确定这些交易的性质。因此，整体 NFT 艺术市场可能大于新兴的以艺术为导向的 NFT 市场的交易量。

### 4.4.4 价格动态

理解 NFT 艺术市场中价格波动的决定因素尤其具有挑战性，因为它是新兴的，且在历史上主要受到投机投资和“鲸鱼”（即大额 NFT 持有者）的存在的影响。我们从其他资产市场汲取灵感，并将价格决定因素分为以下类别：

- **艺术家声誉:** 与传统艺术市场类似，艺术家的声誉和知名度在 NFT 的价值中起着重要作用。知名且受尊敬的艺术家的作品通常能够获得更高的价格。
- **稀缺性:** NFT 的价值可以在它是罕见或限量版时增加。这是供需的基本原则：当供应有限且需求高时，价格倾向于上涨。该概念也适用于同一集合内的 NFT 特征，这使得拥有更稀缺特征的 NFT 比同一集合中的其他 NFT 更有价值（见 Mekacher et al., 2022）。
- **艺术作品的质量:** 作品的感知美学或概念质量可以影响其价格。然而，这可能高度主观，并且会随时间而变化。
- **来源:** NFT 的历史和所有权可以影响其价值。拥有显著历史或由知名人物拥有的 NFT 可能会获得更高的价格。
- **市场情绪:** NFT 市场与加密货币市场一样，受市场情绪的强烈影响。炒作、媒体报道和名人效应都能显著影响价格。
- **实用性:** 部分 NFT 附带额外的好处或实用功能，例如独家活动访问、实物商品或额外的数字内容。这些实用功能可以提升 NFT 的价值。

到目前为止关于 NFT 价格动态的最全面研究是 Bori 等人 (2023) 的研究，他们收集了大规模的 NFT 数据集并分析了价格决定因素，发现时间因素解释了日志价格变化的 41%。虽然艺术家特有因素解释了大部分差异，但市场的动量和时机在其中发挥了重要作用。Bori 等人 (2023) 再次确认了稀缺性的作用，这与 Kong and Lin (2021) 与 Dobrynskaya and Bianchi (2023) 保持一致，但表明稀缺性与价格的关系在供应固定的情况下尤为强烈。其他研究 NFT 价格动态的作品包括 Goetzmann 和 Nozari (2022)、Nadini 等人 (2021) 以及 Kräussl 和 Tugnetti (2023)。

与股票、加密货币和其他可交易资产一样，NFT 的价值可以受到更广泛的市场趋势、经济指标和投资者情绪的影响。

然而，NFT 市场也具有使其与传统资产市场相当不同的独特特征：

- **波动性:** NFT 市场表现出高度波动性，价格在短时间内可以大幅上升或下降。这部分原因是该市场相对新颖，且充斥着大量投机投资。
- **缺乏流动性:** 与股票和加密货币不同，后者在交易量足够时通常可以快速出售，NFT 有时难以出售，尤其是来自不知名艺术家或收藏的 NFT。
- **监管:** NFT 市场的监管程度低于传统金融市场。这导致一些批评者认为它可能增加风险，包括欺诈风险，尽管传统金融行业也经历了大量欺诈和风险行为。
- **去中心化:** NFT 通常在去中心化平台上买卖，这可能导致额外的复杂性，包括技术问题或漏洞。

由于缺乏流动性、对高价值目标的透明度以及跨国执法的困难，NFT 市场存在滥用行为的潜在风险，如复杂的诈骗、价格操纵和洗钱。

此外，Huang 和 Goetzmann (2023) 指出一种行为现象，即潜在的 NFT 购买者会关注一组被审查的高价 NFT，这会影响他们对未来回报的预期——即投资者在牛市期间专注于高价 NFT 的销售，并据此推算未来的价格走势。然而，当 NFT 市场开始崩溃时，这些投资者反应迟缓。这些交易的先后关系

No central agency currently enforces the return of stolen assets on public blockchains. Victims rely on the bad actor to return the NFTs. However, some marketplaces have established a system whereby stolen NFTs are flagged and sometimes even removed from their marketplace. Flagging stolen NFTs raises awareness to potential buyers not to purchase stolen NFTs. A registry might help to establish transparency and potentially hinder the distribution of stolen NFTs, for example, if protocols block interactions with stolen NFTs.

### 4.5.4 洗钱和价格操纵

如前所述，区块链可能使从被盗资产中获利变得更加困难。然而，洗钱和潜在的价格操纵方案即使在透明环境下也更难被发现。

在这方面，我们认为传统资产环境下的洗钱行为是非法的（Liu et al., 2023），因为它通常与价格操纵和其他非法行为相关。

资本管制，即持有者必须证明资金来源的措施，可能有助于限制非法资金的流入并增加洗钱的难度。然而，恶意行为者会想尽办法规避这些控制，就像在任何市场环境中一样。

价格操纵方案同样难以发现和证明，尤其是因为 NFT 市场相对缺乏流动性。因此，任何交易都更有可能产生价格影响。监管机构和执法机构应确保所有市场和环境（包括 NFT 市场）适用相同的规则，这可能包括为市场制定新的 Know-Your-Customer（KYC）或 Proof-of-Funds 规则。

## 4.6 结论

艺术行业已为数十年挣扎不已，2020 年疫情的突发冲击以及艺术机构的关闭给艺术家带来了尤其巨大的打击。然而，这些逆风与分布式账本技术的流行相结合，区块链原生和创作者开始将艺术作为其主要且最易理解的使用案例之一。艺术 NFT 在 2020 和 2021 年开始迅速增长，吸引了主要媒体标题的关注，并为新兴 NFT 交易所产生了大量交易费用。

本章讨论了艺术 NFT 市场的三个方面。首先，我们提供了艺术领域 NFT 市场形成的背景，重点关注因缺乏法律对所有权的明确性而导致的混乱和阻碍增长的因素。特别是，大多数 NFT 从未明确其所有权所代表的内容；很少有 NFT 的所有权直接赋予对艺术品的所有权。此外，关于 NFT 合同执行的司法先例仍然很少。目前仍有大量兴趣和法律工作在进行，以改进 NFT 合同的标准。其次，我们提供了 NFT 交易增长的证据，以及洗钱现象——即通过持有多个钱包的用户进行欺诈性 NFT 销售，以营造活动和稀缺性的假象。NFT 交易市场在 2021 年呈现出巨大的增长，但自 2022 年底以来已显著降温。然而，经常被假设的价格和交易量泡沫似乎至少部分是由洗钱活动引起的。此外，洗钱活动似乎与 NFT 交易所或市场之间的竞争有关或被驱动；例如，用户可能进行洗钱活动以在各种市场中获取激励。第三，我们提供了

