---
title: Daemon Monitoring
taxonomy:
    category: docs
---

## Server daemon configuration (`monitoring`,`log`)


##### `log-file`

| Item | Value |
| ---- | ----- |
| Description | Write messages to log file per default messages are output to stdout. |
| Type | string |
| Example | "/var/log/replication-manager.log" |

##### `log-file` (2.0), `logfile` (0.6)

| Item | Value |
| ---- | ----- |
| Description | Write messages to log file per default messages are output to stdout|
| Type | string |
| Example | `/var/log/replication-manager.log` |

##### `log-level`

| Item | Value |
| ---- | ----- |
| Description | Log verbosity level, og level >3 are very verbose and print the server monitoring workflow only to use in debugging |
| Type | int |
| Example | 1 to 7 |

##### `log-syslog ` (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | duplicate stdout to local UDP syslog port |
| Type          | boolean |
| Example       | true |

##### `log-rotate-max-age` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Rotate after this number of days    |
| Type          | integer |
| Default       | 7 |

##### `log-rotate-max-backup` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Keep this number of log files   |
| Type          | integer |
| Default       | 7 |

##### `log-rotate-max-size` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Rotate after this size in Mb  |
| Type          | integer |
| Default       | 5 |

##### `log-sql-in-monitoring` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Log all SQL queries send to backend for monitoring servers |
| Type          | boolean |
| Default       | false |

The sql_general.log can be found under each cluster directory and can be use to track what was trigger to backend during failover, rejoin step

##### `verbose` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Add more debugging information |
| Type          | int |
| Example       | 1 |

##### `memprofile`

| Item          | Value |
| ----          | ----- |
| Description   | Write a memory profile to a file readable by pprof. |
| Type          | string |
| Default       | `/tmp/repmgr.mprof` |


##### `monitoring-datadir` (2.0), `working-directory` (1.1)

| Item          | Value |
| ----          | ----- |
| Description   | Path to write temporary and persistent files |
| Type          | string |
| Example       | `/var/lib/replication-manager` |

##### `monitoring-sharedir` (2.0), `share-directory` (1.1)

| Item          | Value |
| ----          | ----- |
| Description   | Path to the share files provided with packaging with no write access |
| Type          | string |
| Default Value | `/usr/share/replication-manager` |

##### `monitoring-basedir` (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | Path to a basedir where a data and share directory can be found, used mostly for developer or collocation of the product with a tar.gz deployment. |
| Type          | string |
| Default Value | `/usr/local/replication-manger` |

##### `monitoring-save-config` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Save configuration changes to <monitoring-datadir>/clusterd |
| Type          | bool |
| Default Value | false |



##### `monitoring-ticker` (2.0), `read-timeout` (1.1)

| Item          | Value |
| ----          | ----- |
| Description   | Monitoring interval in seconds. |
| Type          | integer |
| Default Value | 2 |

##### `monitoring-write-heartbeat` (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | Inject heartbeat into proxy or via external VIP. Without this option long inactive write period and database expire log days can make switchover to failed without founding last binlog position |
| Type          | bool |
| Default Value | 2 |

##### `monitoring-write-heartbeat-credential` (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | Credential DB user to inject heartbeat into proxy or via external VIP.  |
| Type          | bool |
| Default Value | 2 |

##### `title`

| Item          | Value |
| ----          | ----- |
| Description   | An explicit description of the managed cluster  |
| Type          | string |
| Default Value | `CRM production MariaDB cluster` |

##### `monitoring-schema-change` (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | Monitor schema change |
| Type          | bool |
| Default Value | true |

This parameter is needed for alerting on schema change and for sharding proxy to push DDL change

##### `monitoring-schema-change-script` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Monitor schema change external script |
| Type          | string |
| Default Value | ""|


##### `monitoring-performance-schema` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Monitor performance schema |
| Type          | bool |
| Default Value | true |

This enable to get slow queries templating from performance schema

##### `monitoring-processlist` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   | Enable capture 50 longest process via processlist |
| Type          | bool |
| Default Value | true |

##### `monitoring-queries` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   |  Monitor long queries |
| Type          | bool |
| Default Value | true |

Currently unused

##### `monitoring-query-rules` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   |   Monitor query routing from proxies |
| Type          | bool |
| Default Value | true |

Enable to build a consolidated view of multiple cluster proxies query rules


##### `monitoring-capture` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   |   Enable capture on internal error for 5 monitor loops |
| Type          | bool |
| Default Value | true |


The capture files are found in the cluster datadir

Capture are show slave status, show processlist, show global status, show innodb status

##### `monitoring-capture-trigger` (2.1)

| Item          | Value |
| ----          | ----- |
| Description   |   Enable capture on internal error for 5 monitor loops |
| Type          | string  |
| Default Value | "ERR00076,ERR00041" |

Trigger to capture on max connections threshold and slave delay

##### `monitoring-capture-file-keep` (2.1)
| Item          | Value |
| ----          | ----- |
| Description   |  Purge capture file keep that number of them |
| Type          | integer  |
| Default Value |5 |


### Deprecated

##### `daemon`  (2.0)

| Item          | Value |
| ----          | ----- |
| Description   | Tell to monitor in post 2.0 release |
| Type          | integer |
| Default Value | 1 |
