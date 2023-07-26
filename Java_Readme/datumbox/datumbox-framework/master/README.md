Datumbox Machine Learning Framework
===================================
[![Build Status](https://api.travis-ci.org/datumbox/datumbox-framework.svg)](https://travis-ci.org/datumbox/datumbox-framework) [![Windows Build status](https://ci.appveyor.com/api/projects/status/2aqkak8kmt8ooj4i?svg=true)](https://ci.appveyor.com/project/datumbox/datumbox-framework) [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.datumbox/datumbox-framework-lib/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.datumbox/datumbox-framework-lib) [![License](https://img.shields.io/:license-apache-brightgreen.svg)](./LICENSE)

[![Datumbox](http://www.datumbox.com/img/logo.png)](http://www.datumbox.com/)

The Datumbox Machine Learning Framework is an open-source framework written in Java which allows the rapid development Machine Learning and Statistical applications. The main focus of the framework is to include a large number of machine learning algorithms & statistical methods and to be able to handle large sized datasets. 

Copyright & License
-------------------

Copyright (C) 2013-2020 [Vasilis Vryniotis](http://blog.datumbox.com/author/bbriniotis/). 

The code is licensed under the [Apache License, Version 2.0](./LICENSE).

Installation & Versioning
-------------------------

Datumbox Framework is available on [Maven Central Repository](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.datumbox%22%20AND%20a%3A%22datumbox-framework-lib%22). 

The latest stable version of the framework is 0.8.2 (Build 20200805). To use it, add the following snippet in your pom.xml:
```
    <dependency>
        <groupId>com.datumbox</groupId>
        <artifactId>datumbox-framework-lib</artifactId>
        <version>0.8.2</version>
    </dependency>
```

The latest snapshot version of the framework is 0.8.3-SNAPSHOT (Build 20200805). To test it, update your pom.xml as follows:
```
    <repository>
       <id>sonatype-snapshots</id>
       <name>sonatype snapshots repo</name>
       <url>https://oss.sonatype.org/content/repositories/snapshots</url>
    </repository>

    <dependency>
        <groupId>com.datumbox</groupId>
        <artifactId>datumbox-framework-lib</artifactId>
        <version>0.8.3-SNAPSHOT</version>
    </dependency>
```

The [develop branch](https://github.com/datumbox/datumbox-framework/tree/develop) is the development branch (default github branch), while the [master branch](https://github.com/datumbox/datumbox-framework/tree/master) contains the latest stable version of the framework. All the stable releases are marked with [tags](https://github.com/datumbox/datumbox-framework/releases).

The releases of the framework follow the [Semantic Versioning](http://semver.org/) approach. For detailed information about the various releases check out the [Changelog](./CHANGELOG.md).

Documentation and Code Examples
-------------------------------

All the public methods and classes of the Framework are documented with Javadoc comments. Moreover for every model there is a JUnit Test which clearly shows how to train and use the models. Finally for more examples on how to use the framework checkout the [Code Examples](https://github.com/datumbox/datumbox-framework-examples/) or the [official Blog](http://blog.datumbox.com/).

Pre-trained Models
------------------

Datumbox comes with a large number of pre-trained models which allow you to perform Sentiment Analysis (Document & Twitter), Subjectivity Analysis, Topic Classification, Spam Detection, Adult Content Detection, Language Detection, Commercial Detection, Educational Detection and Gender Detection. To get the binary models check out the [Datumbox Zoo](https://github.com/datumbox/datumbox-framework-zoo/).

Which methods/algorithms are supported?
---------------------------------------

The Framework currently supports performing multiple Parametric & non-parametric Statistical tests, calculating descriptive statistics on censored & uncensored data, performing ANOVA, Cluster Analysis, Dimension Reduction, Regression Analysis, Timeseries Analysis, Sampling and calculation of probabilities from the most common discrete and continues Distributions. In addition it provides several implemented algorithms including Max Entropy, Naive Bayes, SVM, Bootstrap Aggregating, Adaboost, Kmeans, Hierarchical Clustering, Dirichlet Process Mixture Models, Softmax Regression, Ordinal Regression, Linear Regression, Stepwise Regression, PCA and several other techniques that can be used for feature selection, ensemble learning, linear programming solving and recommender systems.

Bug Reports
-----------

Despite the fact that parts of the Framework have been used in commercial applications, not all classes are equally used/tested. Currently the framework is in Alpha version, so you should expect some changes on the public APIs on future versions. If you spot a bug please [submit it as an Issue](https://github.com/datumbox/datumbox-framework/issues) on the official Github repository. 

Contributing
------------

The Framework can be improved in many ways and as a result any contribution is welcome. By far the most important feature missing from the Framework is the ability to use it from command line or from other languages such as Python. Other important enhancements include improving the documentation, the test coverage and the examples, improving the architecture of the framework and supporting more Machine Learning and Statistical Models. If you make any useful changes on the code, please consider contributing them by sending a pull request.

Acknowledgements
----------------

Many thanks to [Eleftherios Bampaletakis](http://gr.linkedin.com/pub/eleftherios-bampaletakis/39/875/551) for his invaluable input on improving the architecture of the Framework. Also many thanks to ej-technologies GmbH for providing a license for their [Java Profiler](http://www.ej-technologies.com/products/jprofiler/overview.html) and to JetBrains for providing a license for their [Java IDE](https://www.jetbrains.com/idea/).

Useful Links
------------

- [Code Examples](https://github.com/datumbox/datumbox-framework-examples/)
- [Datumbox Zoo: Pre-trained models](https://github.com/datumbox/datumbox-framework-zoo/)
- [Datumbox.com](http://www.datumbox.com/)
- [Machine Learning Blog](http://blog.datumbox.com/)

