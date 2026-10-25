# # Ensemble algorithms

> > You know me, I think there ought to be a big old tree right there.
> > And let's give him a friend. Everybody needs a friend.
> >
> > Bob Ross

This chapter serves as a basic introduction to *ensembles*; specifically, ensembles of decision trees, although the ensemble methods discussed in this chapter are general algorithms that can also be applied to non-tree-based methods. The idea of ensemble modeling is to combine many models together in an attempt to increase overall prediction accuracy. As we'll see in this chapter, how the individual models are created and combined differs between the various ensembling techniques.

Have you ever watched the show *Who Wants to be a Millionaire*? If not, the game is very simple. A contestant is asked a series of multiple choice questions (each with four choices) of increasing difficulty, with a top prize of $1,000,000. The contestant is allowed to use three “lifelines,” a form of assistance to help the contestant with difficult questions. Over the years, a number of different lifelines were made available (e.g., the contestant could choose to randomly eliminate two of the incorrect answers). One of the most useful lifelines (IMO) involved polling the audience. If the contestant chose this lifeline, each audience member was able to use a device to cast their vote as to what they thought was the correct answer. The proportion of votes for each multiple choice answer was displayed to the contestant who could then choose to go with the popular vote or not. This lifeline was notorious for its accuracy; according to some sources, Regis Philbin (one of the hosts) once stated that the audience is right 95% of the time!

So why was polling the audience so accurate? As it turns out, this phenomenon has been observed for centuries and is often referred to as *the wisdom of the crowd*. In particular, it is often the case that the aggregated answers from a