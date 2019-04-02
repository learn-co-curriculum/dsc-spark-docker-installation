
# Installing and Configuring PySpark with Docker

## Introduction

In addition to running on the clusters, Spark provides a simple standalone deploy mode. We can launch a standalone cluster either manually, by starting a master and workers by hand, or use our provided launch scripts. It is also possible to run these daemons on a single machine for testing. In this lesson, we'll look at installing a standalone version of Spark on Windows and Mac machines. All the required tools are open source and directly downloadable from official sites referenced in the lesson. 

## Objectives
You will be able to:
- Install Docker and Kitematic on Windows/Mac environments
- Install a standalone version of Spark on a local server 
- Test the spark installation by running a simple test script

## Docker
For this section, we shall run PySpark on a single machine in a virtualized environment using __Docker__. Docker is a container technology that allows __packaging__ and __distribution__ of software  so that it takes away the headache of things like setting up environment, configuring logging, configuring options etc. Docker basically removes the excuse "*It works on my machine*". 

[Visit this link learn more about docker and containers](https://www.zdnet.com/article/what-is-docker-and-why-is-it-so-darn-popular/)

### Install Docker and docker Toolbox
 
 
- Download & install Docker on Mac : https://download.docker.com/mac/stable/Docker.dmg
- Download and install Docker on Windows:  https://hub.docker.com/editions/community/docker-ce-desktop-windows

In addition to Docker, we will also need to down and install the docker toolbox. 

- Docker Toolbox for Mac: https://docs.docker.com/toolbox/toolbox_install_mac/
- Docker toolbox for Windows: https://docs.docker.com/toolbox/toolbox_install_windows/

Visit following guides for step by step installation instructions. 

[Guide for installing docker toolbox on mac](https://docs.docker.com/toolbox/toolbox_install_mac/)

[Guide for installing docker toolbox on windows](https://docs.docker.com/toolbox/toolbox_install_windows/)


### Kitematic

Docker toolbox is mainly required above for a Docker plugin called ["Kitematic"](https://kitematic.com/). Kitematic allows "one click install" of containers in Docker running on your Mac and windows and lets you control your app containers from a graphical user interface (GUI). This takes away a lot of cognitive load required to set up and configure virtual environments. 

Once Docker and Toolbox are successfully installed, we need to perform following tasks in the given sequence. 


### Click on the docker toolbar on mac and select Kitematic

<img src="kite.png" width=200>

### Sign up on docker hub 
Upon running kitematic, you will be asked to sign up on docker hub. This is optional , but recommended as it can allow to share your docker containers and run them on different machines. 

This option can be accessed via "My Repos" Section in the Kitematic GUI. 
 
<img src="hub.png" width=400>

### Search for `pyspark-notebook` repository, and click on the image provided by `jupyter` 
It is imperative to use the one from __jupyter__ for our labs to run as expected, as there are lots of other offerings available. 

![](search.png)

Run the repo when it is downloaded, it will start an `ipython-kernel`. To run jupyter notebooks , click on the right half of kitematic where it says "web preview".

![](click.png)

This will open a browser window asking you for a token ID. Go back to the kitematic and check the left bottom of terminal-like screen for string that says: `token?= --- ` as shown above . Copy the text after that and put it into the jupyter notebook page.


![](token.png)


This will open a new jupyter notebook , like we've seen before. We are now ready to program in spark.  

## Testing the installation

In order to make sure everything went smooth, Let's run a simple script in a new jupyter notebook. 

```python
import pyspark
sc = pyspark.SparkContext('local[*]')
rdd = sc.parallelize(range(1000))
rdd.takeSample(False, 5)
```

If everything went fine , you should see an out like this:
```
[941, 60, 987, 542, 718]
```

Do not worry if you dont fully comprehend what above meant. Next we will look into some basic programming principles and methods from Spark which will explain this. 

## Summary 

In this lesson, we looked at installing Spark using Docker container. The process works same for both Mac and Windows based systems. Make sure to follow all steps in the given sequence. 
