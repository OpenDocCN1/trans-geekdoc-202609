7. The next configuration option pertains to database usage. The options are Multifunctional Database, for both InnoDB and MyISAM storage engines with resources split evenly between the two; Transactional Database, which enables both InnoDB and MyISAM but dedicates the most server resources to InnoDB; and Non-Transactional Database Only, which disables InnoDB and applies all resources to MyISAM. Unless you know exactly what your database will be used for, select the Multifunctional Database radio button and click Next to continue.

8. If you have selected a database usage option that includes the InnoDB storage engine, the next step in the configuration process enables you to configure the disk location and storage thresholds. The defaults are shown in Figure 2.8, which you can simply confirm by clicking Next to continue, or you can change these settings and then click Next to continue with your custom settings in place.

![](bbox=[0.07, 0.445, 0.57, 0.73])

**FIGURE 2.8** Tune the disk usage options for the InnoDB storage engine.

9. The next configuration option determines the number of concurrent connections to your MySQL server. Your setting will depend on the amount of traffic and database usage by your website or application. The default setting is Decision Support (DSS)/OLAP, which has a maximum number of 100 concurrent connections