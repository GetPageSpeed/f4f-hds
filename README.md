# f4fhds

Nginx module for Adobe f4f format.

This module implements handling of HTTP Dynamic Streaming requests in the “/videoSeg1-Frag1” form — extracting the 
needed fragment from the videoSeg1.f4f file using the videoSeg1.f4x index file. This module is an alternative to the 
Adobe’s f4f module (HTTP Origin Module) for Apache.

It is open-source equivalent for commercial [ngx_http_f4f_module](http://nginx.org/en/docs/http/ngx_http_f4f_module.html#f4f_buffer_size)
module.

## Synopsis

```
location /video/ {
    f4fhds;
    ...
}
```

## Installation

### CentOS/RHEL 6, 7, 8

Pre-compiled module packages are available from [the GetPageSpeed repository](https://www.getpagespeed.com/redhat).

```
sudo yum -y install https://extras.getpagespeed.com/release-latest.rpm
sudo yum -y install nginx-module-f4fhds
```

### Compilation

```
./configure --add-module /my/path/to/src/f4f_hds
make
make install
```


## Limitations

* The assumption is that all files contain a single (first) segment, e.g. Seg1
* The files should reside in a local non-networked filesystem, due to use of `mmap(2)`.