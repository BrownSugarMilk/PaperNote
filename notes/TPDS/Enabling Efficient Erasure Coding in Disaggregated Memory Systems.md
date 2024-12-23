# 1. What
Using exponential pipeline to overlap the latency of erasure coding and RDMA WIRTE so that the we can minimize the overhead of EC.
# 2. Why
Disaggregated memory systems are becoming more and more popular, and the performance of these systems is becoming critical for many AI application systems and data analysis systems. However, a large-scale memory pool also means easy to lose data.To enable fault tolerance, we introduce erasure coding (EC).
# 3. How
key insight: 
1. Making use of the locality of encoding.
2. Overlapping the latency of encoding and RDMA write.
3. Designing a exponential pipeline to considerate the head and tail latency of encoding and RDMA write.It is important to assume a suitable size of data block for encoding.Too big data block can not make good use of the locality of encoding, and too small data block will bring extra overhead because we will have more rounds of transmission.
optimizations:
1. Dispatch coding tasks for multi-cliet.
2. Optimization on small objects.
# 4. Bad
1. It has a bad performance when the data block is too small compared to replication strategy.
2. There is still a question with the spilt of pipeline and how the pipeline runs.

