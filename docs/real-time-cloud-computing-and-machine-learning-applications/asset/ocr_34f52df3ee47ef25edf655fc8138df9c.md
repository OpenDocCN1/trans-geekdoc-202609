654 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonon

# 6.4.4.4. Timer & TimerTask

+   - Timer Class
This class is a facility for threads to schedule tasks for future execution in a background thread. Tasks may be scheduled for one-time execution or repeated execution at regular intervals. Timer tasks should complete quickly. If a task takes excessive execution to complete, the "hogs" the timer's task execution thread. For this program, the schedule (TimerTask task, long delay, long period) method is used. It Schedules the specified task for fixed-delay execution, beginning after the specified delay. The timer can be terminated using the cancel () method that discarding any scheduled tasks.

+   - TimerTask Class
This class represents a class that defines a task that can be scheduled for onetime or repeated execution by a Timer. The TimerTask can be cancelled using the cancel () method. The task to be performed is implemented in the abstract run () method of the TimerTask object.

# 6.4.4.5. The Monitoring Process

When the application is started, the GUI shown in Figure 6.44 is presented to the user. The monitoring process can be started by clicking on the "Monitor" button. Clicking on the Monitor button triggers the monitorActionPerformed () method in which the following tasks are performed:

+   - First, it checks the state of the monitoring process to determine if it has started or not by verifying the value of the boolean monitoring.
- If the value returned is false, it the monitoring process has not yet started. The following tasks are performed:
  - The timer object is initialized with the default "new Timer() constructor.
  - A newTimer is created using the "new TimerTask() constructor. This object defines the task to be performed by the Timer object. The actions to be performed are defined in the abstract run () method of the TimerTask object. The actions performed by the TimerTask are explained below.
  - Capture data from the API using the JSOUP Library
  - A connection to the API endpoint is made using the connect () method of the JSOUP class. The body of the HTML page of the API endpoint is fetched using the get () method. The ignoreContentType () is set to true so that JSOUP ignores the content type when parsing the HTML document. A String representation of the API response is obtained using the .text () method of the Document object obtained by JSOUP.