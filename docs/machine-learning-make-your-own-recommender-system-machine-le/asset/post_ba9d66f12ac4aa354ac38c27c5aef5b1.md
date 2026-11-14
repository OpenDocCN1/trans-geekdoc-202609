
Potter or Star War series, are redundant. This problem is exacerbated if closely related items—such as those of the same series—are displayed in another tab adjacent to the recommended items section. If users become accustomed to seeing the same popular and obvious recommendations in their sidebar, they will gradually lose interest. An element of serendipity is a major advantage of recommender systems. Therefore, a slightly lower correlation between items might provide more effective recommendations and a higher conversion rate.

The effectiveness of recommendations also varies by use case and how recommendations are displayed. Highly correlated item recommendations may perform poorly on the home page but enjoy a higher conversion rate when placed deeper into the website. A key goal of recommender systems is item discovery, and it may take several instances of exposure before the user is ready to purchase or complete a target conversion action. This is why some Internet companies follow a policy of cycling recommendations to users three or more times before determining whether the suggested item is a poor match.

Thus, while the training and test data split is convenient for evaluating a user’s rating patterns, it does little to assess how users will react to a recommendation in the real world and does not consider factors outside the model’s testing space.

The interpretation of the results can also differ by organization. Monetized blogs that generate revenue based on page views and ad impressions may not be affected by a high exit rate from recommended content. Alternatively, businesses that focus on content marketing to build rapport with customers and improve their search engine rankings might not be satisfied with a recommender system that leads to a shallow level of user engagement.

Most exponents of recommender systems, therefore, evaluate model performance based on customized user actions rather than split validation. One method is user studies, which involves observing how users interact with recommender systems via online screen recordings or experimental trials. Meanwhile, more large-scale evaluation can be performed with the aid of A/B testing.

## A/B Testing

In A/B testing, two prediction models randomly alternate between users so comparisons can be formed from the results of Group A and Group B. Users in Group A might be fed collaborative-based filtering recommendations, while users in Group B might be exposed to content-based recommendations.

A/B tests typically require a thousand or more users to accurately assess the performance of one recommender system model over another. The performance of the systems can be evaluated based on numerous metrics. A primary metric is analyzing the click-through rate of items recommended to the user (usually displayed inside the website’s sidebar or below a post). Recommended items that generate a high-click rate are looked upon favorably. A/B testing can also be implemented on the design and labeling of recommended items. A/B tests, however, should only test one variable at a time.

To ensure that the model is effective at maximizing user engagement, A/B testing may also need to factor in the time-on-page or the exit rate of users who click through to a recommended item. If a user immediately exits after arriving on the page of a recommended item, this is not considered a positive result.

A/B testing, itself, can be performed in a variety of ways and there are numerous SaaS (software-as-a-service) options available, including Optimizely and VWO.

The advantages of A/B testing over user studies are scalability and relevance. Through automation, A/B testing can be scaled out to thousands or even millions of users, albeit at some extra cost. Secondly, A/B test results are highly relevant as they capture genuine interactions between the end-user and the recommended item(s). Users are generally impervious to the fact that a website is conducting live A/B testing and aren’t coerced to select a recommended item as they might in a user study.

## Top-N Qualities

Most recommender systems today serve not just one recommendation but a list of items to recommend, called a “top-N” list. “N” refers to the number of items displayed to the user as recommendations. At the time of writing, Audible.com recommends 24 items on its homepage whereas Amazon recommends 10.

Using a top-N list as a unit of analysis, we can assess the recommendations based on a number of qualities including hit rate, average reciprocal hit rate, and diversity.

The hit rate, for example, recognizes items in the top-N list that the user has rated in the past and is divided by the number of items in the list. While hits might not lead to user conversion (as the user has already rated and consumed the item), their presence is a good indicator that the recommender system understands the user’s tastes. In addition, adding a few hits to an N-list helps to instill an element of trust. If you present a list of unfamiliar items the user has never seen before, they might not trust your platform’s ability to recommend items and understand their personal preferences. Conversely, one or two familiar items might attract the user’s attention and prompt them to explore other items in the list.

Another variation of the hit rate method is the average reciprocal hit rate (ARHR), which is a weighting system that takes into account the item’s placing in the top-N list. This in effect rewards items listed prominently in the first few places of a top-N list, where there’s higher visibility, and penalizes familiar items low in the N-list.

Next is diversity, which is a measure of variety in your N-list. Rather than focus exclusively on predictable items like other videos from the same YouTube account, diversity incentivizes variation across items—usually based on content characteristics (i.e. genre, creator, etc). Diversity can be measured using a number of metrics including Intra-List Similarity (ILS), cosine similarity, and Jaccard similarity coefficient between pairs of items. Note, however, that this method can be expensive to run and there’s no guarantee that diversity will improve user conversion.

## User Studies

While user studies are more difficult to scale and they generate results in a contrived environment, they help to generate valuable qualitative insights. Rather than solely looking at the numbers—as is the case with A/B testing —user studies may elicit ideas and feedback to optimize the recommender system and its interface.

For instance, feedback might comprise suggestions that the recommended items were too similar to items the user had already purchased or consumed in the past. Rather than being recommended a near-identical item, the user perhaps prefers some variety in their recommendations. Users might also offer feedback that they prefer not to watch back-to-back-to-back videos of cats swinging around the room on a fan because it makes them feel nauseous and the entertainment factor has a diminishing rate of return. Instead, they’d prefer to switch up their viewing activity with tips on cat grooming and highlights of cats performing other spectacular feats. User studies can also help provide specific feedback on the visual design and labeling of recommender systems.

While it’s risky to redo your entire recommender system based on qualitative feedback from a small number of users, user study suggestions can be tested and validated using A/B testing. A combination of user studies and A/B testing is indeed an ideal evaluation strategy.

Lastly, qualitative feedback can be valuable at highlighting aspects overlooked in an A/B test. Speaking on the re-installment of Netflix’s online subscriber profile feature, former Chief Product Officer, Neil Hunt, told CNNMoney, "focus-group testing showed that profiles generate more viewing and more engagement."

The subscriber profile feature allows a single paid subscriber account to manage multiple individual users (e.g., husband and wife, two roommates) with separate user features including ratings and friend lists to produce tailored recommendations.

"Listening to our members, we realized that users of this feature often describe it as an essential part of their Netflix experience," explained Hunt.

This particular example underlines the importance of qualitative feedback in a quantitative-centric era of doing business.

In conclusion, when it comes to recommender systems, evaluation can be messy. Also, the more you look at the results post-implementation, the more feedback and suggestions for optimization you will find. Recommender systems, therefore sit on the edge of machine learning and their own specialized subfield. They employ the same algorithms and self-learning techniques as other machine learning applications but rely on their own methods of evaluation outside of split validation and other traditional performance metrics.

The complexity of recommender model evaluation also means that there are ample jobs, prize money, and engaging work for those looking to build their career in this breakaway subfield of machine learning.
