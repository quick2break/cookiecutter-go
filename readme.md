
# cookiecutter-go

- boilerplate, go project starter.
- go 微服务项目目录生成工具.
- feature:
    - [x] `mono repo`: 支持创建 `mono repo`, git 项目根目录.
    - [x] `single app`: 支持创建 `single app`, 单个微服务目录.
    - [x] 可单个使用, 也可同时组合使用
- usage:
    - [x] 先创建 `mono-repo` 根目录
    - [x] 切换到 `app/` 下, 创建 `single app` 单个微服务目录.
- require:
    - [x] 基于 [cookiecutter](https://github.com/cookiecutter/cookiecutter) 实现.


## quickstart:

### install:

- https://cookiecutter.readthedocs.io/en/1.7.2/installation.html

```bash

# Mac OS X 安装 cookiecutter:
brew install cookiecutter

# Debian/Ubuntu:
sudo apt-get install cookiecutter

```








### how to use:


- [x] choice 1: create `mono-repo` + `single-app` with `gin`
- [x] choice 2: create `mono-repo` + `single-app` with `go-micro`
- [x] choice 3: create `library-repo`


#### 1. mono-repo + single-app with gin or go-micro

- 1.1 create mono repo:


> git repo / project root.
>
> 根据命令行参数提升, 逐步创建.

```bash

cd your-workspace/

# 在当前目录下, 创建mono repo 项目根目录: 使用 gin
cookiecutter https://github.com/better-go/cookiecutter-go.git --directory="mono-repo/gin"


# 在当前目录下, 创建mono repo 项目根目录: 使用 go-micro
cookiecutter https://github.com/better-go/cookiecutter-go.git --directory="mono-repo/go-micro"



```


- 1.2 create single app folder:

```bash

cd your-mono-repo-app-create-root/

# 在当前目录下, 创建微服务目录: 使用 gin
cookiecutter https://github.com/better-go/cookiecutter-go.git --directory="single-app/gin"

# 在当前目录下, 创建微服务目录: 使用 go-micro
cookiecutter https://github.com/better-go/cookiecutter-go.git --directory="single-app/go-micro"


```

#### 2. create library repo:

- `library-repo`

```bash

cd your-workspace/

# 在当前目录下, 创建mono repo 项目根目录:
cookiecutter https://github.com/better-go/cookiecutter-go.git --directory="library-repo"

```



## mono repo structure:


```bash

[~/cookiecutter-go/{{cookiecutter.repo_name}}] [master]

-> % tree . -L 5
.
├── Makefile
├── README.MD
├── app
│   ├── basic
│   │   ├── user
│   │   │   ├── auth
│   │   │   ├── identity
│   │   │   │   ├── Makefile
│   │   │   │   ├── cmd
│   │   │   │   ├── configs
│   │   │   │   ├── docs
│   │   │   │   ├── internal
│   │   │   │   ├── proto
│   │   │   │   └── readme.md
│   │   │   ├── permission
│   │   │   ├── readme.md
│   │   │   └── role
│   │   └── {{cookiecutter.basic_app_name}}
│   │       ├── cmd
│   │       │   └── main.go
│   │       ├── configs
│   │       │   └── configs.toml
│   │       ├── docs
│   │       ├── internal
│   │       │   ├── dao
│   │       │   ├── domain
│   │       │   └── service
│   │       └── proto
│   │           ├── api
│   │           ├── config
│   │           └── model
│   ├── biz
│   │   └── {{cookiecutter.biz_app_name}}
│   │       └── cmd
│   │           └── main.go
│   └── std
│       ├── Makefile
│       ├── proto
│       │   ├── config
│       │   │   └── config.proto
│       │   └── error
│       │       └── code.proto
│       └── readme.md
├── deploy
│   ├── local
│   │   └── Makefile
│   └── staging
│       └── Makefile
├── go.mod
├── infra
│   └── tool
├── pkg
├── script
└── tmp

39 directories, 15 files


```


## single app structure:


```bash

-> % tree -L 3 ./single-app/{{cookiecutter.app_name}}
./single-app/{{cookiecutter.app_name}}
├── cmd
│   └── main.go
├── configs
│   └── configs.toml
├── internal
│   └── dao
│       └── db
├── proto
│   └── api
│       └── api.go
└── readme.md

7 directories, 4 files


```


## cookiecutter docs:

- https://github.com/cookiecutter/cookiecutter
    - `项目脚手架`的脚手架

### install:

- https://cookiecutter.readthedocs.io/en/1.7.2/installation.html

### multi template:

- https://cookiecutter.readthedocs.io/en/1.7.2/advanced/directories.html
- 支持一个 git 下, 存放多个`目录创建模板`.

```bash

cookiecutter https://github.com/user/repo-name.git --directory="directory1-name"


```

### create a template:


- https://cookiecutter.readthedocs.io/en/1.7.2/first_steps.html
- 创建自己的项目目录模板结构


```bash
# 创建 template 文件夹: 命名格式如下(类似)
mkdir {{cookiecutter.directory_name}}
mkdir {{cookiecutter.repo_name}}

```

- `cookiecutter.json` 文件示例格式


```json
{
    "full_name": "Henry",
    "email": "xxx@gmail.com",
    "repo_name": "complexity",
    "project_short_description": "Refreshingly simple static site generator.",
    "release_date": "2013-07-10",
    "year": "2013",
    "version": "0.1.1"
}

```



## ref:

- https://github.com/audreyr/cookiecutter-pypackage
- https://github.com/pydanny/cookiecutter-django
    - https://github.com/pydanny/cookiecutter-django/blob/master/cookiecutter.json
- https://github.com/golang-standards/project-layout
- https://github.com/micro/micro
    - https://github.com/micro/micro/blob/master/client/cli/new/new.go
- https://github.com/adobe/go-starter
- https://github.com/gatsbyjs/gatsby-starter-default
