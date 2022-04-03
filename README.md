# dex-gitlab-patch
patch file for https://github.com/dexidp/dex/tree/master/server, making mattermost team edition works with dex (implicitly openldap)

notes:
- minimal modification to make mattermost team edition works with dex (so, openldap)
- forcing backward compatilibity of dex's oidc to behave as oauth2 by injecting openid scope
- gitlab id (crc32 of email): not sure of collision rate as crc32's uint32 is still within int64, so far so good.
