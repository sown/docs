# KMIBot

KMIBot is the bot that does things for the [SUWS / SOWN Discord](https://sown.org.uk/discord).

It is written in Python using discord.py, and the source code is available on GitHub: [`sown/kmibot`](https://github.com/sown/kmibot).

## Hosting

KMIBot is hosted on [`containers-dev`](../infrastructure/servers/containers.md#containers-dev-containers-1).

It is not currently managed by ansible.

## Backend and Web Interface

The bot has a REST API backend and database that is used to store stateful information. It is also available for users to log into to interface with the bot without using Discord.

It is available at [ferry.containers-dev.sown.org.uk](https://ferry.containers-dev.sown.org.uk).
