Sequence概念  
1. 通过顺序递增的序号来编号，管理进行交换的数据。  
2. 对事件的处理总是沿着序号逐个递增处理。  
3. 一个sequence用于标识某个特定事件处理者(ringbuffer,producer,consumer)的处理进度。  
4. 能消除多线程之间共享问题    

Sequencer概念  
1. 此接口有两个实现SingleProducerSequencer/MultiProducerSequencer  
2. 实现生产和消费之间正确传递数据  

Sequencer Barrier  
1. 保持ringbuffer,producer,consumer之间的平衡关系(唤醒/刮起) 
2. 定义是否可以处理事件的逻辑  

WaitStrategy拒绝策略：
- BusySpinWaitStrategy：最低效的阻塞策略，对cup消耗最小   
- SleepingWaitStrategy：适合用于异步日志类  
- YieldingWaitStrategy：无锁，性能最好  

EventProcessor  
- 主要事件循环处理事件中的Event拥有消费者的Sequence
- 实现类BatchEventProcessor包含类EventLoop的有效实现并且将回调到一个EventHandler接口的实现对象 


