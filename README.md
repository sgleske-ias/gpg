# Encrypting messages and files

The following encrypts a `file` to `file.asc`.  Share the encrypted `file.asc`
with me.

    gpg -ear "Sam Gleske" file

For larger files, it's better to create a `file.gpg` with:

    gpg -er "Sam Gleske" file

# Securely managing files

If files need to be downloaded onto my laptop, then I stream tar into GPG to
encrypt it.

    ssh HOSTNAME 'tar -cz file1 file2' | gpg -er "Sam Gleske" -o file.tgz.gpg

To upload and extract the contents from local to a remote server the following
command can be run.

    gpg -d < file.tgz.gpg | ssh HOSTNAME 'tar -xz'
