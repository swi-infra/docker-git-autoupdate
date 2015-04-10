= Git auto-updating container =

This image:
 - takes a GIT_URL, that it clones and expose as a volume (/git)
 - polls from the git remote periodically

Arguments:
 - GIT_URL: provided as this to git clone
 - POLLING_FREQ: polling frequency as given to cron, something like "*/5 * * * *", default to 5 minutes
 - SSH_KEY: can be used to provide an SSH key to authenticate against remote repository
            needs to be base64'd

In case URL is ssh (ssh:// or git@), the image will automatically accept the remote key.

Sample:
`docker run --rm -e GIT_URL=git@github.com:legatoproject/legato-docs.git -e SSH_KEY="$(cat ~/.ssh/id_rsa | base64)" --name legato-jenkins git-autoupdate`

