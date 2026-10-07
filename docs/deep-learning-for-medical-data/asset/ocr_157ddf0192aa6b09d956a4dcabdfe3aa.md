# SAMENVATTING - SUMMARY IN DUTCH

Deze thesis heroverwegt de fundle componenten van deep learning en evalueert hoe toepassing in de context van medische beeldanalyse. Het identificeert drie belangrijke uitdagingen waar deep learning in dit domein tekort komt: de integratie van kundige kennis, het gebruiken van unlabeled data en het inschatten van model onzekerheid. De thesis is gestructureerd in delen die respectvelijk deze uitdagingen aanpakken.

In Deel I introduceert deze een nieuw deep learning model dat deskundige kennis integreert door middel van roto-reflective equivariance, om de nauwkeurigheid en robuustheid van medische beeldvorming te verbeteren, specifiek voor de detectie van metastatische weefsels in histopathologische preparaten. Het voorgestelde model presteert beter dan traditionele CNN-architecturen en is robuust onder input-perturbaties. Vervolgens wordtzocht hoe de deep learning-gemeenschap gemotiveerd kan worden om zich te richten op medische problemen. Een nieuwe dataset, PCam wordt geïroduceerd, afgeleid van de Camelyon16-challenge.

Deel II onderzoekt de voordelen van self-supervised representation learning door middel van Contrastive Predictive Coding (CPC) en introduceert Perturbative Predictive Coding (CPC2), de prestaties van CPC verbetert door specifieke medische beeldvormaugmentaties te integreren.

De III van deze thesis behandelt de uitdaging van het schatten van model onzekerheid, cruciaal voor medische besluitvorming met hoog risico. Het introduceert een nieuwe variational inference meth die het gebruik maakt van multinomiale verdelingen over quantized latent variabelen. De voorgestelde methode toont competitieve prestaties in onzekerheid schatten en risico analyse vergeleken met bestaande methoden.

De thesis concludeert dat door de geïdentificeerde uitdagingen te pakken, deep learning beter geschikt kan worden voor medische beeldvorm-