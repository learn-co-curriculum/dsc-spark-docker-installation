The best way to run pyspark on a machine in a virtualized environment is to use docker. Docker is a container technology
that allows developers to 'package' their software and ship it so that it takes away the headache of things like setting up
environment properly, configuring logging, setting proper options, breaking the machine etc.. basically removes 
the excuse `It works on my machine`
I'll stop babbling about docker and containers. If you're interested to know more, head here: http://unix.stackexchange.com/questions/254956/what-is-the-difference-between-docker-lxd-and-lxc

Step1: Installing docker on Mac
- Download & install the docker dmg file: https://download.docker.com/mac/stable/Docker.dmg
- Download & install docker toolbox:      https://download.docker.com/mac/stable/DockerToolbox.pkg

We will be using Kitematic (which comes bundled with docker toolbox) for managing docker environment

Step2:
- Click on the docker toolbar on mac and select `Kitematic`
- Sign up on docker hub (so that you can push your containers to be used on other machines.. remember the `It works on my machine excuse`?)
- Search for pyspark-notebook and click on the image provided by *jupyter* (it is imperative to use the one from jupyter)
- Once it is downloaded, it will start an ipython-kernel and on the right half of kitematic will say something like `web preview`.

something similar to this:
![kitematic_ex](https://datarhei.github.io/restreamer/img/installation-osx-windows-kitematic-3.png "Kitematic example")

Click on it and it will take you to the browser which will ask for a token id. 
- Go back to the kitematic and check the left bottom of terminal-like screen for string that says: `token?=`. Copy the
text after that and put it into the jupyter notebook page.

Step3: (only for using python2)
- Workers by default start with python3 kernel (regardless of how you start the notebook kernel). To change this behavior
and strictly use python2, you should always execute following command as the first line in the notebook:
```
import os
os.environ['PYSPARK_PYTHON'] = 'python2'
```

Step4: 
- Finally a reminder that we are running everything locally. we don't have separate clusters to perform execution. Hence,
when creating spark context, you should do:
```
import pyspark
sc = pyspark.SparkContext('local[*]')
```

Example:
- Try running this:
```
rdd = sc.parallelize(range(1000))
rdd.takeSample(False, 5)
```
