
# References

Dutta, M. K., Singh, A., Singh, A., Burget, R., & Prinosil, J. (2015). Digital identification tags for medical fundus images for teleophthalmology applications. *Proceedings 2015 38th International Conference on Telecommunications and Signal Processing*. pp. 781-784. Prague, Czech Republic. DOI: 10.1109/TSP.2015.7296372

Gonzalez, R. C., & Woods, R. E. (2002). *Digital Image Processing* (2nd Ed.). Prentice-Hall Publishers, Upper Saddle River, NJ 07458.

Hai, H., Xie, D. Q., & Ke, Q. (2018). A watermarking-based authentication and image restoration in multimedia sensor networks. *International Journal of High-Performance Computing and Networking*, 12(1), 65–73. doi:10.1504/IJHPCN.2018.093846

Hu, Z., Guo, X., Hu, X., Chen, X., & Wang, Z. (2005). The Identification and Recognition Based on Ocular Fundus. *Springer Link Lecture Notes in Computer Science*, 3832, pp. 770-776.

Karmakar, R., & Basu, A. (2019). Implementation of a Reversible Watermarking Technique for Medical Images. In Bhattacharyya, S. (Ed.), *Intelligent Innovations in Multimedia Data Engineering and Management* (pp. 1–37). Hershey, PA: IGI Global. doi:10.4018/978-1-5225-7107-0.ch001

Melkemi, K., & Golea, N. E. H. (2017). ROI-based fragile watermarking for medical image tamper detection. *International Journal of High-Performance Computing and Networking*, 1(1), 1. doi:10.1504/IJHPCN.2017.10013846

Muharemagic, E., & Furht, B. (2004). Survey of Watermarking Techniques and Applications. Department of Computer Science and Engineering, Florida Atlantic University, 777 Glades Road, Boca Raton, FL 33431-0991, USA.

Nammer, N., & Emman, E. L. (2007). Hiding a Large Amount of Data with High Security using Steganography Algorithm. *Journal of Computer Science*, 3(4). pp. 223-232.

Poonkuntran, S., Rajesh, R. S., & Eswaran, P. (2009a). Reversible, Multilayered Watermarking Scheme for Fundus Images Using Intra-Plane Difference Expanding. *Proceedings of the IEEE International Advance Computing Conference*, pp. 2583-2587, Patiala, India.

Poonkuntran, S., Rajesh, R. S., & Eswaran, P. (2009b). Wavetree Watermarking: An Authentication Scheme for Fundus Images. *Proceedings of the IEEE Sponsored International Conference on Emerging Trends in Computing*, pp. 507-511. India.

Poonkuntran, S., Rajesh, R. S., & Eswaran, P. (2009c). A Robust Watermarking Scheme for Fundus Images Using Intra-Plane Difference Expanding. *Proceedings of the IEEE Sponsored International Conference on Emerging Trends in Computing*. pp. 433-436. India.

Poonkuntran, S., Rajesh, R. S., & Eswaran, P. (2009e). Analysis of Difference Expanding Method for Medical Image Watermarking. *Proceedings of 2009 International Symposium on Computing, Communication, and Control*, pp. 30-34. Singapore.

Poonkuntran, S., Rajesh, R. S., & Eswaran, P. (2009d). Imperceptible Watermarking Scheme for Fundus Images Using Intra-Plane Difference Expanding. *International Journal on Computer and Electrical Engineering*, 1(4). 1793-8198.

Shanmugam, P., Rajesh, R. S., & Perumal, E. (2008). A Reversible Watermarking With Low Warping: An Application to Digital Fundus Images. *Proceedings of the IEEE International Conference on Computer and Communication Engineering*, pp. 472-477.

Sliwa, J. (2019). Assessing complex evolving cyber-physical systems (case study: Smart medical devices). *International Journal of High-Performance Computing and Networking*, 13(3), 294–303. doi:10.1504/IJHPCN.2019.098570

Tian, J. (2002). Reversible Watermarking by Difference Expansion. *Proceedings of Workshop on Multimedia and Security: Authentication, Secrecy, and Steganalysis*, pp. 19-22.

Tian, J. (2003). Reversible Data Embedding using a Difference Expansion. *IEEE Transactions on Circuits and Systems for Video Technology*, 13(8), pp. 890-893.

Wang, B., Ding, Q., & Gu, X. (2019). A secure reversible chaining watermark scheme with hidden group delimiter for WSNs. *International Journal of High-Performance Computing and Networking*, 14(3). doi:10.1504/IJHPCN.2019.102126

Wu, M., & Liu, B. (2003). Data Hiding in Image and Video. I. Fundamental Issues and Solutions. *IEEE Transactions on Image Processing*, 12(6), pp. 685-695.

# Chapter 7

**Phuc Do**  
University of Information Technology (VNU-HCM), Vietnam

**Trung Hong Phan**  
University of Information Technology (VNU-HCM), Vietnam

## Abstract

In this chapter, `Image2vec` or `Video2vector` are used to convert images and video clips to vectors in large multimedia database. The `M-tree` is an index structure that can be used for the efficient resolution of similarity queries on complex objects. `M-tree` can be profitably used for content-based retrieval on multimedia databases provided relevant features have been extracted from the objects. In a large multimedia database, to search for similarities such as `k-NN` queries and `Range` queries, distances from the query object to all remaining objects (images or video clips) are calculated. The calculation between query and entities in a large multimedia database is not feasible. This chapter proposes a solution to distribute the `M-Tree` structure on the `Apache Spark` framework to solve the `Range Query` and `kNN Query` problems in large multimedia database with a lot of images and video clips.

## Introduction

Multimedia databases contain images and video clips (Guo, 2013; Riaz, Ashraf, & Aslam, 2014). Today, the volume of multimedia database contains a huge number of objects. In this we use `Image2vec` (Garcia-Gasulla, Béjar, Cortés, Ayguadé, & Labarta, 2015) or `Video2vec` (Hu, Li, & Li, 2016) to convert images and videos to vectors and store these vectors for more convenience in processing. To search for similarities such as `kNN` queries and `Range` queries in vector spaces (representing images and video clips), we need to calculate distances from the query vector to all remaining vectors. In a large multimedia database, the vector space with millions to billions of vectors. The calculation of distances as above is not feasible. Therefore, we need a method to reduce the number of distance calculations in these problems. The `M-Tree` structure, which is a distance-based vector space indexing method, can effectively solve the `Range` queries and `kNN` queries (Ciaccia, Patella, & Zezula, 1997; Kouahla, 2011). Because the `M-Tree` structure is implemented on a local system, it only solves problems in small vector spaces, in which the set of vectors can fit into a computer. However, very large multimedia databases contain millions of vectors of image or video clip are very popular. The local `M-Tree` structure cannot meet the new needs to solve problems of similarity searching in large vector spaces, in which vectors must be stored distributedly across multiple computers. Therefore, in this article, we propose a solution to distribute the `M-Tree` structure on the `Apache Spark` framework (Assefi, Behravesh, Liu, & Tafti, 2018; Shanahan & Dai, 2019; Zecevic & Bonaci, 2017) to solve the `kNN` and `Range Query` problems in large vector spaces. In addition, we also present experimental results on creating both local and distributed `M-Tree` structures built from 64-dimentional vector sets with different scales. Finally, we present the experimental results on the `kNN` and `Range` queries on the built `M-Tree` structures of a multimedia database of image and video clips.

The main contributions of this article are as follows:

*   Converting multimedia objects as images and video clips to vectors using `Image2vec` and `Video2vec`.
*   Proposing a solution to distribute the `M-Tree` structure to meet new needs in the era of big data.
*   Solving `kNN` and `Range Query` problems based on the distributed `M-Tree` structure.
*   Providing relevant experimental results.

The rest of this article is organized as follows. Section 2 is the related works. Section 3 introduces the knowledge base we use in this article. Section 4 is the methodology. Section 5 is the experiments. The final is the conclusion and future work.

## Related Work
