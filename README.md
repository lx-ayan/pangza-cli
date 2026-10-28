# pangza

Pangza CLI：初始化空项目，并生成 `entity` / `mapper` / `service` / `controller`。

## 安装

```bash
npm i -g pangza
# 或
npx pangza init my-app
```

## init

```bash
pangza init my-app
pangza init my-app --modules=orm,auth,redis --db=mysql
```

交互勾选模块：`orm` / `auth` / `redis` / `log` / `schedule` / `encrypt` / `validate`（勾选后写入对应 `@pangza/*` 依赖）。  
`Mapper` / `MapperType` 从 `@pangza/orm` 导入；`Validate` 从 `@pangza/validate` 导入。  

勾选 `orm` / `redis` 时会写入 `EnableOrm()` / `EnableRedis()`。

`init` 时会请求 npm 查询 `@pangza/core` 最新版本，写入 `package.json` 为 `^x.y.z`（离线则回退内置版本）。  
强制指定版本：`PANGZA_VERSION=1.1.5 pangza init my-app`。

初始化还会生成：
- `application.yaml`：默认 `server.port: 5270`
- `tsconfig.json`：`@/*` → `src/*`

## generate（`g`）

在项目根目录执行：

```bash
pangza g controller user
pangza g service user
pangza g mapper user
pangza g entity user
pangza g all user
```

别名：`c|controller`、`s|service`、`m|mapper`、`e|entity`、`a|all`。  
覆盖已有文件：加 `--force`。

生成路径示例（`user`）：

```text
src/entity/user.ts
src/mapper/user.ts
src/service/user.ts
src/controller/user/index.ts   → /api/user
```
