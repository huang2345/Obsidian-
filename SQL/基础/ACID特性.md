DBMS的事务都遵循四种特性，四种特性的首字母结合起来统称为**ACID**。
#### 原子性(Atomicity)
指：在事务结束时，其所包含的更新处理要么全部执行完成，要么全部不执行。从线程安全的角度上将，原子性能够保证数据不被竟态条件影响。
#### 一致性(Consistency)
事务中包含的处理要满足提前设置的约束，例如主键约束与`NOT NULL`约束。对于事务来说，违法的SQL会被回滚
#### 隔离性(Isolation)
保证不同事务之间互不干扰。该特性保证了事务之间不会互相嵌套，在事务未结束之前，它所做出的更改对其他事务而言是不可见的。
#### 持久性(Durability)
指：在事务结束后，DBMS能够保证该时间点的数据状态会被保存的特性。即使由于系统故障导致数据丢失，也能通过一些手段进行恢复。
保证持久性的方法，其中常见的就是将日志保存到硬盘中。
