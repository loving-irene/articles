### 将本地文件上传到远程

`scp local_file.zip root@remote_ip:/path/to/folder`

### 从远程服务器下载文件

`scp root@remote_ip:/path/to/files local/path`

### 多文件传输

-   从本地复制多个文件到远程
    `scp index.css json.js root@remote_ip:/path/to/folder`
-   从远程复制多个文件到本地
    `scp root@remote_ip:/path/to/folder/\{file1,file2}\`


### 复制整个文件夹

-   从本地复制到远程主机上
    `scp -v -r folder root@remote_ip:/path/to/folder`
-   从远程到本地（一般在当前本地当前文件夹执行命令）
-   `scp -r root@remote_ip:/path/to/folder .`