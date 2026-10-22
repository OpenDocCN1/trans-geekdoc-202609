Because of the lack of a good model store solution, companies like Stitch Fix resolve to build their own model store. Figure 10-10 shows the artifacts that Stitch Fix’s model store tracks. When a model is uploaded to their model store, this model comes with the link to the serialized model, the dependencies needed to run the model (Python environment), the Git commit where the model code generation is created (Git information), tags (to at least specify the team that owns the model), etc.

![](bbox=[0.13, 0.23, 0.84, 0.64])

Figure 10-10. Artifacts that Stitch Fix’s model store tracks. Source: Adapted from a slide by Stefan Krawczyk for CS 329S (Stanford).

# Feature Store

“Feature store” is an increasingly loaded term that can be used by different people to refer to very different things. There have been many attempts by ML practitioners to define what features a feature store should have.30 At its core, there are three main problems that a feature store can help address: feature management, feature

30 Neal Lathia, “Building a Feature Store,” December 5, 2020, https://oreil.ly/DgsvA; Jordan Volz, “Why You Need a Feature Store,” Continual, September 28, 2021, https://oreil.ly/kQPMb; Mike Del Balso, “What Is a Feature Store?” Tecton, October 20, 2020, https://oreil.ly/pzy0I.