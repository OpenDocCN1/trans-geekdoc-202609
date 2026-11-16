# Chapter 5

# Deep material networks for fiber suspensions with infinite material contrast¹

# 5.1 Introduction

For composites with kinematically unconstrained solid phases, the literature presented in section 1.2.4 provides compelling evidence for the accuracy and versatility of (direct) DMNs. However, the (direct) DMN architecture has yet to be applied to composites involving fluids or infinite material contrast, which is required for suspensions of rigid fibers. Because (direct) DMNs are based on laminates of solids, the treatment of fluids with a DMN architecture requires a different type of building block. Additionally, treatment of infinite material contrast with DMNs is challenging, because the rank-one laminates of a DMN have singular effective properties if one of the phases is singular, i.e., rigid. Therefore, the singular effective properties of the rank-one laminates may propagate through the whole DMN during the training and evaluation processes, rendering the effective properties of the DMN singular as

¹ This chapter is based on the sections 1 to 5 of the publication "Deep material networks for fiber suspensions with infinite material contrast" (Serr et al., 2024b).