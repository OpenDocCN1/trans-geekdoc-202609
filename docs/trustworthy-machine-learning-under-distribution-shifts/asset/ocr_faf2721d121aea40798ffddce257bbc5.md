# TABLE 6.3. Cross-modal retrieval performance of comparison methods across multiple datasets with different OOM modalities.

| Setting | IM | Method | MSR-VTT | | | | MOSEI | | | |
|---|---|---| | | | | | | | |
| | | | R@1 | R@5 | R@1 | R@5 | R@1 | R@5 | R@1 | R@5 |
| Semi-Supervised | ImageBind | Random | 5.4 | 25.1 | 25.4 | 5.4 | 24.2 | 14.3 | 42.5 | 14.4 | 42.8 | 14.1 | 42.1 |
| | | ERM | 15.6 | 30.3 | 35.2 | 18.5 | 28.2 | 25.5 | 49.3 | 47.1 | 33.4 | 48.2 |
| | | EnM | 18.5 | 32.4 | 39.2 | 21.0 | 39.4 | 29.6 | 46.7 | 33.5 | 50.4 | 50.5 |
| | | MoCo | 20.5 | 33.9 | 38.9 | 23.4 | 43.5 | 30.1 | 47.3 | 52.7 | 56.2 | 51.0 |
| | | COX | 26.9 | 39.9 | 44.3 | 28.7 | 48.0 | 36.2 | 53.8 | 59.8 | 64.2 | 66.4 |
| | | Aligned | 35.5 | 31.5 | 52.4 | 35.6 | 61.8 | 42.9 | 66.4 | 70.0 | 69.5 | 71.7 |
| | LanguageBind | Random | 5.2 | 24.3 | 25.4 | 5.0 | 25.6 | 13.5 | 41.3 | 42.7 | 14.6 | 41.9 |
| | | ERM | 16.3 | 31.5 | 36.2 | 18.7 | 37.8 | 25.7 | 48.4 | 47.6 | 33.4 | 49.3 |
| | | EnM | 19.8 | 32.4 | 39.6 | 25.8 | 37.9 | 30.2 | 45.5 | 53.5 | 56.1 | 49.7 |
| | | MoCo | 23.9 | 36.0 | 41.9 | 32.5 | 43.5 | 35.0 | 50.3 | 56.0 | 51.7 | 51.7 |
| | | COX | 25.2 | 36.0 | 44.0 | 28.7 | 48.7 | 39.6 | 49.4 | 54.8 | 59.2 | 55.4 |
| | | Aligned | 42.0 | 53.6 | 58.8 | 48.6 | 70.0 | 44.4 | 68.9 | 69.5 | 67.1 | 68.3 |
| Unsupervised | ImageBind | Random | 5.4 | 25.1 | 25.0 | 5.4 | 24.2 | 14.3 | 42.5 | 14.4 | 42.1 | 42.1 |
| | | SSL | 8.9 | 28.4 | 28.5 | 11.0 | 29.1 | 17.4 | 48.8 | 15.2 | 16.9 | 45.0 |
| | | MoCo | 9.2 | 30.9 | 36.0 | 21.1 | 32.9 | 25.1 | 50.7 | 57.8 | 51.5 | 54.4 |
| | | COX | 13.5 | 36.0 | 46.5 | 32.4 | 34.8 | 20.8 | 53.7 | 18.7 | 46.7 | 18.2 | 48.9 |
| | LanguageBind | Aligned | 35.5 | 51.5 | 52.3 | 38.6 | 58.8 | 44.2 | 66.4 | 68.9 | 69.4 | 70.1 |

OOM testing, which justifica that leveraging the knowledge from IM peers can help OOM generalization by using OOM data alone. Even though the performance is relatively limited compared to the fully pre-trained baseline under the unsupervised case, it is an extremely challenging setting, we can still largely improve the performance for over 10% compared to the Random baseline, which demonstrates that the unsupervised OOM generalization is indeed learnable leads to a novel research direction for improving the generalization performance. Additionally, note that the performance of COX is affected by the quality of IM posters, as LanguageBind would show relatively higher performance compared to ImageBind. This might be helpful to leverage sophisticated IM peers to benefit the generalization performance.