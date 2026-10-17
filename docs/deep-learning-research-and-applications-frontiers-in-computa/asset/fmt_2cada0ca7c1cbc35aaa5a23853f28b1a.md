
![Figure 1.17: IBM Watson Studio subsections. (a) Projects (both for new and existing) subsection, (b) creating new project, and (c) services (both for new and existing) subsection.](graphic/converted/b_9783110670905-001_fig_017.png)

Figure 1.17: IBM Watson Studio subsections. (a) Projects (both for new and existing) subsection, (b) creating new project, and (c) services (both for new and existing) subsection.

Once a project is created, an admin can add data assets to it for working with that data. Data assets can be added from local files, community, and database connections. All the collaborators in the project are automatically authorized to access the data in the project. After adding raw data into project, data needs to be refined, which consists of cleansing and shaping. Cleansing can be done by removing data that is incorrect, incomplete, improperly formatted, or duplicated. Whereas shaping data can be done by filtering, sorting, combining or removing columns, and performing operations. The refined data is ready for analyzing and visualizing \[[14](#bodymatter-001.xhtml#b_9783110670905-001_ref_014)\].

## 1.7 Conclusion

In this chapter, an overview with their relationship between AI, ML, and DL has been specified. At the same time, the reason for considering DL as state of the art in modern era has been discussed. The main focus is to highlight different cloud platforms available in the market by different vendors. In Section 1.6, different steps of using ML with IBM Watson Studio – have been described, including data set management and cleansing raw data. Comparative discussion in terms of performance, accuracy, 24 × 7 availability, and user-friendliness between the ML platform offerings by multiple organizations can be considered for future study.

## References

\[1\][https://www.forbes.com/sites/bernardmarr/2017/08/08/the-amazing-ways-how-google-uses-deep-learning-ai/#509e1a7b3204](https://www.forbes.com/sites/bernardmarr/2017/08/08/the-amazing-ways-how-google-uses-deep-learning-ai/%23509e1a7b3204) [→](#bodymatter-001.xhtml#xref_d63256e561)

\[2\][https://www.techtimes.com/articles/3442/20140213/netflix-deep-learning-based-ai-will-tell-you-what-you-want-to-watch-but-do-we-need-one.htm](https://www.techtimes.com/articles/3442/20140213/netflix-deep-learning-based-ai-will-tell-you-what-you-want-to-watch-but-do-we-need-one.htm) [→](#bodymatter-001.xhtml#xref_d63256e564)

\[3\][https://www.digitaltrends.com/computing/mit-future-video/](https://www.digitaltrends.com/computing/mit-future-video/) [→](#bodymatter-001.xhtml#xref_d63256e567)

\[4\][https://theintercept.com/2018/04/13/facebook-advertising-data-artificial-intelligence-ai/](https://theintercept.com/2018/04/13/facebook-advertising-data-artificial-intelligence-ai/) [→](#bodymatter-001.xhtml#xref_d63256e570)

\[5\][https://www.systematics.co.il/wp-content/uploads/Deep\_Learning\_ebook.pdf](https://www.systematics.co.il/wp-content/uploads/Deep_Learning_ebook.pdf) [→](#bodymatter-001.xhtml#xref_d63256e573)

\[6\][https://www.cs.ubbcluj.ro/~gabis/ml/ml-books/McGrawHill%20-%20Machine%20Learning%20-Tom%20Mitchell.pdf](https://www.cs.ubbcluj.ro/~gabis/ml/ml-books/McGrawHill%20-%20Machine%20Learning%20-Tom%20Mitchell.pdf) [→](#bodymatter-001.xhtml#xref_d63256e616)

\[7\]Haykin Simon S. Neural networks and learning machines. Pearson, Upper Saddle River, 2009, 3. [a](#bodymatter-001.xhtml#xref_d63256e636), [b](#bodymatter-001.xhtml#xref_d63256e687), [c](#bodymatter-001.xhtml#xref_d63256e802)

\[8\]Deng L. A tutorial survey of architectures, algorithms, and applications for deep learning. APSIPA transactions on signal and information processing, 2014, 3. [→](#bodymatter-001.xhtml#xref_d63256e1041)

\[9\]Deng L., Dong Y. Deep learning: Methods and applications. Foundations and Trends® in Signal Processing, 2014, 7, 3–4, 197–387. [→](#bodymatter-001.xhtml#xref_d63256e1050)

\[10\]Liu W., Zidong W., Xiaohui L., Nianyin Z., Yurong L., & Fuad E. A. A survey of deep neural network architectures and their applications. Neurocomputing, 2017, 234, 11–26. [→](#bodymatter-001.xhtml#xref_d63256e1053)

\[11\]Schmidhuber J. Deep learning in neural networks: An overview. Neural networks, 2015,61, 85–117. [→](#bodymatter-001.xhtml#xref_d63256e1133)

\[12\]Bishop Ch. M. Pattern recognition and machine learning (information science and statistics). 2006. [a](#bodymatter-001.xhtml#xref_d63256e1136), [b](#bodymatter-001.xhtml#xref_d63256e1740)

\[13\][https://hortonworks.com/blog/exciting-data-science-experience-hdp/](https://hortonworks.com/blog/exciting-data-science-experience-hdp/) [→](#bodymatter-001.xhtml#xref_d63256e2217)

\[14\]Kanit W., Smilkov D., Wexler J., Wilson J., Mané D., Fritz D., Krishnan D., Viégas F.B., & Wattenberg M. Visualizing dataflow graphs of deep learning models in TensorFlow. IEEE transactions on visualization and computer graphics, 2018, 24, 1, 1–12. [→](#bodymatter-001.xhtml#xref_d63256e2363)

# 2 Convolutional Neural Networks: A Bottom-Up Approach

Karan Maheshwari School of Computer Science and Engineering, Vellore Institute of Technology, Vellore, India. Aditya Shaha School of Computer Science and Engineering, Vellore Institute of Technology, Vellore, India. Dhruv Arya School of Computer Science and Engineering, Vellore Institute of Technology, Vellore, India. Rajkumar Rajasekaran School of Computer Science and Engineering, Vellore Institute of Technology, Vellore, India. B. K. Tripathy School of Information Technology and Engineering, Vellore Institute of Technology, Vellore, India.

#### Abstract

A lot has changed in the world since the inception of the so-called deep learning (DL) era. Unlike conventional machine learning algorithms, where human learns more of feature extraction than machine, which just crunches numbers, DL algorithms are quite promising as they have revolutionized the way we deal with data and have become adept in taking humanlike decisions. Based on the powerful notion of artificial neural networks, these learning algorithms learn to represent data or, if we rephrase, can extract features from raw data. DL has paved way for end-to-end systems where one learning algorithm does all the tasks. Convolutional neural networks have earned a lot of fame lately, especially in the domain of computer vision where in some cases its performance has beaten that of humans. A lot of work has been done on convNets and in this chapter we will demystify how convolutional neural networks work and will illustrate using one novel application in the field of astronomy where we will do galaxy classification using raw images as input and classify them based on its shape. In addition to this we will investigate what features the network is learning. We will also discuss how DL superseded other forms of learning and some recent algorithmic innovations centered on convolutional neural nets.

Keywords: deep learning (DL), convolutional neural networks, galaxy classification, artificial neural networks, deconvolution,

## 2.1 Introduction
