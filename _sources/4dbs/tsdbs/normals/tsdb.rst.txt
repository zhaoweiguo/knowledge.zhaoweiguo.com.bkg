其他时序数据库
################

* RRDtool http://oss.oetiker.ch/rrdtool/
* :ref:`Graphite <graphite>`  
* Kdb+  http://kx.com/
* Druid http://druid.io/
* KairosDB  http://kairosdb.github.io/


* from: https://www.sojson.com/blog/67.html
* RRD(round-robin-database): RRDtool使用的底层存储。C语言编写的。性能比较高
* whisper: Graphite底层的存储,Python写的
* prometheus: An open-source service monitoring system and time series database. 目前只有单机版本。
* InfluxDB: 开源distributed time series, metrics, and events database。Go语言编写, 不依赖于其他外部服务。底层支持多种存储引擎，目前是LevelDB, RocksDB, HyberLevelDB和LMDB(0.9之后只支持Bolt，最新版本采用了自己写的存储引擎)。
* OpenTSDB [1]_ : 基于HBase编写的Time Series Database
* kairosdb: OpenTSDB的改善版，底层存储引擎是Cassandra。
* Heroic: Kairosdb的改善版，Spotify公司开源的时序数据库（Spotify的监控框架），引入了ElasticSearch作为元数据索引。目前还处于不稳定状态。


.. [1] http://opentsdb.net/index.html






