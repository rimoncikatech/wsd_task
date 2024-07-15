# Kubernetes Pod Restart Diagnosis

There are many possible reason why the java-app pod might be restarting at random

#### Memory Limits Exceeded:

The pod's memory limit is set to 1500Mi. If the application uses more memory than this limit, it will be terminated by the Kubernetes OOM (Out of Memory) killer.


### CPU Limits Exceeded:

The pod's CPU limit is set to 2000m (2 cores). If the application uses more CPU than this limit, it may be throttled, which can lead to performance issues or restarts.

The java-app container is currently using 3m, which is well below the limit. However, sudden spikes in CPU usage can still occur and cause issues.


#### Java Heap Size (Xmx) Issues:

The java-app has an Xmx setting of 1000M. This means the Java Virtual Machine (JVM) will use up to 1000Mi for the heap. If the application needs more heap memory, it will not be able to allocate it, potentially causing an OutOfMemoryError, leading to pod restarts.