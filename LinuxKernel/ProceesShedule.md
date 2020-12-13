#Linux进程调度

## 查看进程的方法
```
┌──(kali㉿kali)-[~]
└─$ ps -aux                                                                                                                                1 ⨯
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.5 168116 11352 ?        Ss   Dec12   0:05 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    Dec12   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   Dec12   0:00 [rcu_gp]
root           4  0.0  0.0      0     0 ?        I<   Dec12   0:00 [rcu_par_gp]
root           6  0.0  0.0      0     0 ?        I<   Dec12   0:00 [kworker/0:0H-kblockd]
root           8  0.0  0.0      0     0 ?        I<   Dec12   0:00 [mm_percpu_wq]
root           9  0.0  0.0      0     0 ?        S    Dec12   0:00 [ksoftirqd/0]
root          10  0.0  0.0      0     0 ?        I    Dec12   0:02 [rcu_sched]
root          11  0.0  0.0      0     0 ?        S    Dec12   0:00 [migration/0]
root          13  0.0  0.0      0     0 ?        S    Dec12   0:00 [cpuhp/0]
root          14  0.0  0.0      0     0 ?        S    Dec12   0:00 [cpuhp/1]
root          15  0.0  0.0      0     0 ?        S    Dec12   0:00 [migration/1]
root          16  0.0  0.0      0     0 ?        S    Dec12   0:00 [ksoftirqd/1]
root          18  0.0  0.0      0     0 ?        I<   Dec12   0:00 [kworker/1:0H-kblockd]
root          19  0.0  0.0      0     0 ?        S    Dec12   0:00 [cpuhp/2]
root          20  0.0  0.0      0     0 ?        S    Dec12   0:00 [migration/2]
```

## Process  Descriptor进程描述符
* 进程描述符其实就是一个指向一个链表的指针，链表元素是task_struct structure。
* The task_struct structure的分配是基于slab分配器提供重用和作色功能之上。The task_struct structure is allocated via the slab allocator to provide object reuse and cache coloring.
```
```
