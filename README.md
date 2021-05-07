# Distributed-Systems


## Principles/Properties to Consider: 


- Fault tolerance: ability to survive uncaught exceptions
- Data redundancy: never lose user data
- Scalability: Handling extra load should not require re-writing the app
- Test Coverage: a "decent" amount of code tested




### key concepts: 

- Entities communicate by message passing
- vertices, edges and diameter : n,m,d 
- message cost: number of message transmissions M
- entity workload Lnode = M/|V |, that is, the number of messages per entity, and the transmission load Llink = M/|E|, that is, the number of messages per link
- bit complexity: In this case, we may sometimes consider the bit-defined load functions: the entity bit-workload Lbnode = B/|V |, that is, the number of bits per entity, and the transmission bit-load Lblink = B/|E|, that is, the number of bits per link.
- ideal time complexity, T


| Type               | 32 - Bit | 64-Bit   |
| ------------------ | -------- | -------- |
| Int                | 12 bytes | 24 bytes |
| Float              | 16 bytes | 24 bytes |
| String             | 21 bytes | 37 bytes |
| Reference(pointer) | 8 bytes  | 8 bytes  |



Case Study: Back of the evolope calculation for distributed process mining algorithm

measures the transmission bit-load for a given process log containing n number of tasks. 


1. Exchange Task List: 

| Number of tasks | Size                                    |
| --------------- | --------------------------------------- |
| 12              | 37 bytes * 12 + 8 bytes *12 = 540 bytes |
| 50              | 2250 bytes                              |
| 100             | 4500 bytes                              |


2. Exchange Successor Matrix: 

| length of Matrix | size                                               |
| ---------------- | -------------------------------------------------- |
| 12 * 12 =        | 12 * 12 * 24 bytes + 8 bytes * 12*12 =  4608 bytes |
| 50 * 50 =        | 2500 * 24 + 2500 * 8 = 80,000 bytes                |
| 100 * 100 =      | 10^4 * 24 + 10^4*8 = 320000 bytes                  |


3. Exchange loop count: 

| length of Matrix | size                                               |
| ---------------- | -------------------------------------------------- |
| 12 * 12 =        | 12 * 12 * 24 bytes + 8 bytes * 12*12 =  4608 bytes |
| 50 * 50 =        | 2500 * 24 + 2500 * 8 = 80,000 bytes                |
| 100 * 100 =      | 10^4 * 24 + 10^4*8 = 320000 bytes                  |

4.   Effect of network configurations and process log size on number of messages passed and amount of data transferred over an internet connection. 
 
 | No. of tasks | No. of Nodes | No. of messages | Total Data transferred over network (in bytes) | Total Time taken for computation:<br><br>(assume 1000kb/sec connection) |
| ------------ | ------------ | --------------- | ---------------------------------------------- | ----------------------------------------------------------------------- |
| 12           | 3 nodes      | 2 * 3 = 6       | 9756 * 2 = 19512 /1024 = 19.05KB               |                                                                         |
| 12           | 5 nodes      | 4 * 3 = 12      | 9756 * 4 = 39024/1024 = 38.10KB                |                                                                         |
| 12           | 7 nodes      | 6*3 = 18        | 9756 * 6 = 58536/1024 = 57.164 KB              |                                                                         |
| 12           | 9 nodes      | 8* 3 = 24       | 9756 * 8 = 78048/1024 = 76.218 KB              |                                                                         |
| 50           | 3 nodes      | 2 * 3 = 6       | 162250 * 2 = 324500/1024 = 316.89 KB           |                                                                         |
| 50           | 5 nodes      | 4 * 3 = 12      | 162250 * 4 = 649000/1024 =                     |                                                                         |
| 50           | 7 nodes      | 6*3 = 18        | 162250 * 6 = 973500/1024 = 950.68 KB           |                                                                         |
| 50           | 9 nodes      | 8* 3 = 24       | 162250 * 8 = 1298000/1024 = 1267.57 KB         |                                                                         |
| 100          | 3 nodes      | 2 * 3 = 6       | 644500 * 2 = 1289000/1024 = 1258.78 KB         |                                                                         |
| 100          | 5 nodes      | 4 * 3 = 12      | 644500 * 4 = 2578000/1024 = 2517.57 KB         |                                                                         |
| 100          | 7 nodes      | 6*3 = 18        | 644500 * 6 = 3867000/1024 = 3776.36 KB         |                                                                         |
| 100          | 9 nodes      | 8* 4 = 32       | 644500 * 8 = 5156000/1024 = 5035.156 KB        |                                                                         |

5. 
| Number of tasks in Process: | TOTAL size ( adding 1,2,3)   in bytes |
| --------------------------- | ------------------------------------- |
| 12                          | 540 + 4608* 2 = 9756                  |
| 50                          | 2250 + 80,000*2 = 162250              |
| 100                         | 4500 + 320000*2 = 644500              |


----
### References

1. http://deeplearning.net/software/theano/tutorial/python-memory-management.html 
2. https://gist.github.com/jhclark/2845836
    [HD ACCESS] Read 1 MB sequentially from disk `20,000,000 ns` 
    [NETWORK] Send packet CA->Netherlands->CA 150,000,000 ns = 0.15sec

3. https://wondernetwork.com/pings/ 
 4. http://serverfault.com/questions/137348/how-much-network-latency-is-typical-for-east-west-coast-usa

5. A. Burattin and A. Sperduti, “PLG: A framework for the generation of business process models and their execution logs,” in Business Process Management Workshops - BPM 2010 International Workshops and Education Track, Hoboken, NJ, USA, September 13-15, 2010, Revised Selected Papers, ser. Lecture Notes in Business Information Processing, M. zur Muehlen and J. Su, Eds., vol. 66. Springer, 2010, pp. 214–219. [Online]. Available: http://dx.doi.org/10.1007/978-3-642-20511-8 20


