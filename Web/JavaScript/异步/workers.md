使用workers可以使程序在其他线程运行，workers给了开发者在Web中在不同线程中运行代码的能力。对于多线程代码，线程之间的资源争夺导致的线程锁等等问题。
workers为了避免这些问题，主代码与workers之间不能访问彼此的变量，workers和主代码运行在完全分离的环境中只能通过 `postMessage()` 来传递信息和 `addEventListener()` 来监听主代码传递的信息来通信。

