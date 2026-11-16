
Table E.6.49: We list the detailed results for all the experiments of action masking and input representation. Results show the average number of steps required for all successful episodes and standard deviation with respect to the random seeds. In brackets, we show the overall percentage of successful episodes. In the summary row, the last number in brackets denotes the total number of puzzles where a solution below the upper bound of optimal steps was found. Entries without values mean that no successful policy was found among all random seeds.

| Puzzle | Suggested Parameters | Optimal | Random | PPO (Internal State) | PPO (RGB Pixels) | MaskablePPO (Internal State) | MaskablePPO (RGB Pixels) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Blockade | v2v32 | 144 | 2296 (0%) | 1772 ± 472 (4.9%) | 1620 ± 292 (6.0%) | 9 ± 0 (99.7%) | 304 ± 4 (99.4%) |
| Bowling | r4v2 | 51 | 1458 (88.5%) | 441 ± 204 (99.2%) | 133 ± 99 (99.7%) | 8 ± 0 (99.8%) | 41 ± 17 (75.1%) |
| Breakout | c2v2 | 54 | 1483 (98.2%) | 744 ± 410 (77.8%) | 509 ± 342 (80.7%) | 15 ± 0 (92.1%) | 419 ± 137 (51.7%) |
| Capture | v2v2 | 202 | 446 (0.0%) | 416 ± 61 (0.2%) | 311 ± 78 (0.0%) | 43 ± 14 (0.1%) | 20 ± 6 (0.0%) |
| Chase | v2v2 | 296 | 1000 (100%) | 8 ± 0 (100.0%) | 11 ± 0 (100.0%) | 4 ± 0 (100%) | 4 ± 0 (100%) |
| Climber | r4v4 | 284 | 1000 (0.0%) | 978 ± 99 (0.0%) | 971 ± 88 (0.0%) | 717 ± 142 (0.3%) | 919 ± 136 (0.1%) |
| CoinRun | v2v2 | 61 | 1318 (98.0%) | 8000 ± 1847 (0.1%) | 8338 ± 393 (0.2%) | 477 ± 142 (0.1%) | 1919 ± 836 (0.1%) |
| Dodgeball | v2v2 | 202 | 446 (0.0%) | 1000 (0.0%) | 497 ± 61 (0.0%) | 462 ± 56 (0.0%) | 128 ± 33 (0.0%) |
| FruitBot | r4v4 | 156 | 1000 (36.0%) | 8600 ± 779 (16.8%) | 8720 ± 812 (15.3%) | 2462 ± 250 (61.3%) | 5928 ± 1467 (40.5%) |
| Heist | v2v2 | 284 | 446 (0.0%) | 22 ± 0 (100%) | 22 ± 0 (100%) | 10 ± 0 (100%) | 10 ± 0 (100%) |
| Jumper | v2v2 | 192 | 446 (0.0%) | 889 ± 299 (0.0%) | 803 ± 44 (0.0%) | 111 ± 11 (0.0%) | 111 ± 11 (0.0%) |
| Leaper | v2v2 | 51 | 2237 (89.1%) | 1228 ± 113 (87.8%) | 2304 ± 188 (87.5%) | 25 ± 8 (99.1%) | 1608 ± 1144 (60.1%) |
| Maze | v2v2 | 72 | 1000 (99.7%) | 1968 ± 1089 (99.2%) | 1794 ± 1190 (99.7%) | 222 ± 18 (98.4%) | 402 ± 66 (42.4%) |
| Miner | v2v2 | 296 | 1446 (0.0%) | 1000 (0.0%) | 471 ± 284 (0.0%) | 173 ± 52 (0.0%) | 291 ± 185 (0.0%) |
| Ninja | v2v2 | 114 | 446 (1.3%) | 228 ± 92 (19.0%) | 250 ± 206 (4.4%) | 212 ± 238 (4.3%) | 671 ± 396 (43.1%) |
| Plunder | v2v2 | 284 | 446 (0.0%) | 924 ± 164 (0.0%) | 886 ± 194 (0.0%) | 10 ± 0 (100%) | 10 ± 0 (100%) |
| Starpilot | v2v2 | 284 | 1000 (100%) | 1000 (100%) | 1000 (100%) | 1000 (100%) | 1000 (100%) |
| BossFight | r4v4 | 192 | 446 (0.0%) | 442 ± 140 (0.0%) | 412 ± 121 (0.0%) | 79 ± 30 (99.6%) | 347 ± 136 (49.7%) |
| CaveFlyer | v2v2 | 192 | 446 (0.0%) | 474 ± 102 (0.0%) | 298 ± 73 (0.0%) | 214 ± 38 (0.0%) | 136 ± 34 (0.0%) |
| Chaser | v2v2 | 192 | 446 (0.0%) | 70 ± 300 (55.4%) | 514 ± 235 (10.0%) | 738 ± 328 (0.0%) | 1409 ± 387 (17.7%) |
| Summary | . | 217 | 1784 (71.7%) | 1604 ± 961 (43.0%) | 1078 ± 380 (58.7%) | 814 ± 428 (72.3%) | 1007 ± 503 (79.1%) |

## E.6.4 Episode Length and Early Termination Parameters

In Table E.6.50, the puzzles and parameters used for training the agents for the ablation in Section 8.4.4 are shown in combination with the results. Due to limited computational budget, we included only a subset of all puzzles at the easy human difficulty preset for DreamerV3. Namely, we have selected all puzzles where a random policy was able to complete at least a single episode successfully within 10,000 steps in 1000 evaluations. It contains a subset of the more challenging puzzles, as can be seen by the performance of many algorithms in Table E.6.47. For some puzzles, e.g. NetSlide, Samegame, Sixteen and Untangle, terminating episodes early brings a benefit in final evaluation performance when using a large maximal episode length during training. For the smaller maximal episode length, the difference is not always as pronounced.

Table E.6.50: Listed below are the puzzles and their corresponding supplied parameters. For each setting, we report the average success episode length with standard deviation with respect to the random seed, all averaged over all selected puzzles. In brackets, the percentage of successful episodes is reported. # Steps stands for the maximal episode length, ET stands for early termination after a given number of state repeats.

| Puzzle | Supplied Parameters | # Steps | ET | DreamerV3 |
| --- | --- | --- | --- | --- |
| Bridges | 7x7I30e10m2d0 | 1e4 | 10 | 4183.0 ± 2140.5 (0.2%) |
| | | 1e4 | - | - |
| | | 1e5 | 10 | 4017.9 ± 1390.1 (0.3%) |
| | | 1e5 | - | 4396.2 ± 2517.2 (0.3%) |
| Cube | c4x4 | 1e4 | 10 | 21.9 ± 1.4 (100.0%) |
| | | 1e4 | - | 21.4 ± 0.9 (100.0%) |
| | | 1e5 | 10 | 22.6 ± 2.0 (100.0%) |
| | | 1e5 | - | 21.3 ± 1.2 (100.0%) |
| Flood | 12x12c6m5 | 1e4 | 10 | - |
| | | 1e4 | - | - |
| | | 1e5 | 10 | - |
| | | 1e5 | - | - |
| Guess | c6p4g10Bm | 1e4 | 10 | - |
| | | 1e4 | - | 1060.4 ± 851.3 (0.6%) |
| | | 1e5 | 10 | 2405.5 ± 2476.4 (0.5%) |
| | | 1e5 | - | 3165.2 ± 1386.8 (0.6%) |
| Netslide | 3x3b1 | 1e4 | 10 | 3820.3 ± 681.0 (18.4%) |
| | | 1e4 | - | 3181.3 ± 485.5 (21.1%) |
| | | 1e5 | 10 | 3624.9 ± 746.5 (23.0%) |
| | | 1e5 | - | 4050.6 ± 505.5 (10.6%) |
| Samegame | 5x5c3s2 | 1e4 | 10 | 53.8 ± 7.5 (38.3%) |
| | | 1e4 | - | 717.4 ± 309.0 (29.1%) |
| | | 1e5 | 10 | 47.3 ± 6.6 (36.7%) |
| | | 1e5 | - | 1542.9 ± 824.0 (26.4%) |
| Signpost | 4x4c | 1e4 | 10 | 6848.9 ± 677.7 (1.1%) |
| | | 1e4 | - | 6861.8 ± 301.8 (1.5%) |
| | | 1e5 | 10 | 6983.7 ± 392.4 (1.6%) |
| | | 1e5 | - | - |
| Sixteen | 3x3 | 1e4 | 10 | 4770.5 ± 890.5 (2.9%) |
| | | 1e4 | - | 4480.5 ± 2259.3 (25.5%) |
| | | 1e5 | 10 | 3193.3 ± 2262.0 (57.0%) |
| | | 1e5 | - | 3517.1 ± 1846.7 (25.3%) |
| Undead | 4x4de | 1e4 | 10 | 5378.0 ± 1552.7 (0.5%) |
| | | 1e4 | - | 5324.4 ± 557.9 (0.6%) |
| | | 1e5 | 10 | 5666.2 ± 553.3 (0.5%) |
| | | 1e5 | - | 5771.3 ± 2323.6 (0.4%) |
| Untangle | 6 | 1e4 | 10 | 474.7 ± 117.6 (99.1%) |
| | | 1e4 | - | 1491.9 ± 193.8 (89.3%) |
| | | 1e5 | 10 | 597.0 ± 305.5 (96.3%) |
| | | 1e5 | - | 1338.4 ± 283.6 (88.7%) |

## E.6.5 LLM Evaluation

We have extended the PUZZLES library with an interface for large language models (LLMs) and vision language models (VLMs). This allows for easy evaluation of these models on truly out-of-distribution data. Thanks to the scalability of our benchmark, puzzle sizes can be continuously increased to match the current capabilities of the models. Currently, we focus on zero-shot evaluation of LLMs/VLMs, where the models are not provided with any specific training on the puzzle they need to solve. This is similar to a human solving a puzzle for the first time. For future evaluations, however, this could be improved by either training the model on a smaller version of the puzzle, or giving it some examples and allowing it to explicitly come up with a strategy. The LLM/VLM had to play the puzzle using the same cursor interface as the RL agents and the human expert, requiring it to plan ahead and execute single steps. This also means that the model was not able to solve the puzzle directly by outputting a solution in text format.

To reduce the computational cost of LLM evaluation, we implemented early termination after state repetition. Specifically, if an LLM enters the exact same state five times, indicating no progress in solving the puzzle, the evaluation terminates. Additionally, for each puzzle, we set the maximum number of steps to the upper bound of an optimal policy.

During evaluation, the LLM is not provided with the complete history of all past actions and states. Instead, it receives only the explanation of the game, the current discrete state, an image of the current puzzle state, and the most recent past action. Action masking is employed to limit the LLM’s choices to reasonable actions.

The game explanations and instructions for playing the game using the keyboard are sourced from https://www.chiar.greenen.org.uk/~sgtatham/puzzles/doc/. Further details about the LLM evaluation framework are available on the official GitHub repository at https://github.com/ETH-DISCO/rlp/tree/main/llm. The code is designed to easily support the addition and evaluation of new LLMs. For more information, please refer to https://github.com/ETH-DISCO/rlp?tab=readme-ov-file#run-an-llm-that-is-available-via-api.

We conducted experiments with Gemini 1.5 Flash and GPT-4o mini, allowing each LLM 5 attempts to solve each puzzle. Our results show that GPT-4o mini solved slightly more puzzles than Gemini 1.5 Flash. Interestingly, the evaluation with GPT-4o-mini took approximately 5 hours, while Gemini 1.5 Flash required only 1 hour.
