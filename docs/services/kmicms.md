# KMICMS - Wagtail CMS

KMICMS is our [Wagtail](https://wagtail.org) content management system (CMS) for managing and serving the content on the [SOWN website](https://www.sown.org.uk).

The source code is available on GitHub: [sown/kmicms](https://github.com/sown/kmicms).

## Access

The admin interface is accessible at [https://www.sown.org.uk/admin](https://www.sown.org.uk/admin).

This service is publicly accessible, but requires authentication.

## Permissions

Wagtail has a flexible permissions model, but at a basic level we have two groups integrated with [SOWN SSO](./sso.md):

* `kmicms:staff` - grants permission to access Wagtail Admin.
* `kmicms:superuser` - grants superuser permissions.

These permissions are refreshed on login, so if you have additional permissions granted you may need to logout and log back in.

## Hosting

KMICMS is hosted on [`containers-prod`](../infrastructure/servers/containers.md#containers-prod-containers-2).

It is not currently managed by ansible.

## Staging

There is additionally a staging instance of KMICMS, for testing purposes. It is hosted on [`containers-dev`](../infrastructure/servers/containers.md#containers-dev-containers-1).

The staging site can be accessed at [https://sown-staging.containers-dev.sown.org.uk](https://sown-staging.containers-dev.sown.org.uk).

The permissions groups for the staging site are:

* `kmicms:staging:staff` - grants permission to access Wagtail Admin.
* `kmicms:staging:superuser` - grants superuser permissions.