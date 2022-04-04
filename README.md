# mattermost-dex-openldap-patch
patch file for https://github.com/dexidp/dex/tree/master/server, making mattermost team edition works with dex v2.31.1 (implicitly openldap)

prereq:
- setup mattermost & openldap
- build and run dex, golang knowhow to understand this tiny patch.

notes:
- minimal modification to make mattermost team edition works with openldap via dex (simulating gitlab's oauth2 sso)
- inject openid scope to force backward compatilibity, making dex's oidc behave as though it is gitlab's oauth2, not to be confused with gitlab's oidc, oidc is enterprise feature in mattermost, not in team edition.
- gitlab id (crc32 of email): not sure about crc32 collision rate, crc32's uint32 is still within int64, so far so good.

steps:
- clone dexidp/dex
- cd into dex/server/ `git apply mattermost-dex-gitlab.patch` 
- cd back dex/ `make build` or `buildah bud` 🎉 there you have it, mattermost 🔗 dex 🔗 openldap
