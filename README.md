# shinken-pack-collectd-shinken

## Description

This Shinken monitoring pack is used to manage shinken services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-shinken: Manage all default thresholds and values for services

### Services

| Service name           | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| $KEY processes         | Check Shinken processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _shinken_processes         |
| Shinken - Listen $KEY$ | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _shinken_listen            |

## Default values

    _shinken_processes                          shinken-arbiter $(shinken-arbiter)$$(1:2)$$(1:2)$,shinken-broker $(shinken-broker)$$(1:)$$(1:)$,shinken-poller $(shinken-poller)$$(1:)$$(1:)$,shinken-reactionner $(shinken-reactionner)$$(1:)$$(1:)$,shinken-receiver $(shinken-receiver)$$(1:)$$(1:)$,shinken-scheduler $(shinken-scheduler)$$(1:)$$(1:)$
    _shinken_listen                             7767 (webui) $(7767)$$(1:)$$(1:)$,7768 (scheduler) $(7768)$$(1:)$$(1:)$,7769 (reactionner) $(7769)$$(1:)$$(1:)$,7770 (arbiter) $(7770)$$(1:)$$(1:)$,7771 (poller) $(7771)$$(1:)$$(1:)$,7772 (broker) $(7772)$$(1:)$$(1:)$,7773 (receiver) $(7773)$$(1:)$$(1:)$
