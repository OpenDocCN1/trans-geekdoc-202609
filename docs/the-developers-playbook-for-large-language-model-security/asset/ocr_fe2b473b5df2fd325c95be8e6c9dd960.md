# # Importance of SBOMs

A software bill of materials is a comprehensive inventory or a detailed list of all components, libraries, and modules that comprise a piece of software. Think of it as a manifest or an ingredient list for software, detailing every element in the final product. This includes code written by the software development team and any open source or third-party components integrated into the software.

![](bbox=[0.175, 0.23, 0.26, 0.305])

The software bill of materials derives from the manufacturing term “bill of materials” (BOM), a comprehensive inventory that lists all the materials, components, and sub-assemblies needed to manufacture a product. It typically includes part names, numbers, quantities, and other descriptive information.

The purpose of an SBOM is to provide clear visibility into the software’s composition, which is crucial for security, compliance, and management. By understanding precisely what’s in their software, organizations can better monitor for vulnerabilities, comply with legal and licensing requirements, and manage updates and patches more effectively. In supply chain security, an SBOM is a vital tool for identifying potential risks and ensuring the integrity of software components.

The information tracking in your SBOM is essential for rapid response and remediation, reducing the window of opportunity for attackers. Furthermore, an SBOM helps your company comply with security standards and regulations, as it provides proof of due diligence in using secure and licensed components. In the increasingly complex software development landscape, where dependencies are deeply intertwined, an SBOM acts as a map, guiding the way to a more secure and resilient software infrastructure.

Let's see how we might apply and extend SBOM concepts to our LLM models and applications.

# # Model Cards

Earlier in this chapter, we learned that Hugging Face has become the de facto place to trade machine learning models and training sets. With a need to track important model information and dependencies, the company developed a standardized artifact called a model card.

Hugging Face’s model cards are designed to provide comprehensive information about each AI model hosted on its platform. The goal is to offer users—whether developers, researchers, or end users—a clear understanding of a model’s capabilities, limitations, and intended use cases. This approach aligns with broader efforts in the AI community to ensure that AI models are used ethically and effectively.