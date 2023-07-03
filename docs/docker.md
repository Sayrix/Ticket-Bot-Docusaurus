---
sidebar_position: 5
---

# 🐋 Docker Setup

Hellow fellow docker mates. So the setup for docker isn't terribly hard, matter of fact, might be easier than normal setup.

## Standard Setup
1. Please visit the [config doc](https://doc.ticket.pm/docs/config#general-configuration) (ignore the .env section) to setup your configuration file
2. Modify the locales if needed
3. Boot up the container
    * For Linux, run: `TOKEN=[REPLACE THIS WITH YOUR DISCORD TOKEN]; docker compose up -d`
    * For Windows, export env variable for `TOKEN`, then run `docker compose up -d`

## Updates
For any source and config updates, run: `docker compose up -d --build`

## Prisma Notice
Docker automatically uses postgresql as database and store your data in `./db-data` folder.