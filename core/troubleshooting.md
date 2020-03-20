# Troubleshooting

Secure-rm will retry 3 times if an error occur to ensure the task succeeded. Should work on OS X, Linux \(almost, see below\), and Windows. \(See build status\)

## File systems

secure-rm will only work on file systems that overwrite blocks in place.

List of known file systems that will not work:

* ext3
* ext4
* AthFS – AtheOS
* OneFS
* ssd's at large
* reiserfs
* ...
* especially on the vast majority of

  journaled file systems.

## "WARN Too many open files, cannot ...:"

Don't worry, you've just submitted too much file for Node. The tool will retry 3 times to ensure the task succeeded. While you don't get an error, the tool can handle this issue.

If you really need to delete millions of file in one time, split the task \(e.g. ./your\_folder/a _then ./your\_folder/b_ ...\).

## Using Windows:

Be sure to use `".\path\file"` with double quotes since back-slashes will always be interpreted as escape characters, not path separators.

Another solution is to double the back-slashes like: `.\\path\\file`

Or if you can, use forward slashes!

