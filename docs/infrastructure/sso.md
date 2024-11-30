# Single Sign-On (SSO)

SOWN uses [Authentik](https://goauthentik.io) for single sign-on (SSO), using OpenID Connect (OIDC), SAML2 or in some cases forward proxy authentication.

## Access

SSO is accessed at [sso.sown.org.uk](https://sso.sown.org.uk). You can log in with your SOWN account credentials or a University of Southampton iSolutions account.

This service is publicly accessible, but requires authentication.

## Permissions

Access to applications is configured using groups. Some applications will require you to be a member of a group in order to access it, whereas others will allow you access and set your permissions depending on the groups that you are a member of.

Group names must be in the format: `<app-name>:<role>`, e.g `kmicms:superuser`.

## Hosting

SSO is hosted on [`containers-secure`](./servers/containers.md#containers-secure-containers-3).

It is not currently managed by ansible.

There is an upgrade script that will automatically check for an update and deploy it when run:

```shell
root@containers-3:/docker/authentik# ./upgrade.py

SOWN SSO Upgrade Script
Current Version is Authentik 2024.10.2
The latest version is Release 2024.10.4, which was released on 2024-11-21T18:47:39Z

Please read the following release notes:

See https://docs.goauthentik.io/docs/releases/2024.10#fixed-in-2024104

What's Changed

...

Full Changelog: https://github.com/goauthentik/authentik/compare/version/2024.10.3...version/2024.10.4


Would you like to attempt an update? [y/n]: y
[+] Running 30/12
 ✔ worker Pulled                               37.6s
 ✔ server Pulled                               37.6s

[+] Running 4/4
 ✔ Container authentik-redis-1       Running   0.0s
 ✔ Container authentik-postgresql-1  Running   0.0s
 ✔ Container authentik-worker-1      Started   4.4s
 ✔ Container authentik-server-1      Started
```

Please note that it can take up to a minute after Authentik has restarted before it will be fully started and ready to log users in.