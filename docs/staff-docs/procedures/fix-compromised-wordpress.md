---
title: Restoring a Compromised WordPress Site
---

Users may request for their site to be restored after it is sorried. Rollbacks can only be performed with `root`.

1. If the user requests for their media to be backed up, `tar` the `/public_html/wp-content/uploads` folder and email it to them.
2. Run `reset-wpadmin username`. Note that the user will need to recover their password on the WordPress web admin dashboard later, or manually do so according to the instructions on the user-docs.
3. Run `restore-wpbackup target-username staff-username` as root/with `sudo`. Select a backup using best judgement. It is usually best to check for when files were last changed to estimate a compromise date.
4. Delete their `public_html` directory.
5. Rename the backed-up directory to `public_html` with `mv public_html_backup /* public_html`.
6. Run `wp core update` in their `public_html` directory.
7. Unsorry the account.