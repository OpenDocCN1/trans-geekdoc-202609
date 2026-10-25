individual—that is, the model inputs—and receiving in return the predictive score for that individual.

I didn't have it so easy. Since I'd programmed the modeling method from scratch, I had no industrialized tool. To make matters worse, I wasn't an engineer. Although I'd been programming since I was ten, I'd never pursued a career in it. As an academic-turned-analytics consultant, I knew what needed to be done conceptually, but I was in no position to personally translate my models into production-ready code and integrate that code into an operational system.

So, I spelled it out for them. In a dense, three-page, single-spaced Word document entitled “Scoring Module Requirements,” I wrote down every single detail the engineers needed, every step they would need to code in order to use the models to predict responses to ads. For a given user and a given ad, it described how their code should look up a bunch of values within a table I’d created—the table had about 50,000 rows of values that constituted the 291 models—and then apply the right arithmetic. The document ended like this:

> Finally, after calculating the relative probabilities of a response (p1) and of no response (p0), normalize the two with the formula p1/(p0 + p1). This is the absolute probability of a response, that is, the score output by the model.

Given the characteristics of an individual that make up the inputs to a model, calculating the score isn't all that complex—especially with the simple kind of model I’d used for EduPay, Naive Bayes. But pulling together those inputs on the fly is a whole ‘nother ball game.

# The Data Disconnect: Getting the Inputs to a Deployed Model

> Getting the data right and having it in the right place at the right time is 80–90 percent of the problem.
> 
> —Scott Zoldi, chief analytics officer, FICO

If the struggle to deploy predictive models is a battle, then the challenge of hooking up its inputs is right at the frontlines. Somehow, a deployed model must receive the right set of values each time the