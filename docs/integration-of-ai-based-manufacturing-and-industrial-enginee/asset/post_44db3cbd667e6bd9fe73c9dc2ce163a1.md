
Danielsson et al. (2021) presents the quicker and easier deployment of web-based applications on cloud platforms. Quinton et al. (2014) developed a model to automatically select the suitable cloud environment to deploy. The work provides a scalable model to deal with dynamic changes in the cloud environment. Finally, the tool developed in Chen et al. (2013) provides the virtualization and management tools for constructing dynamic and virtual machines for the application.

## 8.3 AUTOMATED PROVISIONING ARCHITECTURE

The main objective of this system is to develop an automated one-click controller that will provision all the AI-driven web applications for developers and make it easy to carry out resource provisioning and deployment on cloud platforms. The deployment service needs to be automated (Wang et al., 2019a). The load balancing task to be taken care of during the deployment, considering the type of applications that needs to be deployed. In order to automate the deployment, it is necessary to benchmark the type and size of the application. Resource provisioning is performed by looking into the needs of the application and the available resources. The scripts required for the application’s configuration are then created using a middleware program (Bhambri et al., 2021).

The proposed system will be of great use to both technical and non-technical users if the entire process is automated. Multiple collaborators can work on multiple branches with the use of Phased.js, with a provision of monitoring the applications on the deployed servers. Applications are managed with less memory consumption and server crash issues can also be handled efficiently (Paoletti et al., 2018).

The architecture for Automated Provisioning is depicted in Figure 8.1.

![](img/3d190e19625a7567e7b93c8e95b18d9c_142_0.png)

FIGURE 8.1 Automated provisioning architecture.

## 8.4 METHODOLOGY

The proposed system creates a simple and minimal application which assists users in deployment procedure and introduces an auto resource allocation to the process. The web application will run locally on the host machine (which runs on a PhasedJS framework) and allows users to manage and deploy their applications on the production server (PaaS such as Heroku, AWS, Azure etc.).

Many processes work together cooperatively under the hood to achieve this task. Since Phased JS is based on NodeJS, every script runs asynchronously, which reduces CPU overheads and mean that the deployment becomes smoother. Since different applications have different memory requirements, PhasedJS automatically analyzes target applications for memory usage and sets a threshold before deployment. This ensures that the target application does not exceed the memory limit. Also, before deployment PhasedJS attaches a logger and a couple of bash scripts for target application scaling. The logger logs useful console statements to the end user for further debugging live applications.

In Figure 8.2 Phased Js Architecture is illustrated. The PhasedJS creates a package which includes user app, logger, scaling scripts and other helper bash scripts, which then is sent to the cloud platform for deployment.

Figure 8.3 summarizes in detail the dataflow design of the proposed architecture. This is called cloud orchestration, which means using multiple tools, processes, and API to combine and automate successful deployment of the target application. The coordination takes place in an orchestration layer which governs and controls all the deployed apps in one platform. The bash script creates a process called Master Process, which itself creates error handles and worker processes. A worker process takes care of an http request and a web socket connection. The master process automatically carries out the allocation of CPU and memory to the worker process. This allows the target application to scale and use memory within the target limit (Tanwar et al., 2022).

![](img/3d190e19625a7567e7b93c8e95b18d9c_143_0.png)

FIGURE 8.2 Phased.JS architecture.

![](img/3d190e19625a7567e7b93c8e95b18d9c_144_0.png)

FIGURE 8.3 Phased.Js data flow design.

## 8.5 IMPLEMENTATION

By using express framework and other scripting languages, the proposed system enables developers to deploy lightweight applications to the cloud.

Making a local app scalable:

```
cluster = require('cluster')
os = require('os')
expressServer =require('./app.js')
/*check if current process is master*/
if cluster.isMaster then {
    print "Master <process.pid> is running"
    /*get the number of cpu cores*/
    cpuCount = os.cpus().length
    /*create a worker for each cpu core*/
    for(i = 0; i < cpuCount; i++){
        cluster.fork()
    }
}
else {
    /*not a master process, so we'll just spawn the express server */
    expressServer()
    print "Worker <process.pid> started"
}
/*cluster API*/
/*create a new process if a worker dies*/
```

```
Cluster on 'exit' => callback(worker) {
    print "Worker ${worker.id} died"
    print "Starting a new worker"
    cluster.fork()
}
```

The approach applied here in PhasedJS is the pre-benchmarking done on the deployed application and compressed to make it compatible for deployment. The manual process of git version control is automated and the extra steps such as commit and push to git remote branches are completely removed and the deployment is completely done on any local git repository. Our PhasedJS was able to successfully deploy several applications made using react, angular, flask, next, go, etc. using resource provisioning and bash scripts which were used to automate the manual steps.

Figures 8.4, 8.5 and 8.6 are sample benchmarks of the application deployed on the server using which the threshold is determined.

![](img/3d190e19625a7567e7b93c8e95b18d9c_145_0.png)

FIGURE 8.4 Sample benchmark1.

![](img/3d190e19625a7567e7b93c8e95b18d9c_146_0.png)

FIGURE 8.5 Sample benchmark2.

Sequences of commands executed after the app is sent to target server:

```
#!/bin/bash
tar -C "/$1" -xvf myApp.tar &&
node benchmark.js &&
node setThreshold.js &&
npm install &&
npm start
```

Figure 8.7 depicts the experimental setup of Phased Js

```
error count: 0
stats {
  totalElapsed: 1198.1304010000313,
  main: {
    meter: {
      count: 1200,
      median: 130.84634999994887,
      p75: 140.62892575003207,
      p95: 198.48426009994583,
      p99: 226.7253292900161,
      p999: 234.72202170000423
      count: 2000,
      currentRate: 1070.5308542672988,
      '1MinuteRate': 0,
      '5MinuteRate': 0,
      '15MinuteRate': 0
    },
    histogram: {
      min: 51.5140000008289,
      max: 508.28610100085425,
      sum: 861257.12757699995,
      variance: 1295.9362372297717,
      mean: 170.62856378849997,
      stdev: 55.99911439507605,
      count: 2000,
      median: 169.57720000005793,
      p75: 184.61562499997732,
      p95: 236.69760650081787,
      p99: 297.97643179995775,
      p999: 508.2648178710389
    }
  }
}
```

FIGURE 8.6 Sample benchmark3.

![](img/3d190e19625a7567e7b93c8e95b18d9c_147_0.png)

FIGURE 8.7 Phased.js UI.

## 8.6 RESULTS AND DISCUSSION

AI-based applications are taken to act as the test cases used for testing the phased Js setup. These applications were chosen to highlight various statistical parameters and memory usage to manually deploy an application on the cloud and using a proposed automated system.

The metrics such as CPU usage, memory usage, resource allocation are measured using both manual and proposed systems. The results achieved are shown in the form of tables provided in Tables 8.1 and 8.2. The AI-based applications were chosen based on various parameters. We had taken some heavy applications to be deployed by PhasedJS.

TABLE 8.1
Time Comparison Table

| Application | Automated Time With Phased.js (seconds) | Manual Time Without Phased.js (seconds) |
|---|---|---|
| DownTube | 79 | 900 |
| Fertilizer recommendation | 50 | 600 |
| Test case App (self-deployment) | 30 | 300 |

TABLE 8.2
Relative Usage by Using Phased.js

| Applications | Memory Usage | CPU Usage |
|---|---|---|
| DownTube | 1.3× | 2× |
| Fertilizer Recommendation | 1.3× | 1.7× |

![](img/3d190e19625a7567e7b93c8e95b18d9c_148_0.png)

FIGURE 8.8 Result of Application 1 deployed using Phased.Js.
