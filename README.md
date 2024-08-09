## Tools for executing performance related tests on an ppc64le node. 

### Fio : 
 
Usage:
```
wget https://raw.githubusercontent.com/kishen-v/ppc64le-toolkit/main/fio-3.37 -O /usr/local/bin/fio 
```
OR
``` 
curl -o /usr/local/bin/fio https://raw.githubusercontent.com/kishen-v/ppc64le-toolkit/main/fio-3.37
```
---
#### In-cluster debugging: Deploy the OS container with the latest fio installed by:
```
kubectl apply -f fio.yaml
kubectl exec --it fio -- bash
```
The fio binary is available in the $PATH and can be run inside the pod to determine read/write I/O performance. 

iostat with extended metrics with regards to the storage's read/write wait(r_await/w_await), queue length, svctm(service time) can be monitored to identify any spikes in the metrics. 

Additionally, iotop can help identify processes that are IO intensive. 


Reference guide for fio: https://medium.com/@krisiasty/nvme-storage-verification-and-benchmarking-49b026786297
