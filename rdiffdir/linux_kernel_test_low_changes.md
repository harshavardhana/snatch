## Linux kernel rdiffdir test - low changes

```
# Total files
# find linux-3.8 -type f | wc -l
41520

# Total directories
# find linux-3.8 -type d | wc -l
2690

# Total size
# du -s linux-3.8
567768  linux-3.8

# Create signature file
# time rdiffdir sig linux-3.8 linux-3.8.sig

real    0m9.586s
user    0m8.137s
sys     0m1.147s

# du -s linux-3.8.sig
48512   linux-3.8.sig

# Create delta file
# time rdiffdir delta linux-3.8.sig linux-3.8.3 linux-3.8.3-3.8.delta

real    0m22.973s
user    0m20.470s
sys     0m1.736s

# du -s linux-3.8.3-3.8.delta
43332   linux-3.8.3-3.8.delta

# Patch old directory
# time rdiffdir patch linux-3.8 linux-3.8.3-3.8.delta

real    0m22.335s
user    0m14.813s
sys     0m5.912s

```
## Final result
```
# du -s linux-3.8
567804  linux-3.8
```