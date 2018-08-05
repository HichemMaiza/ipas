# Implementing Predictive Analytics with Spark in Azure HDInsight

This tutorial is about creating a spark cluster on the Microsoft ASURE cloud using HDInsight service.

## Provisioning a Spark Cluster using HDInsight service

### Create a HDInsight Service

* Search for `HDInsight` in the `create a resource` search bar (a big green **+** sign in the left corner of the screen) as shown in fig11, then hit create as shown in fig12

* <img src="img/step11.png" width=800 />
* ![step12](img/step12.png)

### We will create our cluster with our custom configuration

* Cluster name: kratos0

* Subscription : Free trial

* Cluster Type : Spark

* Operating System : Linux

* Version : Spark 2.2.0 (HDI 3.6)

![step13](img/step13.png)

### Specify user access infromations

* Cluster login user name : kratosuser (used in case of http connexion)

* Cluster login password : ********* (used in case of http connexion)

* Secure shell (SSH) user name : sshkratosuser (used in case of ssh connexion, consol connexion)

* Ressource group : kratosgroup0

* Location : East US 2 (the data center)

### Storage Settings

the cluster consists of multiple virtual machine which we called nodes, they will need shared storge so they can work on data. we need to specify where that shared storage will be hosted. For large big data processing we use Data lake store but we will stick with Azure Storage at the moment

* Primary storage type : Azuer Storage

* Selection method : My subscriptions

* Create a new Storage account : kratosstore0

* Default container : kratos0 (a blob container to store shared files for the cluster)

![step14](img/step14.png)

### Chose nodes sizes (the cluster size)

* Number of Worker nodes : 1 this parameter has a default value of 4. This a tutoriel I will set it to 1 but in production you have to chose other configurations.

* Worker node size : A4 (1 node, 8 cores) Genral Purpose

* Head node size : D13 v2 (2 nodes, 16 cores)

![step15](img/step15.png)

### Advanced settings

* Nothing to specify, Just clik `Next`

### Summary

* This is a validation step

* click  `create` to create the cluster

![step16](img/step16.png)

And That's it our deployement is finished

### Work with the cluster

* Go to cluster dashbord

![step17](img/step17.png)
![step18](img/step18.png)

* login with your http credentials (connect over a http)

![step19](img/step19.png)
![step20](img/step20.png)

* login over ssh connextion (use your ssh credentials)

copy the link
![step21](img/step21.png)
Depends on your operating system. I'm using windows 10 so i'll make use of `Ubuntu terminal application` to connect via ssh. You can also use `Putty`
![step21](img/step21.png)

```sh
ssh sshkratosuser@kratos0-ssh.azurehdinsight.net
```

You have to put in mind that your are connected to the one node so when you list files you will get the files in that specific node `hno` for this case. it's not the shared storage for that cluster.

![step22](img/step22.png)

If you want to work with shared storage of the cluster. the storage shared with all the other nodes you have to use ``hdfs dfs` command

```sh
hdfs dfs -ls /
```

![step23](img/step23.png)

## Author

* **Hichem MAIZA**

## Imoprtant Links

* [Microsoft Azure Portal](www.portal.azure.com/)

## Acknowledgements
