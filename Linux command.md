# Linux command

## Files

**Disk usage of a directory**: sudo du -shc <directory>

Convert all the files to unix format:

```shell
find <folder> -name "*" | xargs dos2unix
```



## Port

```
netstat -aon | findstr <port-number>
```

- -a Displays all connections and listening ports.
- -o Displays owning process Id associated with each connection.
- -n Displays addresses and port numbers in numerical forms

