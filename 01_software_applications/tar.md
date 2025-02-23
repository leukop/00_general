# tar 

# Switches

| Option | Description                                                                 |
| ------ | --------------------------------------------------------------------------- |
| `-c`   | Creates an archive                                                          |
| `-C`   | Choose working directory, which is source directory (may include several)   |
| `-H`   | Named symbolic links are followed (default symbolic links are not followed) |
| `-f`   | Names the archive by chosen name                                            |
| `-k`   | (`-x` is included) Don't overwrite files                                    |
| `-L`   | All symbolic links are followed and archived                                |
| `-r`   | Add to archive (`-f` is required)                                           |
| `-t`   | List articles of the archive to print output                                |
| `-u`   | Add to arhive, if files are newer than files in archive                     |
| `-v`   | Gives an additional information of task                                     |
| `-x`   | Extracts archive or searches from archive (can include multiple files)      |

# Examples
## Make backup from whole disk (from root folder)

Named as backup0.tar

```bash
 tar -cvf backup0.tar -C / . 
```

## Extract to 

Tar is extracted to the root folder

```bash
 tar -xvf backup0.tar -C /
```
## Copy directory

Copy /usr/user1/ and files and subdirectories to the directory /usr/user2

```bash
 tar -cvf - -C /usr/user1/ . | tar -xvf - -C /usr/user2/
```

## Backup all 30 days old an earlier modified files

```bash
 tar -cvf backup0.tar -C / `find / -mtime +30 -type f -print
```
