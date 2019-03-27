% podman-system-df(1) podman

## NAME
podman\-system\-df - Show podman disk usage

## SYNOPSIS
**podman system df** [*options*]

## DESCRIPTION
Show podman disk usage

## OPTIONS
**--format**=""

Pretty-print images using a Go template

**-v, --verbose**[=false]
Show detailed information on space usage

## EXAMPLE

$ podman system df
TYPE            TOTAL   ACTIVE   SIZE    RECLAIMABLE
Images          6       2        281MB   168MB (59%)
Containers      3       1        0B      0B (0%)
Local Volumes   1       1        22B     0B (0%)

$ podman system df -v
Images space usage:

REPOSITORY                 TAG      IMAGE ID       CREATED       SIZE     SHARED SIZE   UNQUE SIZE   CONTAINERS
docker.io/library/alpine   latest   5cb3aa00f899   2 weeks ago   5.79MB   0B            5.79MB       5

Containers space usage:

CONTAINER ID    IMAGE   COMMAND       LOCAL VOLUMES   SIZE     CREATED            STATUS       NAMES
073f7e62812d    5cb3    sleep 100     1               0B       About an hourago   exited       zen_joliot
3f19f5bba242    5cb3    sleep 100     0               5.52kB   4 hoursago         exited       pedantic_archimedes
8cd89bf645cc    5cb3    ls foodir     0               58B      2 hoursago         configured   agitated_hamilton
a1d948a4b61d    5cb3    ls foodir     0               12B      2 hoursago         exited       laughing_wing
eafe3e3c5bb3    5cb3    sleep 10000   0               72B      2 hoursago         running      priceless_liskov

Local Volumes space usage:

VOLUME NAME   LINKS   SIZE
data          1       0B

$ podman system df --format "{{.Type}}\t{{.Total}}"
Images          1
Containers      5
Local Volumes   1

## SEE ALSO
podman-system(1)

# HISTORY
March 2019, Originally compiled by Qi Wang (qiwan at redhat dot com)