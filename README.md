# QuestarrNG for Unraid

This repository contains QuestarrNG's standalone Unraid Community Applications
profile and Docker template. Application source, releases, and GHCR images are
maintained in [QuestarrNG](https://github.com/snapetech/QuestarrNG).

QuestarrNG is a standalone PC game discovery and acquisition manager. It
supports IGDB metadata, download clients, and optional SeerrNG integration.

## Submit to Community Applications

Submit this repository URL in the [Unraid Community Apps portal](https://ca.unraid.net/submit):

`https://github.com/snapetech/questarrng-unraid`

The template and repository profile are kept here so the portal scans only
Unraid package files, rather than unrelated XML files in the application
source. Run Validate and Scan in the portal before submitting.

## Manual installation

Use the [QuestarrNG template XML](templates/questarrng.xml) with Unraid's Docker
template workflow. It installs `ghcr.io/snapetech-org/questarrng:main` and
configures persistent appdata, a game library, and downloads.

- Web UI: port `5000`
- Appdata: `/mnt/user/appdata/questarrng` mapped to `/app/data`
- Game library: `/mnt/user/media/games` mapped to `/data`
- Downloads: `/mnt/user/downloads` mapped to `/downloads`
- Default file ownership: `PUID=99`, `PGID=100`

Set the mapped paths and ownership to match your Unraid shares. Complete the
first-run account setup and configure IGDB credentials in QuestarrNG settings.
For downloads, make sure the configured client and QuestarrNG can see the same
paths; add a path mapping in QuestarrNG when the client reports a different
download directory. SeerrNG integration is optional.

## Source and support

- [QuestarrNG application source and documentation](https://github.com/snapetech/QuestarrNG)
- [QuestarrNG package and integration support](https://github.com/snapetech/QuestarrNG/issues)

This template repository is distributed under GPLv3; see [LICENSE](LICENSE).

## Local security scanning

Run `./scripts/security-scan-local.sh` to check whether Semgrep or Trivy applies to this repository; both skip the current documentation/package-only content. See [security-scanning.md](docs/security-scanning.md).
