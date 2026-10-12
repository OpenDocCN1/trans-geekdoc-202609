
## 18.3.7 Investigation of Decision Making in the Brain

Kyathanahally et al. [\[105\]](#c18.xhtml#c18-bib-0105) developed a joint ICA technique for building a layered experimental design in which multiple tasks – from simple to complex – with additional layers of complexity introduced at each stage are used in decision making. This is demonstrated using tasks involving intertemporal choice between immediate and future prospects. In their method using EEG–fMRI, (i) the native temporal/spatial resolutions of either modality are not compromised and (ii) fast temporal dynamics of decision making together with the involved deeper striatal structures could be characterized. The joint ICA algorithm assumes a single mixing matrix `A` for both the modalities. Consequently, the acquired (mixed) signals can be represented as:

(18.31)
```
[X_EEG  X_fMRI] = A × [S_EEG  S_fMRI]
```

where `S_EEG` and `S_fMRI` represent respectively, the EEG and fMRI source signals. They showed that the spatiotemporal neural substrates underlying their proposed complex intertemporal task simultaneously incorporating rewards, costs, and uncertainty of future outcomes could be predicted using a linear model from neural substrates of each of these factors. This was not the case for spatial and temporal features obtained separately from fMRI and EEG, respectively. However, certain prefrontal activations in the complex task could not be predicted from the activations for simpler tasks, indicating that Donder's assumption of pure insertion (or cognitive subtraction) [\[106\]](#c18.xhtml#c18-bib-0106) has limited validity. Overall, our approach provides a realistic and novel framework for investigating the neural substrates of decision making with high spatiotemporal resolution.

## 18.3.8 Application to Schizophrenia

Joint EEG–fMRI has been used for identification of a biomarker for schizophrenia [\[107\]](#c18.xhtml#c18-bib-0107). A coupled matrix and tensor factorizations (CMTF) approach has been followed in this work to capture underlying patterns more accurately without imposing strong constraints on the latent neural patterns, i.e. biomarkers.

EEG, fMRI, and sMRI data collected during an auditory oddball task (AOD) from a group of subjects consisting of patients with schizophrenia and healthy controls, were used in their work.

In their CMTF approach the coupling is along the subject mode. The proposed joint matrix‐tensor parameters and latent variables are estimated by minimizing the following cost function through an alternating optimization approach [\[107\]](#c18.xhtml#c18-bib-0107):

(18.32)
```
f(λ, Σ, Γ, A, B, C, D, E) = ‖X̲ − [λ; A, B, C]‖² + ‖Y − AΣDᵀ‖² + ‖Z − AΓEᵀ‖² + β(‖λ‖₁ + ‖σ‖₁ + ‖γ‖₁)
```

where `X̲` is the fMRI tensor, `Y` is the EEG matrix, `Z` is the sMRI matrix, and `σ` and `γ` are the vectors constructed respectively from the diagonal elements of `Σ` and `Γ`. `‖∙‖₁` stands for *l*₁‐norm operation.
