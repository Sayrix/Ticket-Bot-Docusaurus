---
sidebar_position: 4
---

# 📙 Prisma Setup

## Introduction
Unfortunately, supporting multi-db can be a very complicated task since different types of database offers different features, leading to incompatibility. In order for me to support it, I have to minimize the database features I'm using and even this doesn't work well. So there we have this.

We only support 3 different database: Sqlite, MySQL, and PostgreSQL. For advanced usage, please refer to [Prisma Docs](https://www.prisma.io/docs/concepts/database-connectors).

## Installation
Unless you're looking to use MySQL or PostgreSQL, you do not need to use this. To use the other database, follow the steps below:
1. Copy the schema for the database you want to use below
2. Go to `prisma/schema.prisma` file and paste in the new schema
3. Go to `.env` and point the `DATABASE_URL` to your new database
4. Run `npm run setup` to setup the database

## Sqlite
This is our default option and works out-of-box without any addition work.

The schema for this database should be
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "sqlite"
  url      = env("DATABASE_URL")
}

model config {
  key   String  @id
  value String?
}

model tickets {
  id           Int     @id @default(autoincrement())
  channelid    String  @unique
  messageid    String  @unique
  category     String
  invited      String  @default("[]")
  reason       String
  creator      String
  createdat    BigInt
  claimedby    String?
  claimedat    BigInt?
  closedby     String?
  closedat     BigInt?
  closereason  String?
  transcript   String?
}
```

## MySQL
I do not recommend you select this type of database unless you're running the bot under a service provider that only offers this

The schema for this database should be
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
}

model config {
  key   String  @id
  value String? @db.Text
}

model tickets {
  id           Int     @id @default(autoincrement())
  channelid    String  @unique
  messageid    String  @unique
  category     String  @db.Text
  invited      String  @default("[]") @db.Text
  reason       String  @db.Text
  creator      String  @db.Text
  createdat    BigInt
  claimedby    String? @db.Text
  claimedat    BigInt?
  closedby     String? @db.Text
  closedat     BigInt?
  closereason  String? @db.Text
  transcript   String? @db.Text
}
```

## PostgreSQL
This is the best database, in my option, that the industry has to offer

The schema for this database should be
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model config {
  key   String  @id
  value String? @db.Text
}

model tickets {
  id           Int     @id @default(autoincrement())
  channelid    String  @unique
  messageid    String  @unique
  category     String  @db.Text
  invited      String  @default("[]") @db.Text
  reason       String  @db.Text
  creator      String  @db.Text
  createdat    BigInt
  claimedby    String? @db.Text
  claimedat    BigInt?
  closedby     String? @db.Text
  closedat     BigInt?
  closereason  String? @db.Text
  transcript   String? @db.Text
}
```