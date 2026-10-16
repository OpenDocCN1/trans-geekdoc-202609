```
# lift
# replace divide by zero with 1.0
ax2.plot(xs, realpct_myorder / np.where(xs > 0, xs, 1))

ax2.set_title("Lift Versus Random")
ax2.set_ylabel("X-Fold Improvement") # not cross-fold!
ax2.set_xlabel("Percent Of Population\n" +
    "Starting with Highest Predicted Hits")
ax2.yaxis.tick_right()
ax2.yaxis.set_label_position('right');
```

![](bbox=[0.17, 0.38, 0.47, 0.7])

![](bbox=[0.51, 0.38, 0.85, 0.7])

First, let's discuss the Cumulative Response curve. The y-axis is effectively our true positive rate: how well we are doing with respect to reality. The x-axis is a bit more complicated to read. At a given point on the x-axis, we are targeting the “predicted best” x% of the population and asking how well we did. For example, we can see that when we are allowed to use the first 40% of the population (our top 40% predictions), we get 100% of the hits. That can represent a tremendous real-world savings.

Imagine that we are running a fundraising campaign and sending letters to potential donors. Some recipients will read our letter and throw it in the trash. Others will read our letter and respond with a sizable and appreciated check or PayPal donation. If our mailing had a predictive model as good as our model here, we could save quite a bit on postage stamps. Instead of spending $10,000.00 on postage for everyone, we could spend $4,000.00 and target just that predicted-best 40%. If the model is really that good, we’d still hit all of our target donors who would contribute.

The Lift Versus Random curve—sometimes called a lift curve or a gain curve—simply divides the performance of our smart classifier against the performance of a baseline random classifier. You can think of it as taking a vertical slice up and down from the Cumulative Response graph, grabbing the red-dot value, and dividing it by the blue-line value. It is reassuring to see that when we start out, we are doing far better than random. As we bring in more of the population— we commit to spending more on postage—it