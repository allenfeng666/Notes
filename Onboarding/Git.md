# Switching between HTTPS and SSH

If branch is using an app token, git remote -v will show https. If it’s using SSH, git@github.com. To switch.
- git remote remove origin
- git remote add origin git@github.com:MediaRails/marketplace-db.git
  - git fetch
- git branch -u origin/master