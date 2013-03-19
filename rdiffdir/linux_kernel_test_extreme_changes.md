
## Linux kernel rdiffdir test - extreme changes

```
# find linux-3.8.3 -type d | wc -l
2690
# find linux-3.8.3 -type f | wc -l
41520

# find linux-3.8.3-new/ -type f | wc -l
69405

# find linux-3.8.3-new/ -type d | wc -l
4081

# du -s linux-3.8.3*
567804  linux-3.8.3
6008320 linux-3.8.3-new
48512   linux-3.8.3.sig

# time rdiffdir sig linux-3.8.3 linux-3.8.3.sig

real    0m25.620s
user    0m13.730s
sys     0m2.129s

# time rdiffdir delta linux-3.8.3.sig linux-3.8.3-new linux-3.8.3comp-3.8.3.delta

real    2m58.529s
user    0m36.783s
sys     0m12.279s

# du -s linux-3.8.3comp-3.8.3.delta
5464044 linux-3.8.3comp-3.8.3.delta

# time rdiffdir patch linux-3.8.3 linux-3.8.3comp-3.8.3.delta

real    2m13.907s
user    0m34.879s
sys     0m15.967s
```

## Final result
```
# du -s linux-3.8.3
6038628 linux-3.8.3
```
