```
# du -s linux-3.8.3-3.0.69.delta 
268472  linux-3.8.3-3.0.69.delta
# du -sh linux-3.8.3-3.0.69.delta 
263M    linux-3.8.3-3.0.69.delta
# du -s 0001-Second-commit.patch 
251972  0001-Second-commit.patch
# du -sh 0001-Second-commit.patch 
247M    0001-Second-commit.patch

# time rdiffdir patch linux-3.0.69 linux-3.8.3-3.0.69.delta

real    0m22.098s
user    0m15.425s
sys     0m5.897s

# time git am 0001-Second-commit.patch
Applying: Second commit

Auto packing the repository for optimum performance. You may also
run "git gc" manually. See "git help gc" for more information.
Counting objects: 69398, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (68624/68624), done.
Writing objects: 100% (69398/69398), done.
Total 69398 (delta 24285), reused 0 (delta 0)
Removing duplicate objects: 100% (256/256), done.

real    1m11.902s
user    1m23.321s
sys     0m9.019s

```
(In case of git 'git gc' here would have taken some time)
re-running the same scenario with a 'pre' 'git gc' executed earlier

```
# du -s linux-3.0.69
620100  linux-3.0.69

# time git am 0001-Second-commit.patch
Applying: Second commit
real    0m30.617s
user    0m12.383s
sys     0m3.039s

# time git reset --hard HEAD^
Checking out files: 100% (29965/29965), done.
HEAD is now at 0ab2ede First commit

real    0m33.453s
user    0m4.633s
sys     0m1.359s
```

-- Doing this traditional 'patch' and 'git add' way.
```
# time patch -p1 < 0001-Second-commit.patch 2>&1 > /dev/null

real    0m8.511s
user    0m4.560s
sys     0m3.637s

# time git commit -a -m "Second commit" 2>&1 >/dev/null
 
real    0m17.459s
user    0m15.615s
sys     0m1.661s

Patch generated after applying patch from 'rsync from 3.8.3 --> 3.0.69'
# du -s 0001-Second-commit.patch 
115960  0001-Second-commit.patch

Patch generated after rsync from 3.8.3 --> 3.0.69
# du -s ../0001-Second-commit.patch
251972  ../0001-Second-commit.patch
```
