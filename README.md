Eureka
=====
[![Build Status](https://travis-ci.org/Netflix/eureka.svg?branch=master)](https://travis-ci.org/Netflix/eureka)

Eureka is a REST (Representational State Transfer) based service that is primarily used in the AWS cloud for locating services for the purpose of load balancing and failover of middle-tier servers.

At Netflix, Eureka is used for the following purposes apart from playing a critical part in mid-tier load balancing.

* For aiding Netflix Asgard - an open source service which makes cloud deployments easier, in  
    + Fast rollback of versions in case of problems avoiding the re-launch of 100's of instances which 
      could take a long time.
    + In rolling pushes, for avoiding propagation of a new version to all instances in case of problems.

* For our cassandra deployments to take instances out of traffic for maintenance.

* For our memcached caching services to identify the list of nodes in the ring.

* For carrying other additional application specific metadata about services for various other reasons.


Building
----------
The build requires java8 because of some required libraries that are java8 (servo), but the source and target compatibility are still set to 1.7.


Support
----------
[Eureka Google Group](https://groups.google.com/forum/?fromgroups#!forum/eureka_netflix)


Documentation
--------------
Please see [wiki](https://github.com/Netflix/eureka/wiki) for detailed documentation.

代码构建
--------------
代码构建的时候记得有两个地方需要改
在bulid.gradle 里面的插件 nebula.netflixoss 需要改成5.1.1 的版本不然会报错
plugins {
    id 'nebula.netflixoss' version '5.1.1'
}
然后用的gradle 需要在2.1版本以上4.0版本以下的，不然也会报错jersey 会有问题
jdk最好是用1.8的 如果用jdk10及10以上的版本也会报错