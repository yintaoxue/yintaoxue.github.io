---
layout: post
title: SOLR部署启动报错 Error filterStart
description: 部署solr启动tomcat报错：严重: Error filterStart
category: blog
---

Solr版本：solr3.7.2

#部署solr启动tomcat报错：

	org.apache.catalina.core.StandardContext startInternal
	严重: Error filterStart

#解决方法：

将发布包solr-4.7.2\example\lib\ext目录下的jar拷贝到WEB-INF\lib下从4.3版本开始发生变化

#参考：
[http://wiki.apache.org/solr/SolrLogging](http://wiki.apache.org/solr/SolrLogging)
[http://lucene.472066.n3.nabble.com/Solr-4-3-Tomcat-quot-Error-filterStart-quot-td4067038.html](http://lucene.472066.n3.nabble.com/Solr-4-3-Tomcat-quot-Error-filterStart-quot-td4067038.html)

#错误日志：

	信息: Deploying web application directory E:\opt\data\apache-tomcat-7.0.54\webapps\uq
	2014-6-16 19:12:05 org.apache.catalina.core.StandardContext startInternal
	严重: Error filterStart
	2014-6-16 19:12:05 org.apache.catalina.core.StandardContext startInternal
	严重: Context [/uq] startup failed due to previous errors
	2014-6-16 19:12:05 org.apache.catalina.startup.HostConfig deployDirectory
	信息: Deployment of web application directory E:\opt\data\apache-tomcat-7.0.54\webapps\uq has finished in 2,988 ms

