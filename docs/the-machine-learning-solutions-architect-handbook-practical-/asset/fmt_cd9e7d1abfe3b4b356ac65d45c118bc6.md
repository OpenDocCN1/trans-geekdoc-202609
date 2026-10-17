
Medical device and pharmaceutical manufacturers are piloting the use of generative AI for automated manufacturing and production oversight. By analyzing written standard operating procedures and process documentation, generative models can validate that critical manufacturing processes adhere to regulatory compliance standards and internal policies. Any deviations or missing steps can be flagged to ensure protocols meet requirements before reaching inspection. This proactive auditing can identify compliance gaps upstream and enable corrective actions sooner. With the ability to thoroughly scan extensive documentation and compare them to guidelines at scale, generative AI can strengthen quality assurance and streamline production oversight in medical product manufacturing.

## Media and entertainment

The media and entertainment sector presents tremendous opportunities to apply generative AI across the entire content value chain and consumer touchpoints.

For content production, media companies are exploring the use of generative models to autonomously synthesize completely new images, videos, and other multimedia from textual prompts. These models can also meaningfully enhance existing assets, such as increasing image and video resolution, colorizing black-and-white content, or restoring corrupted and damaged files.

In content distribution, generative AI can unlock capabilities like automated metadata tagging, hyper-relevant search, and customized recommendations that can substantially improve media discovery and engagement. Marketing campaigns can also leverage dynamically generated, personalized content tailored to individual user interests and localized preferences. With contextually relevant experiences powered by generative AI, media companies can deepen audience relationships, improve retention, and better monetize content catalogs.

Media companies are piloting the use of generative AI to enrich customer experience such as automating live sports commentary and reporting. By ingesting real-time data and narratives around games, generative models can provide customized play-by-play and analysis as engaging, conversational outputs. When applied to customer service, conversational AI interfaces leveraging these models could deliver highly responsive, natural interactions to resolve subscriber issues and queries.

## Automotive and manufacturing

The automotive and manufacturing industries are exploring generative AI across customer experience, product engineering, and smart manufacturing use cases.

For instance, some automakers are evaluating conversational AI to power interactive digital owner’s manuals in the car or on mobile devices. This would enable voice-guided vehicle troubleshooting and contextual search for repair procedures. Generative AI call center analytics can also help summarize transcripts to address customer issues faster and improve agent training.

In product engineering, generative models are being explored to ideate exterior and interior styling concepts balanced with considerations like aerodynamics, space utilization, and ergonomics. These models can also predict simulation outcomes to complement physics-based testing.

For smart manufacturing, generative AI can assist by producing detailed machine troubleshooting guides using maintenance manuals, issue patterns, and repair procedures. This can enable self-guided maintenance and reduced downtime.

With the potential benefit and impact promised by generative AI, what does it take to turn an idea into a practical generative AI solution? How do we navigate the various stages of the generative AI project lifecycle? What are the different science and technology options available for consideration? What challenges and risks should we be keeping a watchful eye on? In this next section, we will explore and try to answer these questions.

# The lifecycle of a generative AI project and the core technologies

The lifecycle for developing and deploying generative AI solutions spans multiple stages, with some variations from traditional ML projects, such as model customization and model evaluation. While certain phases like use case definition and data preparation align closely, stages including model development, training, evaluation, and adaptation take on unique characteristics for generative models.

![](OEBPS/Images/B20836_15_01.png)

Figure 15.1: Generative AI project lifecycle

At a high level, a generative AI project consists of a series of stages, including identification of business use cases, model selection or pre-training, domain adaptation and model customization, post-customization model evaluation, and model deployment. It’s important to recognize that while a generative AI project places significant emphasis on the capabilities and quality of the model itself, the model constitutes just one facet within the broader development of a generative AI solution.

Before delving into the lifecycle details, it’s crucial to grasp the various adoption approaches that different organizations take, as they significantly impact project execution. Based on their business objectives, organizations typically fall into one of three categories for generative AI adoption:

*   `Model consumers`: Direct consumers of `foundation models` (`FMs`) typically leverage them as-is to address specific business challenges. While they may employ techniques like prompt engineering for customization, they don’t invest resources in teaching the model new domains or tasks. Their primary focus is on solving immediate business problems for internal or external customers seeking end-user applications rather than building foundational technology blocks. Additionally, these organizations generally don’t prioritize enhancing existing FMs with proprietary datasets. An example of a model consumer is a generative AI application developer who builds a customer support chatbot that directly consumes the OpenAI GPT model or Claude model from Anthropic via application APIs.

*   `Model tuners`: FM tuners are organizations aiming to fine-tune existing FMs for specific business purposes. This refinement can involve domain adaptation, enriching the model with domain-specific data (e.g., finance or medicine), or teaching the model new tasks (e.g., writing in a specific style). These organizations typically have distinct business goals, including generating revenue, reducing costs, improving productivity, or enhancing customer experiences. They possess proprietary datasets that offer a competitive edge, as well as the scientific and engineering expertise needed to tailor an existing model to meet their unique business needs. An example of a model tuner could be a financial services organization enriching an open-source LLM with their proprietary dataset such as a financial research report, so the model can perform better with research report summarization tasks.

*   `Model developers`: FM developers are organizations dedicated to constructing FMs from the ground up. These models are subsequently provided to other organizations for either commercial purposes or for contribution to the open-source community, promoting the advancement and widespread adoption of this technology. Notable examples of FM developers include OpenAI, Anthropic, Google, Meta, Amazon, open-source communities, and government entities. These models typically serve as fundamental building blocks for a variety of general-purpose capabilities, including text generation, summarization, text-to-image generation, question answering, mathematics, planning, and reasoning. The primary audience for these FMs consists of other organizations and developers aiming to create applications powered by generative AI technology, in addition to their internal use. Organizations in this category are characterized by their substantial expertise in data sciences and ML engineering, as well as robust financial backing for these endeavors.
