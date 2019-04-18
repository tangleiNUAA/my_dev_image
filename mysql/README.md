### 初始化需要的数据库及相应的表

```yml
volumes:
  - /my/own/datadir:/var/lib/mysql
```

`/my/own/datadir` 中添加相应的建库和建表的sql文件。

密码不建议在生产环境中使用这种简单密码。
