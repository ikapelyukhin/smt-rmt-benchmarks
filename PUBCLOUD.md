# SMT vs. RMT benchmarks in Public Cloud

## Given:
* AWS `m4.large` server instances in `us-east-2`
* 200 client instances in `us-east-1`, 100 clients per server
* Public cloud setup for both SMT and RMT:
  * HA setup with 2 instances
  * Registration sharing and instance verification enabled
* SMT with stock configuration (`mpm_prefork` with `ServerLimit 150`)
* Varying RMT configurations (different number of `puma` workers and threads)
* Tracking system-wide 1 minute load average (`/proc/loadavg`) and memory usage (as `MemTotal - MemAvailable` from `/proc/meminfo`)

## CPU utilization

| Instance 1 | Instance 2 |
|-------|-------|
| SMT1, stock configuration | SMT2, stock configuration |
| [![stock_smt1_cpu]][stock_smt1_cpu] | [![stock_smt2_cpu]][stock_smt2_cpu] |
| RMT1, stock configuration (1w, 5t) |  RMT2, stock configuration (1w, 5t)
| [![1w_5t_rmt1_cpu]][1w_5t_rmt1_cpu] | [![1w_5t_rmt2_cpu]][1w_5t_rmt2_cpu] |
| RMT1, 5w, 30t | RMT2, 5w, 30t |
| [![5w_30t_rmt1_cpu]][5w_30t_rmt1_cpu] | [![5w_30t_rmt2_cpu]][5w_30t_rmt2_cpu] |
| RMT1, 10w, 15t | RMT2, 10w, 15t |
| [![10w_15t_rmt1_cpu]][10w_15t_rmt1_cpu] | [![10w_15t_rmt2_cpu]][10w_15t_rmt2_cpu] |
| RMT1, 30w, 5t | RMT2, 30w, 5t |
| [![30w_5t_rmt1_cpu]][30w_5t_rmt1_cpu] | [![30w_5t_rmt2_cpu]][30w_5t_rmt2_cpu] |

## Memory utilization

| Instance 1 | Instance 2 |
|-------|-------|
| SMT1, stock configuration | SMT2, stock configuration |
| [![stock_smt1_mem]][stock_smt1_mem] | [![stock_smt2_mem]][stock_smt2_mem] |
| RMT1, stock configuration (1w, 5t) |  RMT2, stock configuration (1w, 5t)
| [![1w_5t_rmt1_mem]][1w_5t_rmt1_mem] | [![1w_5t_rmt2_mem]][1w_5t_rmt2_mem] |
| RMT1, 5w, 30t | RMT2, 5w, 30t |
| [![5w_30t_rmt1_mem]][5w_30t_rmt1_mem] | [![5w_30t_rmt2_mem]][5w_30t_rmt2_mem] |
| RMT1, 10w, 15t | RMT2, 10w, 15t |
| [![10w_15t_rmt1_mem]][10w_15t_rmt1_mem] | [![10w_15t_rmt2_mem]][10w_15t_rmt2_mem] |
| RMT1, 30w, 5t | RMT2, 30w, 5t |
| [![30w_5t_rmt1_mem]][30w_5t_rmt1_mem] | [![30w_5t_rmt2_mem]][30w_5t_rmt2_mem] |

[stock_smt1_cpu]: ./images_pubcloud/stock/smt1_cpu.png
[stock_smt2_cpu]: ./images_pubcloud/stock/smt2_cpu.png
[stock_smt1_mem]: ./images_pubcloud/stock/smt1_mem.png
[stock_smt2_mem]: ./images_pubcloud/stock/smt2_mem.png

[1w_5t_rmt1_cpu]: ./images_pubcloud/1w_5t/rmt1_cpu.png
[1w_5t_rmt2_cpu]: ./images_pubcloud/1w_5t/rmt2_cpu.png
[1w_5t_rmt1_mem]: ./images_pubcloud/1w_5t/rmt1_mem.png
[1w_5t_rmt2_mem]: ./images_pubcloud/1w_5t/rmt2_mem.png

[5w_30t_rmt1_cpu]: ./images_pubcloud/5w_30t/rmt1_cpu.png
[5w_30t_rmt2_cpu]: ./images_pubcloud/5w_30t/rmt2_cpu.png
[5w_30t_rmt1_mem]: ./images_pubcloud/5w_30t/rmt1_mem.png
[5w_30t_rmt2_mem]: ./images_pubcloud/5w_30t/rmt2_mem.png

[10w_15t_rmt1_cpu]: ./images_pubcloud/10w_15t/rmt1_cpu.png
[10w_15t_rmt2_cpu]: ./images_pubcloud/10w_15t/rmt2_cpu.png
[10w_15t_rmt1_mem]: ./images_pubcloud/10w_15t/rmt1_mem.png
[10w_15t_rmt2_mem]: ./images_pubcloud/10w_15t/rmt2_mem.png

[30w_5t_rmt1_cpu]: ./images_pubcloud/30w_5t/rmt1_cpu.png
[30w_5t_rmt2_cpu]: ./images_pubcloud/30w_5t/rmt2_cpu.png
[30w_5t_rmt1_mem]: ./images_pubcloud/30w_5t/rmt1_mem.png
[30w_5t_rmt2_mem]: ./images_pubcloud/30w_5t/rmt2_mem.png
