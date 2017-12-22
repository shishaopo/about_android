


```
//当execute一个runnable时，当不足corePoolSize时，直接创建一个核心线程；

//当超过corePoolSize，workQueue没满时，放入线程队列等待；

//当worQueue放满，没达到maximumPoolSize时，创建一个非核心线程执行；

//当达到maximumPoolSize时，默认再次execute一个Runnable会直接抛出异常；

//默认情况非核心线程在空闲状态keepAliveTime时间后便会销毁；

//也可以设置核心线程超时销毁，默认核心线程不会被销毁；
    **线程池，核心线程数，最大线程数，超时时间，超时单位，线程队列，线程工厂** 
    ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory)​
```


 

 

系统自带线程池：

    //核心线程数和最大线程数一致为nThread，超时时间为0，即空闲状态立即销毁；线程队列为Integer.MAX_VALUE;
    1.Executors.newFixedThreadPool(int nThread);
    //没有核心线程数，最大线程数为Integer.MAX_VALUE，超时时间为60秒，即所有线程在空闲60秒后都会被销毁；
    2.Executors.newCachedThreadPool();
    //核心线程数和最大线程数都为1个，超时时间为0，线程队列为Integer.MAX_VALUE;
    3.Executors.newSingleThreadExecutor()；
    //特殊线程池，用于执行延时，周期性线程；核心线程为nThread，最大线程为Integer.MAX_VALUE，超时时间为10毫秒，​延时队列；
    4.Executors.newScheduledThreadPool(int nThread);
    //特殊线程池，类似于上面那个，不同的是只有一个线程；​
    5.Executors.newSingleThreadScheduledExecutor();

​

系统自带线程队列：

    1.ArrayBlockingQueue，//FIFO类型，生产者和消费者持有同一把锁，也就是说在存的时候不能取，取得时候不能存；

    2.LinkedBlockingQueue，//FIFO类型，生产者持有一把锁，消费者持有一把锁，当没有数据时消费者阻塞等待，当队列满时生产者阻塞等待；

    3.PriorityBlockingQueue，//按照Comparator顺序排序的队列或自然排序；

    4.SynchronousQueue，//特殊的队列，生产者和消费者交替进行；

    5.LinkedBlockingDeque，//双向队列，与LinkedBlockingQueue类似，不同的是生产者和消费者可以从双向放入或取出数据；

    6.DelayedQueue，//延时队列，元素必须实现Delayed接口，只有到期的元素才可以取出，可以用于定时任务；

    7.LinkedTransferQueue，//预占位模式？看懵逼了；

