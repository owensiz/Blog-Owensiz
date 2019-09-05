# gitignore不生效
> 参考：https://blog.csdn.net/yingpaixiaochuan/article/details/53729446

## 结论
```
git rm -r --cached .
git add .
git commit -m 'update gitignore'
```

## 解释
### 问题
在最初没有添加gitignore的情况下，之前的文件已经被纳入版本管理，此时设置gitignore对之前的文件是无效的。

### 解决方式
先清除本地缓存。

## 命令分析
> 不应当去google，而是git rm --hel

以下是help内容，对部分相关命令做了中文注解。
```
NAME
       git-rm - Remove files from the working tree and from the index

SYNOPSIS
       git rm [-f | --force] [-n] [-r] [--cached] [--ignore-unmatch] [--quiet] [--] <file>...


DESCRIPTION
       Remove files from the index, or from the working tree and the index. git rm will not remove a file from just your working directory.
       (There is no option to remove a file only from the working tree and yet keep it in the index; use /bin/rm if you want to do that.)
       The files being removed have to be identical to the tip of the branch, and no updates to their contents can be staged in the index,
       though that default behavior can be overridden with the -f option. When --cached is given, the staged content has to match either the
       tip of the branch or the file on disk, allowing the file to be removed from just the index.

OPTIONS
       <file>...
           Files to remove. Fileglobs (e.g.  *.c) can be given to remove all matching files. If you want Git to expand file glob characters,
           you may need to shell-escape them. A leading directory name (e.g.  dir to remove dir/file1 and dir/file2) can be given to remove
           all files in the directory, and recursively all sub-directories, but this requires the -r option to be explicitly given.

       -f, --force
           Override the up-to-date check.

       -n, --dry-run
           Don't actually remove any file(s). Instead, just show if they exist in the index and would otherwise be removed by the command.

       -r
           Allow recursive removal when a leading directory name is given.
           
           允许递归recursive删除目录，即可以删除文件夹。
      --
           This option can be used to separate command-line options from the list of files, (useful when filenames might be mistaken for
           command-line options).

       --cached
           Use this option to unstage and remove paths only from the index. Working tree files, whether modified or not, will be left alone.

           从索引中删除文件，但是工作区文件仍是存在的。如果没有--cached后缀，就会同时从工作区和索引中删除文件。

       --ignore-unmatch
           Exit with a zero status even if no files matched.

       -q, --quiet
           git rm normally outputs one line (in the form of an rm command) for each file removed. This option suppresses that output.
```