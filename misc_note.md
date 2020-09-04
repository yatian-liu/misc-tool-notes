## rclone tips
I aliased rclone to `'rclone --filter-from <filter_rules_file> --progress -uv'`. `--progress` shows real time progress during transfer. `-u` skips files that are newer on the destination. `-v` prints more information which are helpful to know the exact operations rclone will do. Filter pattern formats are given in <https://rclone.org/filtering/>.
I configured rclone to ignore Google Docs files.
General usage recipe:
1. Run `rclone check <gdrive:path> <local_path>` to see the differences between the cloud storage and local storage.
2. Check if there is anything that needs special attention. If so, modify the following steps as needed.
3. Run `rclone copy <gdrive:path> <local_path>` to copy the updates on the cloud to local storage; then, run `rclone copy <local_path> <gdrive:path>` to copy the local updates to the cloud.
4. If there are some unneeded files locally, remove them or put them into trash. If there are some unneeded files on the cloud, first use `rclone --dry-run sync <local_path> <gdrive:path>` to confirm the files to be removed, then run without `--dry-run` to actually remove these files.

## Other tips
Retain color when pipe the output of diff to less: `diff --color=always | less -r`. (Also applicable to git diff.) `--color=always` retains output color whenever diff's output is a pipe or a tty. `-r` makes less print control characters for color and other things directly.
`nvidia-smi [-l SEC]`: print the GPU status every SEC seconds.
`df -h`: show disk space usage in human readable way.
`du -sh (file | directory)`: show the size of the input file or directory.

