# File Permissions in Linux

## Project description

I work as a security professional at a large organization, mostly supporting the
research team. Part of my job is making sure the users on that team only have the
access they are supposed to have. For this task I went through the files and
subdirectories in the `projects` directory, checked the permissions that were set
on each one, and compared them to what the organization actually allows. Where the
permissions gave out more access than they should, I used Linux commands to fix
them so the system stayed secure and followed least privilege.

## Check file and directory details

The first thing I needed was a clear view of the current permissions, including any
hidden files. I ran this command from inside the `projects` directory:

```bash
ls -la
```

`ls` lists the contents of a directory. The `-l` flag prints the long format, which
is the part that shows the permission string, owner, and group for each item. The
`-a` flag includes hidden files, which on Linux are the ones whose names start with
a dot. Without `-a` I would have missed `.project_x.txt` completely.

Output:

```
drwx--x---  2 researcher2 research_team 4096 project_k.txt
-rw-rw-rw-  1 researcher2 research_team   46 project_k.txt
-rw-r-----  1 researcher2 research_team   46 project_m.txt
-rw-rw-r--  1 researcher2 research_team   46 project_r.txt
-rw-rw-r--  1 researcher2 research_team   46 project_t.txt
-rw--w----  1 researcher2 research_team   46 .project_x.txt
drwx--x---  2 researcher2 research_team 4096 drafts
```

## Describe the permissions string

I'll use `-rw-rw-r--` from `project_r.txt` as the example.

The string is 10 characters long. The first character is the file type and the
other nine describe the permissions in three groups of three.

- Character 1 (`-`): the file type. A dash means it is a regular file. A `d` here
  would mean it is a directory.
- Characters 2 to 4 (`rw-`): the permissions for the user, meaning the owner of the
  file. This owner can read and write the file but cannot execute it.
- Characters 5 to 7 (`rw-`): the permissions for the group. Everyone in the
  `research_team` group can read and write the file but cannot execute it.
- Characters 8 to 10 (`r--`): the permissions for others, meaning everyone else on
  the system. They can only read the file.

Within each group, `r` is read, `w` is write, and `x` is execute. A dash in any
position means that permission is not granted.

## Change file permissions

The organization does not allow "others" to have write access to any file. Looking
at the output from the check, `project_k.txt` has the string `-rw-rw-rw-`, so the
last group is `rw-`. That means others can write to it, which is not allowed. This
is the file I needed to fix.

I removed write access for others with this command:

```bash
chmod o-w project_k.txt
```

`chmod` changes the permissions on a file. The `o` targets others, the `-` removes
a permission, and the `w` is the write permission. After running it, the permissions
became `-rw-rw-r--`, so others can now only read the file.

## Change file permissions on a hidden file

The research team archived `.project_x.txt`, which is why it is hidden. The rule for
this file is that no one should be able to write to it, but the user and the group
should still be able to read it. Its current string was `-rw--w----`, which meant
the user could write, the group could only write, and no one could read it besides
what the user had.

I set the correct access with this command:

```bash
chmod u-w,g-w,g+r .project_x.txt
```

I made three changes in one command, separated by commas. `u-w` removes write from
the user, `g-w` removes write from the group, and `g+r` adds read for the group.
The user already had read, so I left that alone. After running it, the permissions
became `-r--r-----`, which gives read access to the user and the group and no write
access to anyone.

## Change directory permissions

Everything in the `projects` directory belongs to `researcher2`. Only that user
should be able to get into the `drafts` directory and see its contents. The current
string was `drwx--x---`, where the `d` shows it is a directory and the group still
had execute access, which on a directory is what lets you enter it. That group
access needed to go.

I removed it with this command:

```bash
chmod g-x drafts
```

`g` targets the group, `-x` removes execute, and on a directory execute is the
permission that allows a user to move into it. After running it, the permissions
became `drwx------`, so only `researcher2` can open the directory.

## Summary

I audited the `projects` directory using `ls -la` so I could see every file and
directory along with the hidden file `.project_x.txt`. Reading the 10-character
permission strings, I found three problems: `project_k.txt` let others write to it,
the archived hidden file `.project_x.txt` had the wrong read and write access, and
the `drafts` directory let the whole group in. I fixed each one with `chmod`,
removing write from others on `project_k.txt`, setting `.project_x.txt` to read only
for the user and group, and locking `drafts` down to `researcher2` alone. These
changes brought the directory back in line with the organization's least-privilege
policy and reduced the risk of unauthorized access to the research team's files.
