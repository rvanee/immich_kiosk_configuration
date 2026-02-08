# Getting Immich (Kiosk) to run on a QNAP NAS

This tiny page shows a simple way to configure [Immich](https://docs.immich.app/overview/quick-start/) with [Immich Kiosk](https://github.com/damongolding/immich-kiosk) using Portainer on a QNAP NAS. That combination offers functionality similar to what Kululu provides, including a live slideshow feature. Note that Immich offers QR creation for uploading multimedia files to an album out of the box.

## Installation

For detailed installation instructions, please refer to the official Immich documentation: [Install Immich with Portainer](https://docs.immich.app/install/portainer/). The following docker compose file already contains the Kiosk service and should be ready to go for Immich itself: [`immich_plus_kiosk.yml`](immich_plus_kiosk.yml).
Immich prefers an SSD for its postgres database location, which is why I used one in an empty slot on my NAS and created a static volume on it. Then I created a single shared folder named `immich` in this volume. This results in the following environment variables for this configuration:

- `UPLOAD_LOCATION=/share/Multimedia/immich`
- `DB_DATA_LOCATION=/share/immich/database`
- `IMMICH_VERSION=v2`
- `DB_PASSWORD=postgres`
- `DB_USERNAME=postgres`
- `DB_DATABASE_NAME=immich`

Once Immich is up and running, it is time for a bit of Immich Kiosk configuration:

1. Change the IP address in the `KIOSK_IMMICH_URL` environment variable in the docker compose file to your NAS's IP. A fixed IP is very helpful here (see your access point's documentation for how to arrange for that).
2. Create an Immich API key (click on the account button in the right upper corner of the Immich screen, then select Account Settings, then API keys). Add that key to the KIOSK_IMMICH_API_KEY environment variable in the docker compose file.
3. Update the stack.

I hope this helps.
