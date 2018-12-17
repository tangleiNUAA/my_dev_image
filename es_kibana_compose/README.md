### 为什么是 elasticsearch + kibana

这里不是去搭 ELK 的环境, 而是为了去熟悉熟悉 Elasticsearch6.3 以后的新特性, 而且个人来说更习惯 `kibana` 这个工具, 主要是使用其中的 `dev tool` 这个工具。

### 镜像来源

这里提供两个版本的 Elasticsearch image 来源, 官方给出的 Elasticsearch 镜像[Docker @ Elastic](https://www.docker.elastic.co/), 另一个是 [docker hub](https://hub.docker.com/_/elasticsearch) 中提供的。这两个里面的镜像相同, docker hub 中的 `DockerFile` 如下(以6.5.3为例):

```dockerfile
# Elasticsearch 6.5.3

# This image re-bundles the Docker image from the upstream provider, Elastic. 
FROM docker.elastic.co/elasticsearch/elasticsearch:6.5.3@sha256:e86539ef052ea90a725b58c4ac079530fb4b9ddc5f283dda6a4837c08ab60459

# The upstream image was built by:
#   https://github.com/elastic/elasticsearch-docker/tree/6.5.3

# For a full list of supported images and tags visit https://www.docker.elastic.co

# For Elasticsearch documentation visit https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

# See https://github.com/docker-library/official-images/pull/4916 for more details.
```

最终选择使用 docker hub 的镜像是因为可以使用阿里云的镜像加速器。

### x-pack 相关问题解决

关于 x-pack, 参考 [Elasticsearch6.2.2 X-Pack部署及使用详解](https://blog.csdn.net/laoyang360/article/details/79632579).

在 `elasticsearch`, `kibana` 的镜像中, 默认是开启了 x-pack 的所有功能, 由于 x-pack 的一部分特性还需要 license, 需要关闭这些特性, 参考文档: [Installing X-Pack](https://www.elastic.co/guide/en/x-pack/current/installing-xpack.html#xpack-enabling), 目前这边是把这些特性都关闭了(这个只拿来自己用用, 来熟悉 ES 用的), 暂时一股脑的把这些特性都关了, 后面再去看看怎么玩这个。 关闭掉的特性直接在 Compose 文件中可以看, 或者看下面的表也行:

配置项 | 配置的 功能/特性 描述
:-: | :-:
xpack.graph.enabled | 图形功能
xpack.ml.enabled | 机器学习功能
xpack.monitoring.enabled | 监控功能
xpack.reporting.enabled | 报告功能
xpack.security.enabled | 安全功能
xpack.watcher.enabled | 观察器

- 设置为 `false` 为关闭。
- PS: 一搜 `x-pack`, 全是怎么破解 `x-pack` 的帖子。。。
