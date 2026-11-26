# Unraid Community Apps

## FUTO Backups

The [FUTO Backups template](templates/futo-backups.xml) installs the standalone container for backing up Unraid folders. You need access to the FUTO Backups beta and a FUTO account. See the [standalone setup guide](https://docs.futo.cloud/getting-started/standalone) for account setup, diagnostics, and recovery.

1. In the Unraid container form, set **Backup Source** to the share or folder you want to back up. Add a separate read-only path under `/target` for each additional source. To restore in place, the destination mapping needs write access.
2. Open **WebUI** from the container menu or visit `http://YOUR_UNRAID_IP:22676` from your LAN. Docker publishes the port on all host interfaces by default. To bind to a specific LAN address, enter your server's address and port in **Web UI Port**, for example `192.168.1.10:22676`.
3. Complete setup and save your recovery key outside the container. The `/data` mapping holds the database, settings, and encryption key. If you are migrating an existing install, use **Show more settings** to point **Appdata** at its existing `/data` host path and stop the old container before starting the replacement.
4. For local backup storage, open **Show more settings**, set **Local Backup Destination** to a writable folder or mounted disk, and select `/backends/local` in the app.

Anyone who can reach the Web UI before a FUTO account is connected can configure it. Keep the port on a trusted LAN and use a VPN or authenticated reverse proxy for remote access.

If a backup puts too much load on an SMB or NFS server, try lowering **File Walk Concurrency** from 64 to 16 under **Show more settings**.

## Community Apps submission

Once the template is on the public default branch, run **Validate** and **Scan** and submit it for review through [Unraid Community Apps](https://ca.unraid.net/submit/new).
