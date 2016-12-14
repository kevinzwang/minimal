# MINIMAL
A minimal zsh theme.

# Screenshot
![alt tag](http://i.imgur.com/IdVHRIU.png)

# Installation
[Zgen](https://github.com/tarjoilija/zgen):
```
zgen load subnixr/minimal
```

[Antigen](https://github.com/zsh-users/antigen):
```
antigen theme subnixr/minimal
```

Otherwise, you can always clone the repo and source `minimal.zsh`.

# Configuration
This theme can be customized before sourcing through variables:

- `MINIMAL_PROMPT`: enables prompt customization (default: active)
- `MINIMAL_RPROMPT`: enables right prompt (default: active)
- `MINIMAL_MAGIC_ENTER`: enables magic enter (default: active)
- `MINIMAL_USER_CHAR`: overrides normal user character (default: `λ`)
- `MINIMAL_INSERT_CHAR`: overrides insert mode character (default: `›`)
- `MINIMAL_NORMAL_CHAR`: overrrides normal mode character (default: `·`)
- `MINIMAL_OK_COLOR`: overrides color for succefull last command and git clean 
(default: `2`)
- `MINIMAL_PWD_LEN`: overrides number of working directory segments shown 
(default: `2`)
- `MINIMAL_PWD_CHAR_LEN`: overrides maximun length of pwd's segments before it 
is ellipsed (default: `10`, minimum: `4`)

To disable a feature, just set it to something other than `yes` before  sourcing.

Example:
```
MINIMAL_MAGIC_ENTER="I Don't want this"
source /path/to/minimal.zsh
```

# Description
A prompt with all features:
```
asd λ ›                                                 Workspace/sample master
```
On the left:

- `asd` is the `basename` of python's virtualenv currently in use. It won't be 
shown if not in use.
- `λ` is shown if you are a normal user. When root, a classic `#` will be shown
instead.
- `λ` will be `MINIMAL_OK_COLOR` if the last command exited successfully, 
otherwise will be red.
- `λ` will be underlined if you have jobs in background.
- `›` will be show if you are in insert (default) mode. If using vimode, `·` 
is shown when in normal mode.

On the right:

- The last `MINIMAL_PWD_LEN` segments of `pwd` are shown. If a segment is 
longer than `MINIMAL_PWD_CHAR_LEN` chars, it will be ellipsed. 
If you are near the root (eg: `/usr/bin`) the first slash will be shown.
- Git's current branch. It will be shown only if inside a git repo. It will be 
`MINIMAL_OK_COLOR` if clean, otherwise red.

# Magic Enter
You may miss some info from your prompt: magic enter to the rescue!
```
λ › [subnixr@lambda-arch:~] [14 (72)] [1&] [1]                                ~
Desktop    Downloads  GBA    pgadmin.log  Pictures  Templates  VirtualBox VMs
Documents  Dropbox    Music  Phone        Public    Videos     Workspace
```
If your buffer is empty, pressing enter will print some useful informations:

- Username, hostname and full `pwd`.
- Number of visible files, number of total files.
- Number of background jobs (if any).
- Exit code of last command (if exited with non-zero)
- Colored `ls` output, wrapped in `$PAGER` if output is longer than your view.
- Colored, brief, `git status` output, only if in a git repo

#  I HATE UTF-8!
No problem:
```
MINIMAL_USER_CHAR="$"
MINIMAL_INSERT_CHAR=">"
MINIMAL_NORMAL_CHAR="-"
source /path/to/minimal.zsh
```

