### 9. 并发控制：同步 (1)
> 要把一个算法并行化, 先画出它的计算图 (DAG).

> 生产者-消费者模型可以解决 99% 的并行问题.

条件变量与互斥锁高度相关.

当线程的条件不满足时, 执行 `wait()` 释放锁后进入睡眠;
当某个条件满足时, 调用 `signal()` 会随机唤醒一个线程, 或 `broadcast()` 唤醒所有线程

一个 "万能" 的生产者-消费者模板:
```
lock(mutex);
    while(!cond)
        wait(cv, mutex);
    assert(cond);
    // ... critical section ...
    broadcast(cv);
unlock(mutex);
```

`signal()` 时, 被唤醒的既可能是消费者, 也可能是生产者. 所以在一个线程被唤醒时应再次检查 `cond` 是否成立, 如果不成立就继续睡. 如果将上面代码的 `while` 换成 `if`, 则代码错误.

用条件变量实现并行，重要的就是**条件是什么**.