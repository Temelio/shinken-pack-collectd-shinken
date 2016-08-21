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

| Service name            | Description             | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|-------------------------|-------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Shinken $KEY$ processes | Check Shinken processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _shinken_processes         |
| Shinken $KEY$ listen    | Check listening ports   | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _shinken_listen            |

## Default values

    _shinken_processes                          arbiter $(shinken-arbiter)$$(1:2)$$(1:2)$,broker $(shinken-broker)$$(1:)$$(1:)$,poller $(shinken-poller)$$(1:)$$(1:)$,reactionner $(shinken-reactionner)$$(1:)$$(1:)$,receiver $(shinken-receiver)$$(1:)$$(1:)$,scheduler $(shinken-scheduler)$$(1:)$$(1:)$
    _shinken_listen                             webui $(7767)$$(1:)$$(1:)$,scheduler $(7768)$$(1:)$$(1:)$,reactionner $(7769)$$(1:)$$(1:)$,arbiter $(7770)$$(1:)$$(1:)$,poller $(7771)$$(1:)$$(1:)$,broker $(7772)$$(1:)$$(1:)$,receiver $(7773)$$(1:)$$(1:)$
