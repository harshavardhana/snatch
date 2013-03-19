
## Linux kernel rdiffdir test - high changes

```
# find linux-3.0.69 -type f | wc -l
36791

# find linux-3.0.69 -type d | wc -l
2265

# time rdiffdir sig linux-3.0.69 linux-3.0.69.sig

real    0m9.146s
user    0m7.278s
sys     0m1.047s

# time rdiffdir delta linux-3.0.69.sig linux-3.8.3 linux-3.8.3-3.0.69.delta

real    0m23.173s
user    0m20.539s
sys     0m1.891s

# du -s linux-3.8.3-3.0.69.delta 
268472  linux-3.8.3-3.0.69.delta
# du -s linux-3.0.69.sig 
42952   linux-3.0.69.sig

# du -s linux-3.0.69
506016  linux-3.0.69

# du -s linux-3.8.3
567804  linux-3.8.3

# time rdiffdir patch linux-3.0.69 linux-3.8.3-3.0.69.delta 

real    0m22.994s
user    0m15.468s
sys     0m5.847s
```
## Final result
```
# du -s linux-3.0.69
567820  linux-3.0.69
```