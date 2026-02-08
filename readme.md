# Immich Kiosk Configuration

This tiny project provides a simple way to configure [Immich](https://docs.immich.app/overview/quick-start/) with [Immich Kiosk](https://github.com/damongolding/immich-kiosk) using Portainer on a QNAP NAS. It offers functionality similar to what Kululu provides, including a live slideshow feature. Note that Immich offers QR creation for uploading multimedia files to an album out of the box.

## Installation

For detailed installation instructions, please refer to the official Immich documentation: [Install Immich with Portainer](https://docs.immich.app/install/portainer/).
It took me some effort to get Immich with Immich Kiosk to run, which is why I decided to share my docker compose file: [`immich_plus_kiosk.yml`](immich_plus_kiosk.yml). Note that it still requires creating an API key (click on the account button in the right upper corner of the Immich screen, then select Account Settings, then API keys) and adding that to the KIOSK_IMMICH_API_KEY environment variable in the docker compose file.
Immich prefers an SSD for its postgres database location, which is why I used one in an empty slot on my NAS and created a static volume on it. Then I created a single shared folder with the name `immich`. This results in the following environment variables for this configuration:

- `UPLOAD_LOCATION=/share/Multimedia/immich`
- `DB_DATA_LOCATION=/share/immich/database`
- `IMMICH_VERSION=v2`
- `DB_PASSWORD=postgres`
- `DB_USERNAME=postgres`
- `DB_DATABASE_NAME=immich`

I hope this helps.
