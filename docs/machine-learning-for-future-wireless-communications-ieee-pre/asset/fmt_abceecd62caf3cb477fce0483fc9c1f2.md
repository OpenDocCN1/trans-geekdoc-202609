
14. W. Jiang and T. Kaiser. From OFDM to FBMC: Principles and Comparisons. In F.L. Luo and C. Zhang, editors, Signal Processing for 5G: Algorithms and Implementations, chapter 3. John Wiley & Sons, United Kindom, 2016.

15. W. Jiang and H.D. Schotten. Multi‐antenna fading channel prediction empowered by artificial intelligence. *Proceedings of IEEE Vehicular Tech. Conf. (VTC)*, 2018a.

16. W. Jiang and H.D. Schotten. Neural network‐based channel prediction and its performance in multi‐antenna systems. *Proceedings of IEEE Vehicular Tech. Conf. (VTC)*, 2018b.

17. W. Jiang and H.D. Schotten. A comparison of wireless channel predictors: Artificial intelligence versus Kalman filter. *Proceedings of IEEE Intl. Commu. Conf. (ICC)*, 2019a.

18. W. Jiang and H.D. Schotten. Recurrent neural network‐based frequency‐domain channel prediction for wideband communications. *Proceedings of IEEE Vehicular Tech. Conf. (VTC)*, 2019b.

19. W. Jiang, T. Kaiser, and A.J.H. Vinck. A robust opportunistic relaying strategy for co‐operative wireless communications. IEEE Transactions on Wireless Communications, 15: 2642–2655, 2016.

20. W. Jiang, M. Strufe, and H.D. Schotten. Experimental results for artificial intelligence‐based self‐organized 5G networks. *Proceedings of IEEE PIMRC*, 2017.

21. Y. Jing and H. Jafarkhani. Network beamforming using relays with perfect channel information. IEEE Transactions on Information Theory, 55: 2499–2517, 2009.

22. J. Kim et al. Cooperative distributed beamforming with outdated CSI and channel estimation errors. IEEE Transactions on Communications, 62: 4269–4280, 2014.

23. J.N. Laneman and G.W. Wornell. Distributed space‐time‐coded protocols for exploiting cooperative diversity in wireless networks. IEEE Transactions on Information Theory, 49: 2415–2425, 2003.

24. R. Liao et al. The Rayleigh fading channel prediction via deep learning. Wireless Communications and Mobile Computing, 2018, 2018.

25. W. Liu et al. Recurrent neural network based narrowband channel prediction. *Proceedings of IEEE VTC*, 2006.

26. D.J. Love et al. An overview of limited feedback in wireless communication systems. IEEE Journal on Selected Areas in Communications, 26: 1341–1365, 2008.

27. O. Nerrand et al. Training recurrent neural networks: why and how? an illustration in dynamical process modeling. IEEE Transactions on Neural Networks, 5: 178–184, 1994.

28. E.N. Onggosanusi et al. Performance analysis of closed‐loop transmit diversity in the presence of feedback delay. IEEE Transactions on Communications, 49: 1618–1630, 2001.

29. A.V. Oppenheim and R.W. Schafer. Digital Signal Processing. Prentice‐Hall, first edition, 1975.

30. W. Peng et al. Channel prediction in time‐varying Massive MIMO environments. IEEE Access, 5: 23938–23946, 2017.

31. C. Potter et al. MIMO beam‐forming with neural network channel prediction trained by a novel PSO‐EA‐DEPSO algorithm. *Proceedings of IEEE IJCNN*, 2008.

32. D.J. Ramirez et al. Coordinated multi‐point transmission with imperfect CSI and other‐cell interference. IEEE Transactions on Wireless Communications, 14: 1882–1896, 2014.

33. T.R. Ramya and S. Bhashyam. Using delayed feedback for antenna selection in MIMO systems. IEEE Transactions on Wireless Communications, 8: 6059–6067, 2009.

34. A. Sendonaris et al. User cooperation diversity‐Part I and II. IEEE Transactions on Communications, 51: 1927–1948, 2003.

35. D. Silver et al. Mastering the game of Go with deep neural networks and tree search. Nature, 529: 484–489, 2016.

36. Y. Teng et al. Effect of outdated CSI on handover decisions in dense networks. IEEE Communications Letters, 21: 2238–2241, 2017.

37. K.T. Truong and R. W. Heath. Effects of channel aging in massive MIMO systems. Journal of Communications and Networks, 15: 338–351, 2013.

38. D. Tse and P. Viswanath. Fundamentals of Wireless Communication. Cambridge Univ. Press, Cambridge, UK, 2005.

39. J.L. Vicario et al. Opportunistic relay selection with outdated CSI: outage probability and diversity analysis. IEEE Transactions on Wireless Communications, 8: 2872–2876, 2009.

40. Q. Wang et al. Multi‐user and single‐user throughputs for downlink MIMO channels with outdated channel state information. IEEE Wireless Communications Letters, 3: 321–324, 2014a.

41. Z. Wang et al. Resource allocation in OFDMA networks with imperfect channel state information. IEEE Communications Letters, 18: 1611–1614, 2014b.

42. J. Wu and W. Lee. Optimal linear channel prediction for LTE‐A uplink under channel estimation errors. IEEE Transactions on Vehicular Technology, 62: 4135–4142, 2013.

43. L. Xiao and X. Dong. Unified analysis of generalized selection combining with normalized threshold test per branch. IEEE Transactions on Wireless Communications, 5: 2153–2163, 2006.

44. X. Yu et al. Unified performance analysis of transmit antenna selection with OSTBC and imperfect CSI over Nakagami‐m fading channels. IEEE Transactions on Vehicular Technology, 67: 494–508, 2017.

45. H. Zhang and R.U. Nabar. Transmit antenna selection in MIMO‐OFDM systems: Bulk versus per‐tone selection. *Proceedings of IEEE Intl. Conf. on Commu. (ICC)*, 2008.

46. J. Zheng and B.D. Rao. Capacity analysis of MIMO systems using limited feedback transmit precoding schemes. IEEE Transactions on Signal Processing, 56: 2886–2901, 2008.

# Part III Network Intelligence and Adaptive System Optimization

## 17 Machine Learning for Digital Front-End: a Comprehensive Overview

*Pere L. Gilabert¹, David López‐Bueno², Thi Quynh Anh Pham¹, and Gabriel Montoro¹*

¹*Dept. of Signal Theory and Communications, UPC‐Barcelona Tech., Castelldefels, Barcelona, Spain*

²*CTTC/CERCA & Dept. of Signal Theory and Communications, UPC‐Barcelona Tech., Castelldefels, Barcelona, Spain*

### 17.1 Motivation and Background

In wireless and wired communications, the power amplifier (PA) is a critical subsystem in the transmitter chain – not only because it is one of the most power‐hungry devices and accounts for most of the direct current (DC) power consumed in macro base stations, but also because it is the main source of nonlinear distortion in the transmitter. Amplitude‐ and phase‐modulated communication signals presenting a high peak‐to‐average power ratio (PAPR) have a negative impact on the transmitter's power efficiency, because the PA has to be operated at high power back‐off levels to avoid introducing nonlinear distortion. As shown in [Figure 17.1](#c17.xhtml#c17-fig-0001), to prevent the peaks of the signal from going into compression, it is necessary to operate far from saturation, where the PA is more efficient. Consequently, the mean power added efficiency (PAE) is low, mainly in linear but inefficient class‐A or class‐AB PAs.
