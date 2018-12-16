## Runnable

**该函数没有返回值**

## Callable

**但是call()函数有返回值**

## Future

**Executor是Runnable和Callable的调度容器，Future就是对于具体的Runnable或者Callable任务的执行结果进行取消、查询是否完成、获取结果、设置结果操作**

## FutureTask

**因此FutureTask既是Future、Runnable，又是包装了Callable( 如果是Runnable最终也会被转换为Callable )， 它是这两者的合体**