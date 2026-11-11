# event-signup

虚构的「活动报名与候补助手」。当前只有官方 Nest CLI 生成的默认应用，用来把本地环境和测试跑通。Prisma、数据模型和业务测试本周由自己写，不在这次初始化里。

## 版本

用当前 Node 主动 LTS 生成，并在该版本上跑通构建和默认测试：

| 项目 | 版本 |
| --- | --- |
| Node.js | 26.13.0（Active LTS，Lithium） |
| npm | 11.20.0 |
| Nest CLI | 12.0.12 |
| `@nestjs/core` | 12.4.2 |
| `@nestjs/common` | 12.4.2 |
| `@nestjs/platform-express` | 12.4.2 |
| TypeScript | 6.0.3 |

`.nvmrc` 固定为 `26.13.0`。`package.json` 的 `engines.node` 为 `>=20.11`（Nest CLI 的最低要求）。

## 启动 PostgreSQL

在 `event-signup/` 目录：

```bash
docker compose up -d
```

镜像是 `postgres:18`，端口只绑定 `127.0.0.1:5432`。开发默认账号：用户 `event_signup`，密码 `event_signup_dev`，数据库 `event_signup`。可用 `POSTGRES_USER`、`POSTGRES_PASSWORD`、`POSTGRES_DB` 覆盖。数据卷挂在 `/var/lib/postgresql`（PostgreSQL 18 官方镜像的数据目录）。

## 运行应用

```bash
cp .env.example .env
set -a && source .env && set +a
npm run start
```

应用监听 `127.0.0.1`，端口取环境变量 `PORT`，默认 `3000`。没有安装读取 `.env` 的库，需要自己把变量放进环境。开发监视用 `npm run start:dev`。

## 测试

```bash
npm run build
npm test
npm run test:e2e
```

默认单元测试和 e2e 测试不连接数据库。
