# Domain-Agnostic Super-Resolution

# Abstract

Super-resolution techniques have made remarkable progress in recent years, especially in the vision domain. However, extending these advances to other data modalities has been challenging due to the need for specialized architectures tailored to each domain. In this chapter, we introduce FunctaFormer, a novel domain-agnostic super-resolution method capable of upscaling any arbitrary data type. Our approach leverages Implicit Neural Representations (INRs) to model data as continuous functions, providing a unified framework across different modalities. FunctaFormer obtains competitive performance across various domains, including images, audio, videos, 3D shapes, manifold data, and LiDAR scans.

# 5.1 Introduction

Super-resolution (SR) aims to reconstruct a high-resolution output from a given low-resolution input. While the specific notion of “resolution” varies