# SMT vs. RMT for regular use cases

## Registration

### Given
* AWS `m4.large` server instances in `us-east-2`
* 200 client instances in `us-east-1`
* SMT with stock configuration (`mpm_prefork` with `ServerLimit 150`)
* RMT configuration with 10 workers and 15 threads (which should be equivalent to the number of clients SMT can serve)
* Tracking system-wide 1 minute load average (`/proc/loadavg`) and memory usage (as `MemTotal - MemAvailable` from `/proc/meminfo`)

### Summary of results

* RMT's peak CPU utilization is 1/8th of SMT's
* RMT's average CPU utilization is 1/3th of SMT's
* RMT's memory utilization is 1/4th of SMT's
* Registration to RMT happens 3 times faster than to SMT

| SMT | RMT |
|-------|-------|
| [![no_regsharing_smt_reg_stats_cpu]][no_regsharing_smt_reg_stats_cpu] | [![no_regsharing_rmt_reg_stats_cpu]][no_regsharing_rmt_reg_stats_cpu] |
| [![no_regsharing_smt_reg_stats_mem]][no_regsharing_smt_reg_stats_mem] | [![no_regsharing_rmt_reg_stats_mem]][no_regsharing_rmt_reg_stats_mem] |

[no_regsharing_smt_reg_stats_cpu]: ./images_regular/no_regsharing/smt_reg_stats_cpu.png
[no_regsharing_rmt_reg_stats_cpu]: ./images_regular/no_regsharing/rmt_reg_stats_cpu.png
[no_regsharing_smt_reg_stats_mem]: ./images_regular/no_regsharing/smt_reg_stats_mem.png
[no_regsharing_rmt_reg_stats_mem]: ./images_regular/no_regsharing/rmt_reg_stats_mem.png

## Mirroring

### Given
* AWS `m4.large` server instances in `us-east-2`
* Same repositories enabled

### Summary of results
* RMT mirrors 3 times faster than SMT
* RMT's memory (150 MB difference) and CPU (0.6 vs 0.2) utilization are slightly higher than SMT's

| SMT | RMT |
|-------|-------|
| [![smt_mirror_cpu]][smt_mirror_cpu] | [![rmt_mirror_cpu]][rmt_mirror_cpu] |
| [![smt_mirror_mem]][smt_mirror_mem] | [![rmt_mirror_mem]][rmt_mirror_mem] |

[smt_mirror_cpu]: ./images_regular/smt_mirror_cpu.png
[smt_mirror_mem]: ./images_regular/smt_mirror_mem.png
[rmt_mirror_cpu]: ./images_regular/rmt_mirror_cpu.png
[rmt_mirror_mem]: ./images_regular/rmt_mirror_mem.png
