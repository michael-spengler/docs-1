# Troubleshooting

Secure-rm will retry 3 times if an error occur to ensure the task succeeded. Should work on OS X, Linux \(almost, see below\), and Windows.

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
* especially on the vast majority of journaled file systems.



