# find . -type f | wc -l
36791
# find . -type d | wc -l
2265

# time git init
Initialized empty Git repository in /root/linux-3.0.69/.git/

real    0m0.040s
user    0m0.000s
sys     0m0.004s

# time git add .

real    0m11.302s
user    0m8.551s
sys     0m2.125s

# time git commit -m "First commit"
real    0m16.931s
user    0m2.833s
sys     0m0.760s

# rsync -ah --progress linux-3.8.3/* linux-3.0.69
sent 474.71M bytes  received 799.61K bytes  28.82M bytes/sec
total size is 472.18M  speedup is 0.99

# time git status
real    0m0.603s
user    0m0.356s
sys     0m0.241s

# time git add .

real    0m11.086s
user    0m8.200s
sys     0m2.146s

# time git commit -m "Second commit"
real    0m12.778s
user    0m11.431s
sys     0m1.293s

# time git format-patch -1
0001-Second-commit.patch

real    0m18.058s
user    0m16.663s
sys     0m1.335s

# du -s 0001-Second-commit.patch 
251972  0001-Second-commit.patch

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

# git gc
Counting objects: 69398, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (44339/44339), done.
Writing objects: 100% (69398/69398), done.
Total 69398 (delta 24285), reused 69398 (delta 24285)

Enable gc on all repo's by default
# git config --global gc.auto 1
