Not all behaviours require a threat analysis, so to save CPU processing, threats are not assessed for behaviours that do not use the information.

The following behaviours required threats and are a subset of those required for the whole game. They do, however, show how different behaviours can use different combinations of the same filters to assess the threats in a way that suits the behaviour the player is currently enacting.

# 8.3.2.1 Zone Coverage Behaviour

When in zone coverage, a player is on the defensive side of the field and must keep track of opposing players looking to find a good position to catch the ball. They should also be aware of the ball carrier entering their zone, which would result in this behaviour being replaced with a simple behaviour that chases down the ball carrier and makes a tackle.

The threat filters assessed for this behaviour are:

+   - The opponent is the ball carrier filter.
+   - Opponent positioning inside zone filter.
+   - Distance of the opponent to the endzone filter.
+   - Opponent is currently man-marked filter.
+   - Distance of the opponent to the observing player filter.

# 8.3.2.2 Lead Blocker Behaviour

A Lead Blocker is a player on the offensive side of the field who runs ahead of the ball carrier and blocks off any incoming threats.

The threat filters assessed are:

+   - Distance of the opponent to the ball carrier filter.
+   - Distance of the opponent to the observing player filter.
+   - Opponent is currently man-marked filter.

# 8.3.2.3 Ball Carrier Behaviour

When any player on the field gets the ball, they have one job and that is to take it as many yards upheld as they can before an opposing player brings them down.

The filter required to assess threats for this behaviour is:

+   - Distance of the opponent to the observing player filter.

# 8.4 CONCLUSION

Awareness is a simple enough addition to any sports title and delivers great results. It does not remove the need for other stats such as sprint speed, it only enhances them. When it comes time to incorporate difficulty settings into your game, which always seems to be late in development, modifying the awareness stat or the threat weightings is a subtle way of adjusting the difficulty of your game without any of the AI players doing anything wrong.