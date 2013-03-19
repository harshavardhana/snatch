## Rdiffdir - Inference

Changes associated with ascii files and text - from relatively low to moderate
changes - patch apply time distribution is lower as the files and directories
increase.

Changes associated with binary files - considered as extreme cases - patch apply
time is relatively 9x longer as the amount of files and directories increase.

Even the relative 'delta' files gets bigger and bigger closing to the size of the
`new_directory`

  size(new_directory) - size(old_directory) >= size(delta_file)
         - Delta file is always smaller than or equal to the size of (new_directory)

But another thing to notice is that the individual bytes are slightly higher for
the old directory after the patch procedure when the size of `delta` file
 
  size(delta_file) > size(old_directory_sig) 
         - Usually this is the data point to look for

Now its hard to indicate if data is inconsistent for those individual bytes,
since at a directory level with million of files it would be hard to verify per
file. It could also be an indication that while copying large sets of data there
could be some sort of holes in some of those files at different offsets which
would have caused a marginal increase in their size consumption on disk.
Since rdiffdir is using 'rsync' algorithm internally it is safe to assume that
things are consistent :-)

--
Harsha




