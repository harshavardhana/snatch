
5 levels of sub-directory

# find . -type d | wc -l 
50001

# find . -type f | wc -l
10000

(File crawling)
==============================
Un-cached
# time ls -lR > /dev/null

real    0m23.888s
user    0m1.674s
sys     0m8.297s

Cached
# time ls -lR > /dev/null

real    0m1.129s
user    0m0.360s
sys     0m0.761s
==============================

(File md5sum 10k)
==============================
Un-cached
#  time find . -type f -exec md5sum {} > /dev/null \;

real    2m51.022s
user    0m2.705s
sys     0m18.423s

Cached

# time find . -type f -exec md5sum {} > /dev/null \;

real    0m14.291s
user    0m2.341s
sys     0m11.032s
==============================

(Clojure md5 10k files)
==============================
Un-cached

user=> (time (doseq [l (pmap #(md5file %) (walk-dir2 "/home/testdir"))]))
"Elapsed time: 160993.968907 msecs"
nil

i.e 2m40.993s

Cached
user=> (time (doseq [l (pmap #(md5file %) (walk-dir2 "/home/testdir"))]))
"Elapsed time: 2508.577522 msecs"
nil
user=>

i.e 25.085s
==============================

(Golang Filewalk)

==============================
Un-cached

# time go run filewalk.go /home/testdir

real    1m47.398s
user    1m21.357s
sys     0m18.066s

Cached

# time go run filewalk.go /home/testdir

real    0m55.559s
user    0m54.534s
sys     0m2.775s
==============================