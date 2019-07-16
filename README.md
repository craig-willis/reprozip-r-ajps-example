# reprozip-r-ajps-example
Example output from reprozip for a simple AJPS R replication package

The replication package:
* Uses R to run a single script
* Reads 3 CSV files
* Outputs a PDF

```
docker run --privileged -v `pwd`:/test -it craigwillis/reprozip bash
```

```
$ cd /test

$ reprozip trace Stokes_AJPS_Replication.R

$ reprozip pack ajps

$ reprounzip graph graphfile.dot ajps.rpz

$ dot -Tpng graphfile.dot -o graph-orig.png

$ reprounzip graph --regex-filter ^/site-library --regex-filter ^/usr/local/lib/R --regex-filter ^/usr/lib --regex-filter ^/lib --regex-filter ^/tmp --regex-filter ^/etc --regex-filter ^/sys --regex-filter ^/proc --regex-filter ^/dev --regex-filter ^/bin --regex-filter ^/usr/bin graphfile-pruned.dot ajps.rpz

$ dot -Tpng graphfile-pruned.dot -o graph-pruned.png
```
