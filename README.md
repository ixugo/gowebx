<p align="center">
    <img src="./logo.png#gh-light-mode-only" alt="Goyave Logo" width="550"/>
    <img src="./logo_dark.png#gh-dark-mode-only" alt="Goyave Logo" width="550"/>
</p>

<p align="center">
    <a href="https://github.com/ixugo/goweb/releases"><img src="https://img.shields.io/github/v/release/ixugo/goweb?include_prereleases" alt="Version"/></a>
    <a href="https://github.com/ixugo/goweb/blob/master/LICENSE.txt"><img src="https://img.shields.io/dub/l/vibe-d.svg" alt="License"/></a>
	<a href="https://gin-gonic.com"><img width=30px  src="https://avatars.githubusercontent.com/u/7894478?s=48&v=4" alt="GIN"/></a>
    <a href="https://gorm.io"><img width=70px src="https://gorm.io/gorm.svg" alt="GORM"/></a>

</p>

# 企业 REST API 模板工具

用于自动生成 CRUD 代码

## 设计参考

[Google API Design Guide](https://google-cloud.gitbook.io/api-design-guide)

## 安装

在终端执行

```bash
go install github.com/ixugo/gowebx@latest
go install mvdan.cc/gofumpt@latest
go install golang.org/x/tools/cmd/goimports
```

## 流程

1. clone goweb 模板，或初始化项目 go mod init project
2. 创建 model.go 文件，写入结构体
   ```go
    type User struct {
	    Name string // 昵称
	    Age  int64  //  年龄
    }
   ```
3. 执行 `gowebx -f ./model.go` 即可生成代码
4. 在项目中调用 registerUser 函数，将生成的代码注册到 gin 路由上。

## 功能

- [x] 生成 5 项常用 curd (增删改查,分页搜索)
- [ ] 生成 5 项常用 curd 的测试函数
- [ ] 生成 5 项常用 curd 的接口文档
- [ ] 支持分页查询中，前端传递排序方式
- [ ] 支持分页查询中，前端传递条件
- [ ] 生成 5 项常用的 redis 缓存代码

## 问题

> 为什么不读数据库生成代码?

平时在表中用 json 类型较多，读数据库没办法生成 json 结构体。
