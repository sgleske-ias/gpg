# Communicating securely with Sam Gleske

### Prerequisites

For Linux GPG is typically pre-installed.  For Mac, install [GPG
Suite][mac-gpg].

[mac-gpg]: https://gpgtools.org/

### Importing my GPG key

Before you can securely send me files and messages, you must first import my GPG
public key.

    curl -L https://raw.githubusercontent.com/sgleske-ias/gpg/master/sam_gleske.asc | gpg --import

Feel free to edit the trust of my key with:

    $ gpg --edit-key 'Sam Gleske'
    gpg> trust
    gpg> save

# Send encrypted files to Sam Gleske

The following encrypts a `file` to `file.asc`.  Share the encrypted `file.asc`
with me.

    gpg -ear 'Sam Gleske' file

For larger files, it's better to create a `file.gpg` with:

    gpg -er 'Sam Gleske' file

# Securely managing files from servers

This section is more of a personal note for me.

If files need to be downloaded onto my laptop, then I stream tar into GPG to
encrypt it.

    ssh HOSTNAME 'tar -cz file1 file2' | gpg -er 'Sam Gleske' -o file.tgz.gpg

To upload and extract the contents from local to a remote server the following
command can be run.

    gpg -d < file.tgz.gpg | ssh HOSTNAME 'tar -xz'
