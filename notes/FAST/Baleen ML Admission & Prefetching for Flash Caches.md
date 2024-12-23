# 1. What
Using machine learning to predict the admission and prefetching behavior of Baleen caches for flash caches.
# 2. Why
Flash caches have low write endurance.To avoid premature wearout, we must use admission policies to filter cache insertions and maximize the workload-reduction value of each flash write.
Why use machine learning to predict admission and prefetching behavior of Baleen caches for flash caches?
Actually ml does not have advantages compared to traditional admission policies because it is hard to design a ml model that can accurately predict the admission and prefetching behavior.What's more, a policy's decision is often affected by its past decisions, and can have synergistic or antagonistic effects on other parts of the system.
# 3. How
key insight: 
1. Carefully analyze the TCO of flash cache system.
2. Design a model named Episode to describe accesses.
3. Considerate the subproblems of admission and prefetching.
# 4. Bad
1. Using a testbed and a simulator to evaluate the performance of Baleen.So it is hard to say Baleen make sense.


