# Slurm tools

A collection of various Slurm tools used by USC CARC.

## Installation

These tools are either Bash or Python scripts, so you can simply download and run them as executables. If needed, install Bash or Python and change the file permissions to allow execute permission (e.g., `chmod 755 jobinfo`). If desired, add the executable files to a directory on `PATH`.

## Usage

### nodeinfo

Display node information by partition, CPU/GPU models, and state.

```
$ nodeinfo
-----------------------------------------------------------------------------------------------------------------------
Partition    Timelimit   CPU model     CPUs/ Memory(MB)/ GPU model          State  Nodes Nodelist
                                       node  node
------------ ----------- ------------- ----- ----------- ------------------ ------ ----- ------------------------------
debug        1:00:00     xeon-2640v4   20    128000      gpu:p100:2(S:0-1)  mix    1     e23-02
debug        1:00:00     xeon-2650v2   16    63400       (null)             idle   4     e05-[42,76,78,80]
debug        1:00:00     xeon-2640v3   16    63400       gpu:k40:2(S:0-1)   idle   1     e09-18
epyc-64      2-00:00:00  epyc-7513     64    256000      (null)             mix    1     a01-03
epyc-64      2-00:00:00  epyc-7542     64    256000      (null)             mix    8     b22-[01-08]
epyc-64      2-00:00:00  epyc-7513     64    256000      (null)             alloc  9     a01-[02,04,08,11,14,18],b01-[0
epyc-64      2-00:00:00  epyc-7513     64    256000      (null)             idle   51    a01-[05,07,09,12-13,16-17,19],
epyc-64      2-00:00:00  epyc-7542     64    256000      (null)             idle   24    b22-[09-32]
main*        2-00:00:00  xeon-4116     24    192000      (null)             drain  2     d05-39,d06-27
main*        2-00:00:00  xeon-2640v4   20    64000       (null)             drain  1     d17-38
main*        2-00:00:00  xeon-4116     24    94000+      (null)             mix    47    d05-[06-15,26-38,40-42],d06-[1
main*        2-00:00:00  xeon-2640v4   20    64000       (null)             mix    1     d18-34
main*        2-00:00:00  xeon-2640v3   16    63400       (null)             mix    1     e06-03
main*        2-00:00:00  xeon-2640v3   16    63400       gpu:k40:2(S:0-1)   mix    1     e07-12
main*        2-00:00:00  xeon-4116     24    94000       (null)             alloc  3     d11-[19,30,40]
main*        2-00:00:00  xeon-2640v3   16    63400       (null)             alloc  4     e13-[30-33]
main*        2-00:00:00  xeon-4116     24    94000       (null)             idle   28    d11-[09-11,13-18,20-24,26-29,3
main*        2-00:00:00  xeon-2640v4   20    63400+      (null)             idle   70    d17-[03-37],d18-[01-33,35],e16
main*        2-00:00:00  xeon-2640v3   16    63400       (null)             idle   76    e06-[01-02,04,06-22],e11-[26-2
main*        2-00:00:00  xeon-2640v3   16    63400       gpu:k40:2(S:0-1)   idle   16    e07-[01-11,13-16,18]
main*        2-00:00:00  xeon-2640v4   20    63400       gpu:k40:2(S:0-1)   idle   40    e16-[01-04,06-24],e17-[01-04,0
gpu          2-00:00:00  epyc-7513     64    256000      gpu:a100:2(S:0-7)  mix    7     a01-[01,06,15,20],b01-[01,06],
gpu          2-00:00:00  epyc-7282     32    256000      gpu:a40:2(S:0-1)   mix    7     a02-[01,06,15],a03-[06,15],a04
gpu          2-00:00:00  xeon-6130     32    191000      gpu:v100:2(S:0-1)  mix    28    d11-[02-04],d13-[02-11],d14-[0
gpu          2-00:00:00  xeon-2640v4   20    128000      gpu:p100:2(S:0-1)  mix    23    d23-[10,13-16],e21-[02-13,16],
gpu          2-00:00:00  xeon-6130     32    191000      gpu:v100:2(S:0-1)  alloc  1     d14-07
gpu          2-00:00:00  xeon-2640v4   20    128000      gpu:p100:2(S:0-1)  alloc  1     e23-01
gpu          2-00:00:00  epyc-7282     32    256000      gpu:a40:2(S:0-1)   idle   5     a02-20,a03-[01,20],a04-[01,20]
gpu          2-00:00:00  epyc-7513     64    256000      gpu:a100:2(S:0-7)  idle   5     b01-[15,20],b02-[06,15,20]
gpu          2-00:00:00  xeon-2640v4   20    128000      gpu:p100:2(S:0-1)  idle   14    e21-[01,14-15],e22-[02-12]
oneweek      7-00:00:00  xeon-2650v2   16    128000      (null)             drain  4     e02-[40-41,43,45]
oneweek      7-00:00:00  xeon-2650v2   16    128000+     (null)             mix    4     e02-[68-71]
oneweek      7-00:00:00  xeon-2650v2   16    128000+     (null)             alloc  21    e01-[46,48,52,60],e02-[48-55,7
oneweek      7-00:00:00  xeon-2640v3   16    63400       (null)             alloc  1     e06-24
oneweek      7-00:00:00  xeon-2650v2   16    128000+     (null)             idle   18    e01-[62,64,76],e02-[42,44,46,5
oneweek      7-00:00:00  xeon-2640v3   16    63400       (null)             idle   1     e10-12
largemem     7-00:00:00  epyc-7513     64    1024000     (null)             mix    2     a02-10,a04-10
largemem     7-00:00:00  epyc-7513     64    1024000     (null)             idle   2     a01-10,a03-10
```

### gpuinfo

Display GPU information for cluster.

```
$ gpuinfo -p gpu
------------------------------------------------
Slurm GPU information
------------------------------------------------
There are a total of 182 GPUs [up]
24 a100 gpus
24 a40 gpus
58 v100 gpus
76 p100 gpus
------------------------------------------------
There are a total of 182 GPUs [accessible]
24 a100 gpus
24 a40 gpus
58 v100 gpus
76 p100 gpus
------------------------------------------------
Usage by user:
ttrojan   [total: 8  (interactive: 0 )] a100: 8
------------------------------------------------
There are 174 GPUs available:
a100: 16 available
a40: 24 available
v100: 58 available
p100: 76 available
------------------------------------------------
```

### cqueue

Display job queue information.

```
$ cqueue -p largemem
-----------------------------------------------------------------------------------------
      Job ID       User     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ---------- ------------ ---------- -------- ----------- --------------------
7453378            jesp Run_do52bran   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7453379            jesp Run_do6b.job   largemem  PENDING        0:00 (QOSMaxMemoryPerUser
7473836         ttrojan sys/dashboar   largemem  RUNNING     2:42:28               a04-10
7449562            snet run_study_4x   largemem  RUNNING  2-23:17:10               a02-10
7453377            jesp Run_do51bran   largemem  RUNNING  2-17:02:07               a01-10
7470944          huy435    rfmixchr1   largemem  RUNNING    21:18:51        a02-10,a04-10
```

### myqueue

Display job queue information for user.

```
$ myqueue
------------------------------------------------------------------------------
      Job ID     Job Name  Partition    State     Elapsed     Nodelist(Reason)
------------ ------------ ---------- -------- ----------- --------------------
487418            sim2.sl       main  PENDING        0:00         (Dependency)
486794             sim.sl       main  RUNNING  1-12:13:20               d05-06
```

### jobhist

Display a compact history of user's jobs with basic job information.

```
$ jobhist
-----------------------------------------------------------------------------------------------
 Startdate        Job ID     Job Name  Partition      State     Elapsed Nodes CPUs  Memory GPUs
---------- ------------- ------------ ---------- ---------- ----------- ----- ---- ------- ----
2021-06-25        484933  debugsim.sl      debug     FAILED    00:00:05     1    4    30Gn 0
2021-06-25        484934  debugsim.sl      debug  COMPLETED    00:00:19     1    4    30Gn 0
2021-06-26        486288  interactive       main  COMPLETED    00:20:53     1   16     2Gc 0
2021-06-27        486290  interactive      debug    TIMEOUT    00:30:02     1   16     2Gc 0
2021-06-28        486624       sim.sl    oneweek  COMPLETED  3-00:30:22     1   16   120Gn 0
```

### jobinfo

Display detailed job information.

```
$ jobinfo 483699
Job ID               : 483699
Job name             : simdebug.sl
User                 : ttrojan
Account              : ttrojan_123
Working directory    : /project/ttrojan_123/sim
Cluster              : discovery
Partition            : debug
Nodes                : 2
Nodelist             : e05-[42,76]
Tasks                : 32
CPUs                 : 32
GPUs                 : 0
State                : COMPLETED
Exit code            : 0:0
Submit time          : 2021-08-26T14:56:23
Start time           : 2021-08-26T14:56:24
End time             : 2021-08-26T14:57:32
Wait time            : 00:00:01
Reserved walltime    : 00:10:00
Used walltime        : 00:01:08
Used CPU walltime    : 00:36:16
Used CPU time        : 00:35:18
% User (computation) : 96.35%
% System (I/O)       :  3.65%
CPU efficiency       : 97.37%
Reserved memory      : 61352M/node
Max memory used      : 64.74G (estimate)
Memory efficiency    : 54.03%
Max disk write       : 1.04M
Max disk read        : 14.42M
```

### myaccount

Display Slurm account information for user.

```
$ myaccount
----------------------------------------------------------------
Project accounts
----------------------------------------------------------------
User       Account         Cluster    Def Acct        QOS
---------- --------------- ---------- --------------- ----------
ttrojan    ttrojan_123     discovery  ttrojan_123     normal
ttrojan    ttrojan_123     condo      ttrojan_123     normal

-----------------------------------------------------
Discovery compute allocations
-----------------------------------------------------
Account          Limit              Usage
---------------  -----------------  -----------------
ttrojan_123      billing=12000000   billing=176254

-----------------------------------------------------
Allowed Endeavour partitions for ttrojan
-----------------------------------------------------
PartitionName=trojan AllowAccounts=ttrojan_123,hpcroot
PartitionName=shared AllowAccounts=ALL
```

### mypartitions

Display allowed partitions based on user's Slurm accounts.

```
$ mypartitions
-----------------------------------------------------
Allowed Endeavour partitions for ttrojan
-----------------------------------------------------
PartitionName=trojan AllowAccounts=ttrojan_123,hpcroot
PartitionName=shared AllowAccounts=ALL
```

## License

[MIT](LICENSE) (unless otherwise noted)
