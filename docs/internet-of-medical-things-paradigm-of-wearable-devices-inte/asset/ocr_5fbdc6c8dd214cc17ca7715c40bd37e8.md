# Role of Big Data in e-Healthcare

![](bbox=[0.277, 0.093, 0.722, 0.233])

**FIGURE 8.10** Input data.

A working structure of MapReduce is shown in Figure 8.10. The three phases are summarized below:

+   * **Splitting Phase**: The raw data is split into different chunks of data as shown in Figure 8.11. The number of splits is equivalent to the number of mappers available each chunk of data is sent to one mapper.
* **Map Phase**: This phase takes the input chunk of data from the HDFS and converts it into an Intermediate Dataset as shown in Figure 8.12. The tasks that convert raw data into intermediate data are called Maps.
* **Reduce Phase**: The Reduce phase is further divided into three sub-phases as shown in Figure 8.13.
    * **Shuffle phase** by which the Intermediate Dataset is transferred to one or multiple Reducers.
    * **Sort phase** in which the Reducer groups the input by keys.
    * **Reduce phase** in which the Reducer processes the intermediate data received from the Mappers and produces the final output. The number of Reducers used is equivalent to the number of outputs required.

Other facilities available in MapReduce are the following:

+   * **Reporter**: It is used to report the progress of the MapReduce task. The Mapper and Reducer can use the Reporter to report their progress. Further, it can also be used by these programs as an indication that they are alive and

![](bbox=[0.277, 0.747, 0.722, 0.867])

**FIGURE 8.11** Splitting phase.