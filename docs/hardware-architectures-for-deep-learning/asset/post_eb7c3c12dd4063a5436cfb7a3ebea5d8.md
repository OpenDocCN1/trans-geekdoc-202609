
- 11.3.2 Input interface (DAC) 274
- 11.3.3 Training scheme 276
- 11.3.4 Output interface (ADC) 280
- 11.4 Results and discussion 282
- 11.4.1 Input interface (DAC) 282
- 11.4.2 Output interface (ADC) 284
- 11.4.3 Inverter-based memristive neuromorphic circuit 285
- 11.4.4 Impact of unideal condition 289
- 11.5 Conclusion 291
References 292

# Index 297

# About the editors

Masoud Daneshtalab is a tenured associate professor at Mälardalen University (MDH) in Sweden, an adjunct professor at Tallinn University of Technology (Tal-Tech) in Estonia, and sits on the board of directors of Euromicro. His research interests include interconnection networks, brain-like computing, and deep learning architectures. He has published over 300-refereed papers.

Mehdi Modarresi is an assistant professor at the Department of Electrical and Computer Engineering, University of Tehran, Iran. He is the founder and director of the Parallel and Network-based Processing research laboratory at the University of Tehran, where he leads several industrial and research projects on deep learning-based embedded system design and implementation.

# Preface

Deep learning has greatly affected our everyday life by providing novel IT services and also changing the ways we interact with computers and other technology. In particular, deep learning has brought an unprecedented increase in the quality and accuracy of computer vision and speech recognition which serve as the base of many smart applications and services.

Computer vision is perhaps the most important area that benefits from deep learning. Deep learning enables computers to detect objects of interest in images and classify or identify categories of objects with higher precision. These advances in computer vision have translated to improvements in robotics, autonomous drones, drive-assisted systems and self-driving cars (with early prototypes currently under-test by Tesla and Google). Face detection and recognition can be included in many services (e.g., security and authentication) in smart environments and Internet of Things (IoT) solutions.

Further, recent innovations in deep learning are completely reshaping the future of computer-aided diagnosis, disease detection procedures, and medical decision support tools. With deep learning-based computer vision, computers are expected to read and analyze X-rays, magnetic resonance imaging (MRI), electrocardiogram (ECG) waveforms, and computed tomography (CT) scan images more rapidly and accurately than doctors to diagnose diseases less and invasively. Another emerging application of deep learning in medicine has healthcare monitoring, where biometric monitoring services are implemented on wearable or implantable devices to enable the measurement and analysis of patient data in real time.

Furthermore, deep learning has enabled developing novel and accurate speech recognition functions on smartphones and computers. The popular examples include the voice-enabled features of Android and Windows, Amazon's Alexa, Apple's Siri, and Microsoft's Cortana.

Smart text and language processing is another field that has been revolutionized by deep learning. Google Translate now provides text-to-text and spoken-to-spoken translation for more than 100 pairs of languages. Online subtitle generation for video streams is another capability that is now viable by deep learning.

This rapid growth of the server, desktop, and embedded applications/services based on deep learning has brought about a renaissance in the practical and theoretical aspects of neural networks as the basis of any deep learning system.

However, the superior accuracy and efficiency of neural networks come at the cost of high computational complexity, power consumption, and memory bandwidth demand. State-of-the-art neural networks in many practical applications, such as real-time object recognition in an autonomous vehicle or data analysis in a server, are orders of magnitude larger than conventional neural networks that have long been used since the 1990s. Generally, the size and complexity of neural networks are proportional to the problem complexity. For example, while a few hundred neurons implement a simple digit classifier, an accurate image processing neural network needs thousands of neurons, with several millions of arithmetic operations, to recognize objects of interest in a single picture or video frame.

Modern graphics processing units (GPUs), with tens of Teraflops throughput, often have enough processing power for real-time execution of such large neural networks. However, the power consumption of powerful GPUs (100–200 W) is far beyond the tight power budget of a typical embedded system. Even if dissipating 200 W in a self-driving car, which receives power from the car’s battery, is not a serious issue, the cost of modern GPUs ($1000+) may be prohibitive.

Due to the limited capabilities and power budget of embedded and mobile edge devices, some deep learning-based services on such systems rely on cloud-centric architectures to offload deep learning tasks to cloud-side servers. The way or pre-processed data is sent to the cloud, and the results are sent back to the device. However, this model causes different problems like latency, high energy consumption of continuous data transmission, loss of data privacy and security, and the need for an always-on network connection. Therefore, there is a strong demand to move the deep learning execution to embedded devices to improve latency, power, and privacy issues.

Even for desktop and server computers that employ high-performance central processing units (CPUs) and GPUs with a larger power budget, running a large neural network with millions of neurons and several gigabytes of model parameters is a challenging task. In particular, power- and performance-efficient deep learning implementation in cloud-side servers is critical to reduce power delivery and cooling expenses, which constitute one of the largest components of the total cost of ownership (TCO).

To meet the excessive computational power demand of deep learning applications, the semiconductor industry has introduced deep learning hardware accelerators and domain-specific processors, in which the data path, instruction set, and register configuration are tailored to the specific processing requirements and dataflow model of neural networks. In this way, a customized processor can run neural networks with higher throughput and power efficiency than a general-purpose processor, where a piece of software runs on.

Starting from 2016, almost all major players in the semiconductor industry have fabricated their deep learning accelerators. The example deep learning processors include TPU, IBM TrueNorth, Nvidia Volta, AMD Radeon Instinct, Samsung M1, Silicon Silicon, Qualcomm-A1100, Intel Nervana, Eye IQ, Apple A12-Bionic, Huawei Ascend30, and Cadence C5, to name a few. There are also a stunning number of smaller companies and start-ups that design hardware and software solutions for deep learning.

The academic research follows the same trend as the industrial efforts, with a large body of research work targeting efficient implementation for different this trend is reflected in the growing number of research papers on neural networks published in flagship conferences and journals in recent years.

This book provides an overview of the basic concepts and recent advances in some of the deep learning hardware research areas.

The book is structured into five parts. Part I of the book contains three chapters to introduce the fundamental concepts of neural networks. This part first provides a background on the neural network concepts and models (Chapter 1) and then reviews in more detail some design issues of two important neural network classes, i.e., recurrent neural network (RNN) (Chapter 2) and feedforward (Chapter 3) models.

Part II has two chapters devoted to low-precision data representation for neural networks. The chapters review and introduce state-of-the-art proposals to simplify neural network execution using stochastic (Chapter 4) and binary (Chapter 5) data representations. The chapters show that due to their inherent error-tolerance property, neural networks experience negligible or sublinear accuracy when when approximate representations are employed.

In addition to error tolerance, recent hardware accelerators exploit some interesting properties of the weights and intermediate activations of neural networks to boost performance and energy efficiency. High degree of weight and intermediate data sparsity is one of these properties that neural networks demonstrate. This property suggests that a considerable portion of neural network weights are very small, even equal to zero, or redundant. Furthermore, many intermediate data propagated throughout the network during evaluation become zero. Part III of the book addresses this sparsity issue and its potential capabilities to simplify neural networks. It contains two chapters that first survey effective techniques, from both software and hardware sides, to exploit model sparsity for efficient neural network implementation (Chapter 6), and then introduces in more detail a method that exploits redundant weight values to reduce neural network power consumption (Chapter 7). Convolutional neural network (CNN) is a very popular deep neural network model, which is primarily used for image processing. Part IV is devoted to hardware and software techniques for CNN implementation in power-limited embedded systems. This part first introduces a novel field-programmable gate array architecture for embedded CNN implementation (Chapter 8). Chapter 9 shows how a large convolutional neural network can be broken into a sequence of smaller networks to reduce the model complexity and make it more amenable to acceleration. The final part of the book, Part V, covers the emerging and ever-growing trend of accelerating neural networks on analog hardware. This part presents a mixed-signal neuromorphic platform for always-on biomedical signal processing (Chapter 10), followed by introducing novel-based neuralbased architectures for IoT platforms ( platforms 11).

The rapidly expanding field of deep learning hardware is a popular research topic in electrical/computer engineering and computer science, as part of the syllabus for undergraduate and postgraduate courses at many universities.

This book aims to complement the research and teaching and serve as a reference for researchers, postgraduate students, and engineers who work on learning-based services and hardware platforms.
