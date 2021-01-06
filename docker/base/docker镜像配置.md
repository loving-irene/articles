直接编辑文件 `/etc/docker/daemon.json`

```
{
  "registry-mirrors": [
      "https://6gjvp3gc.mirror.aliyuncs.com"
      ]
}
```

如果有多个，全部放在数组里面，逗号隔开即可。