<p align="left"><img src="https://storage.googleapis.com/gopherizeme.appspot.com/gophers/9e5f19f595edf1bb1a51cb49e4eac9f935c1ec18.png" alt="Logo" height="200"></p> 

# ClamAV Prometheus Exporter

[![Go Report Card](https://goreportcard.com/badge/github.com/r3kzi/clamav-prometheus-exporter)](https://goreportcard.com/report/github.com/r3kzi/clamav-prometheus-exporter)
[![Apache V2 License](https://img.shields.io/badge/license-Apache%20V2-blue.svg)](https://github.com/r3kzi/clamav-prometheus-exporter/blob/master/LICENSE)

Exports metrics from [ClamAV](https://www.clamav.net/) as Prometheus metrics.

## Currently exposed metrics

- ClamAVStatus
- ClamAVThreadsLive
- ClamAVThreadsIdle
- ClamAVThreadsMax
- ClamAVMemHeap
- ClamAVMemMMap
- ClamAVMemUsed

``` 
# HELP clamav_mem_heap Shows heap memory usage
# TYPE clamav_mem_heap gauge
clamav_mem_heap 3.656
# HELP clamav_mem_mmap Shows mmap memory usage
# TYPE clamav_mem_mmap gauge
clamav_mem_mmap 0.129
# HELP clamav_mem_used Shows used memory usage
# TYPE clamav_mem_used gauge
clamav_mem_used 3.237
# HELP clamav_status Shows UP Status
# TYPE clamav_status counter
clamav_status 1
# HELP clamav_threads_idle Shows idle threads
# TYPE clamav_threads_idle counter
clamav_threads_idle 0
# HELP clamav_threads_live Shows live threads
# TYPE clamav_threads_live counter
clamav_threads_live 1
# HELP clamav_threads_max Shows max threads
# TYPE clamav_threads_max counter
clamav_threads_max 12
```

## Installation

ClamAV Prometheus Exporter requires a
[supported release of Go](https://golang.org/doc/devel/release.html#policy).

```shell script
$ go get -u github.com/r3kzi/clamav-prometheus-exporter
```

To find out where `clamav-prometheus-exporter` was installed you can run `$ go list -f {{.Target}} github.com/r3kzi/clamav-prometheus-exporter`. 

For `clamav-prometheus-exporter` to be used globally add that directory to the `$PATH` environment setting.

## Flags

[ClamAV](https://www.clamav.net/) server to connect to:

```shell script
Usage of clamav-prometheus-exporter:
  -clamav-address string
    	ClamAV address to use (default "localhost")
  -clamav-port int
    	ClamAV port to use (default 3310)
```

## Prometheus config

Just scrape this, e.g.:

```yaml
scrape_configs:
  - job_name: 'clamav-prometheus-exporter'
    static_configs:
      - targets: ['localhost:8080']
```

## Contributing

Pull requests are welcome.