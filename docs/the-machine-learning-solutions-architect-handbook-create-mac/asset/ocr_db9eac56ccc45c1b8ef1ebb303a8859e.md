As there are multiple parallel streams in the pipeline, we can use AWS Step Functions to orchestrate the parallel execution of different streams. These can generate the following output streams:

+   - **Subtitle and text analysis stream:** This stream primarily uses Amazon Transcribe and Amazon Comprehend AI services. Transcribe transcribes the audio portion of the videos and generates both subtitle files and regular transcripts. The regular transcripts are then used by Comprehend to run text analysis. Some example metadata that extracted from this stream can include the entities of people and places, the language used, and sentiment for different sections of the transcripts.

+   - **Video tagging and analysis stream:** This stream identifies objects, scenes, activities, people, celebrities, and text with timestamps in the different video frames.

+   - **Image tagging and analysis stream:** This stream identifies objects, scenes, celebrities, and text in different images.

The outputs from the media processing streams can be further processed and organized as useful metadata for the media assets. Once this has been done, they are stored in a media metadata repository to support content search and discovery.

# E-commerce product recommendation

Product recommendation is an important capability in e-commerce. It is a key enabler for increasing sales, improving engagement experience, and retaining customer loyalty.

In e-commerce product recommendation, multiple functional requirements can be framed as ML problems:

+   - **Recommendations based on customer behaviors and profiles:** ML algorithms learn the intrinsic characteristics and purchasing patterns of customers from their past e-commerce interactions to predict the products they will like.

+   - **Ability to address recommendations of cold items (items without history):** ML algorithms can explore customers' reactions toward cold items and adjust their recommendations to balance explore (recommending new items) and exploit (recommending known items).

+   - **Ability to recommend similar items:** ML algorithms can learn the intrinsic characteristics of products based on product attributes and collective interaction patterns from a group of customers to determine product similarity.