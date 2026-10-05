# Towards AI - Monte Carlo Tree Search

.quantQ.mcts.runMCTS[:bucket]
// decide move first vs versus
$0=count[`treeMCTS`]
// randomly finish game

```
bucketTMP:(quantQ.mcts.oneTurnRun)/([{=x`isWinner`];`moveState
    ->isWinner)
    (bucket[`movesState`]);0)
tabTMP:bucket[`treeMCTS`]:tDTMP(`index:1);gameTree: enlist enlist
    bucketTMP[`movesState`]
    [count[`movesState`];isWinner:bucketTMP[`isWinner`)]];
// continue building tree
```

// create local bucket and add features
bucketTMP:
// indexInTree defines what part of the game is stored into the
bucketTMP(`indexInTree`):0;
// treeDepth counts local iterations, to keep track when
    going through the existing tree
bucketTMP(`treeDepthCounter`):0;
isWinner determines local winner
bucketTMP[`isWinner`]:0);

```
// run the MCTS
bucketTMP:(quantQ.mcts.oneTurnRun)/([{=x`isWinner`]);bucketTMP
    :);
1+bucketTMP[`indexInTree`]);
```

```
// extract variables for updated game tree
newGameTree:(count[bucket[`movesState`]])_bucketTMP[`movesState`]):til
isWinner:count[bucket[`indexInTree`]];
ewIndex:bucket[`treeMCTS`]+1);
// updating the existing game tree
bucketTMP:bucket[`treeMCTS`];
bucket[`treeMCTS`]:bucketTMP, ([]) index:newIndex;gameTree:
    elist
newGameTree:isWinner:isWinner)
```

```
// stop if the maximum number of trees has been reached
if(bucket[`numberOfRuns`]<count bucket[`treeMCTS`];bucket[`isWinner`]:1j
    -);
// return bucket
bucket:
```

Let stress several elements in the function. The first run of the MCTS algorithm is run explicitly as a random play. Where there is no prior information available, the oneTurn is iterated until end. Then, the `treeMCTS` table is updated accordingly by appending the first row into the empty table. This approach allows us to start with a pre-trained table where this step would be omitted. For iterations beyond the first, the oneMCTSTurn function is used. After the iteration of this function ends, the