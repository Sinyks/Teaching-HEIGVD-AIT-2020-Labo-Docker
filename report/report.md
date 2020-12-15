# AIT2020 - Labo-Docker

```
Authors:
  Sacha Perdrizat
  Moïn Danai
  Alban Favre
```

### Introduction
In this lab we will dive in the Loadbalancing with an dynamique containers infrastructure.

### Task 0

- **[M1]**
No, Because we can't manage manually the failure of the containers (with 2 it is ok but with more than 1k services it will be complicated)
- **[M2]**
We need to:
   - add a new entry in the ``.env`` file
   - add the new entry in the ``haproxy.cfg``
   - create the new container with the right ip address

- **[M3]**
We can use a dynamic solution to detect the configuration of our containers and transmit it to our loadbalancer.  

- **[M4]**
On of our container can speak to the others for retrieving their configuration.

- **[M5]**
TODO
- **[M6]**
TODO

**Delivrable**

The page ``192.168.42.42:1936``

![](report/images/capture/task0/Q1.png)

The URL of our Repository is :
https://github.com/Sinyks/Teaching-HEIGVD-AIT-2020-Labo-Docker

### Task 1


**Deliverables**:

1. Take a screenshot of the stats page of HAProxy at <http://192.168.42.42:1936>. You should see your backend nodes. It should be really similar to the screenshot of the previous task.

2. Describe your difficulties for this task and your understanding of what is happening during this task. Explain in your own words why are we installing a process supervisor. Do not hesitate to do more research and to find more articles on that topic to illustrate the problem.

### Task 2

**Deliverables**:

1. Provide the docker log output for each of the containers: `ha`, `s1` and `s2`. You need to create a folder `logs` in your repository to store the files separately from the lab report. For each lab task create a folder and name it using the task number. No need to create a folder when there are no logs.

Example:

```
   |-- root folder
     |-- logs
       |-- task 1
       |-- task 3
       |-- ...
```

2. Give the answer to the question about the existing problem with the current solution.

3. Give an explanation on how `Serf` is working. Read the official website to get more details about the `GOSSIP` protocol used in `Serf`. Try to find other solutions that can be used to solve similar situations where we need some auto-discovery mechanism.


### Task 3

**Deliverables**:

1. Provide the docker log output for each of the containers:  `ha`, `s1` and `s2`.Put your logs in the `logs` directory you created in the previous task.

3. Provide the logs from the `ha` container gathered directly from the `/var/log/serf.log` file present in the container. Put the logs in the `logs` directory in your repo.

### Task 4

**Deliverables**:

1. You probably noticed when we added `xz-utils`, we have to rebuild the whole image which took some time. What can we do to mitigate that? Take a look at the Docker documentation on [image layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) Tell us about the pros and cons to merge as much as possible of the command. In other words, compare:

  ```
  RUN command 1
  RUN command 2
  RUN command 3
  ```

  vs.

  ```
  RUN command 1 && command 2 && command 3
  ```

  There are also some articles about techniques to reduce the image
  size. Try to find them. They are talking about `squashing` or
  `flattening` images.

2. Propose a different approach to architecture our images to be able to reuse as much as possible what we have done. Your proposition should also try to avoid as much as possible repetitions between your images.
   
3. Provide the `/tmp/haproxy.cfg` file generated in the `ha` container after each step.  Place the output into the `logs` folder like you
   already did for the Docker logs in the previous tasks. Three files are expected.
   
   In addition, provide a log file containing the output of the `docker ps` console and another file (per container) with
`docker inspect <container>`. Four files are expected.
   
4. Based on the three output files you have collected, what can you say about the way we generate it? What is the problem if any?


### Task 5

**Deliverables**:

1. Provide the file `/usr/local/etc/haproxy/haproxy.cfg` generated in the `ha` container after each step. Three files are expected.
   
In addition, provide a log file containing the output of the `docker ps` console and another file (per container) with
   `docker inspect <container>`. Four files are expected.
   
2. Provide the list of files from the `/nodes` folder inside the `ha` container. One file expected with the command output.
   
3. Provide the configuration file after you stopped one container and the list of nodes present in the `/nodes` folder. One file expected
   with the command output. Two files are expected.
   
 In addition, provide a log file containing the output of the `docker ps` console. One file expected.
   
4. (Optional:) Propose a different approach to manage the list of backend nodes. You do not need to implement it. You can also propose your
   own tools or the ones you discovered online. In that case, do not forget to cite your references.

### Task 6

**Deliverables**:

1. Take a screenshots of the HAProxy stat page showing more than 2 web applications running. Additional screenshots are welcome to see a
   sequence of experimentations like shutting down a node and starting more nodes.
   
   Also provide the output of `docker ps` in a log file. At least one file is expected. You can provide one output per step of your
experimentation according to your screenshots.
   
2. Give your own feelings about the final solution. Propose improvements or ways to do the things differently. If any, provide
   references to your readings for the improvements.
   
3. (Optional:) Present a live demo where you add and remove a backend container.

### Difficulties

### Conclusion