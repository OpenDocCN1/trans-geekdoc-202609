walking, physical contact with people, and object manipulation. The improved availability of tactile sensors has enabled research in this field to flourish (see chapter 8). Prior to the use of learning-based approaches, tactile sensor data were only used with handcrafted features (Yang, Sun, et al. 2016) or to trigger specific actions (Yamaguchi and Atkeson 2016). However, such methods may not scale well as tactile-sensing technology advances—for example, when a higher resolution and a larger amount of data are necessary, or as task complexity increases. By using learning-based approaches, in particular deep learning, it is now possible to handle tasks such as image recognition and natural language processing, which involve high-dimensional data and were previously difficult to process. Moreover, deep-learning approaches have recently been applied to tactile sensing, such as object recognition (Schmitz et al. 2014; Baishya and Bäuml 2016), tactile properties recognition (Gao et al. 2016; Yuan, Wang, et al. 2017), and grasping (Calandra et al. 2018).

In recent years, within research involving tactile sensors, object manipulation using robotic hands has been gaining attention since manipulation is one of the fundamental functions for a robot to perform various tasks such as tidying up, cooking, and folding clothes. In this chapter, the recent development of tactile learning and the following four categories of the object manipulation process are described: 1) object recognition, 2) grasping, 3) in-hand object pose estimation, and 4) in-hand object manipulation.

# Types of tactile sensors

Many different tactile sensors have been developed to improve manipulation in robotic hands (Dahiya et al. 2013; see also chapter 8 for a detailed analysis). The majority of these sensors, however, belong to one of the following three categories:

+   – Multitouch sensors that can only sense force information along one axis—namely, perpendicular to the surface of the sensor. These types of sensors are known as pressure sensors (Ohmura, Kuniyoshi, and Nagakubo 2006; Iwata and Sugano 2009; Mittendorfer and Cheng 2011; Fishel and Loeb 2012).

+   – Three-axis sensors that can sense both shear and pressure forces but are only single touch (Paulino et al. 2017).

+   – Three-axis sensors for both shear and pressure forces that are multitouch (Tomo et al. 2018; Yamaguchi and Atkeson 2016; Yuan, Dong, and Adelson 2017).

At the time of writing, there are only three sensors of the last type: uSkin (Tomo et al. 2018), Finger Vision (Yamaguchi and Atkeson 2016), and GelSight (Johnson and Adelson 2009; Dong, Yuan, and Adelson 2017; Yuan, Dong, and Adelson 2017). The uSkin measures the deformation of silicon during contact by monitoring changes in the magnetic fields of magnets in silicon. The sensor is able to measure both pressure as well as shear force per sensor unit for multiple contact points.

Instead of a magnet, the Finger Vision is a vision-based tactile sensor, meaning that it uses a camera to capture and measure the deformation of its attached marker during contact with the surface. In addition to contact sensing, it can also function as a proximity sensor since the Finger Vision uses transparent silicon.

The GelSight can be manufactured by covering the silicon surface of the Finger Vision with another layer of silicon that contains aluminum powder. The aluminum powder highlights the deformation of the silicon layer more clearly and hence allows for richer informa-