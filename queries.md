# Questions on Networking and Docker Swarm

## 1. Networking

### CIDR Notation (/8, /16, /24, /32)

We often see IP ranges such as:

```text
10.0.0.0/8
10.0.0.0/16
10.0.0.0/24
10.0.0.0/32
```

### Questions

1. How was the count after the slash (`/8`, `/16`, `/24`, `/32`) decided?
2. Is there any networking standard or specification that defines these values?
3. How do we calculate the number of available IP addresses for a given CIDR range?
4. Why do some networks use `/8` while others use `/16` or `/24`?

### My Understanding

The number after the slash represents the number of bits reserved for the network portion of the IP address.

Examples:

| CIDR | Network Bits | Host Bits | Total IPs  |
| ---- | ------------ | --------- | ---------- |
| /8   | 8            | 24        | 16,777,216 |
| /16  | 16           | 16        | 65,536     |
| /24  | 24           | 8         | 256        |
| /32  | 32           | 0         | 1          |

Need to understand the standard and calculation in more detail.

---

## 2. Docker Swarm - Manager Node Failure

Assume we have multiple manager nodes.

### Questions

1. If we drain the current manager/admin node, it will not run any tasks. Correct?
2. If the active manager node goes down:

   * Will another reachable manager automatically become the leader?
   * How is the new leader selected?
3. What happens to the services/tasks running on the failed manager node?
4. Will those tasks automatically move to other worker nodes?
5. Is there any downtime during leader election?

---

## 3. Docker Swarm - Global Service

Assume we have 3 nodes and a service deployed in **Global Mode**.

### Current State

```text
Node-1 -> 1 Task
Node-2 -> 1 Task
Node-3 -> 1 Task
```

Total Tasks = 3

### Questions

#### Scenario 1: One Node Goes Down

If Node-2 goes down:

* Will the task from Node-2 be started on another node?
* Will the cluster still have only 2 tasks?
* Does Docker Swarm try to maintain one task per available node?

#### Scenario 2: Node is Drained

If we execute:

```bash
docker node update --availability drain <node>
```

Questions:

1. What happens to the task currently running on that node?
2. Will Docker Swarm stop the task and schedule it on another node?
3. In Global mode, will the total number of tasks decrease because the node is unavailable?
4. What happens when the drained node becomes active again?

Need to understand the behavior of Global Services during node failure and drain operations.
