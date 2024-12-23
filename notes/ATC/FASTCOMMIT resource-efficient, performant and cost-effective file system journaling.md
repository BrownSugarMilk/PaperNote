# 1. What
a hybrid journaling approach for Ext4 which performs logical journaling for simple and frequent file system modifications, while relying on JBD2 for more complex and rare modifications. 
# 2. Why
Background:
JBD2, the current physical journaling mechanism in Ext4 is bulky and resource-hungry. Specifically, in case of metadataheavy workloads, fsyncs issued by applications cause JBD2 to write copies of changed metadata blocks, incurring high byte and IO overhead. When storing data in Ext4 via NFS (a popular setup), the NFS protocol issues fsyncs for every file metadata update which further exacerbates the problem. In a simple multi-threaded mail-server workload, JBD2 consumed approximately 76% of the disk's write bandwidth. Higher byte and IO utilization of JBD2 results in reduced application throughput, higher wear-out of flash based media and increased performance provisioning costs in cloud-based storage services.
# 3. How
Solution:
a hybrid logical+physical journal that is resource-efficient and minimizes journal overhead.
key insights:
1. FCLog.reducing byte overhead viacompact logging
2. Reducing IO overhead via selective flushing.
3. Reducing context-switching delays via inline journaling.
4. Majority of its code has already been merged in the Linux kernel and is part of mainline Ext4
# 4. Bad
To do

