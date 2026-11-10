---
title: Privacy Policy
---
# Privacy Policy

PhotoCloud Frame Slideshow ("PhotoCloud", "the app") collects no analytics, sends no crash reports
and shows no ads. No server of mine ever sees your photos: the app reads them straight from the
sources you set up. This page lists every time PhotoCloud goes online and what it sends.

PhotoCloud is published by Martin Vysný, Finland. Everything else on this page happens on your
device or between your device and services you choose, and never reaches me. The one exception
is a city search for the weather overlay: the name you type, together with your IP address, as
every request on the internet carries it, reaches my city-search server. For that, I am the one
responsible.

## Your Photos

PhotoCloud shows photos from the sources you set up: your device, your network shares (Samba,
SFTP, DLNA, WebDAV, Nextcloud, ownCloud) and your cloud accounts (Dropbox, OneDrive, Box, Flickr,
Mega, iCloud shared albums). It connects to each source directly from your device, only to sign
in, list your folders and download your photos. It only reads them; it never changes, uploads or
deletes your photos. Each service you connect keeps its own privacy policy.

Downloaded photos and their thumbnails are cached on your device for quicker display. Android may
clear the cache at any time, and so may you, in Android's settings for the app.

{% comment %}
All of it is in streamsources.dat, in the app's files dir (StreamSource.kt). The manifest has
allowBackup="true" and no backup rules, so Auto Backup and device-to-device transfer include it.
Accepted 2026-11-07: Android 9+ encrypts the backup end to end with the screen lock, a restore
brings the sources back, and the user can turn backup off. Change this section if credentials
are ever excluded from backup.
{% endcomment %}
## Passwords and Sign-ins

For Samba, SFTP, Nextcloud, ownCloud, WebDAV and Mega, PhotoCloud remembers the username and
password you enter. For Dropbox, OneDrive, Box and Flickr it remembers the access token the
service gives it, never your password; for an iCloud shared album, the album's link. PhotoCloud
sends them only to that source, to sign in.

They are kept in the app's private storage on your device. Removing the source deletes them, and
so does uninstalling the app. If your device backs up app data, for example Android's backup to
your Google account, that backup includes them, as it does most apps' data.

{% comment %}
The city-search server: https://gitlab.com/mvysny/owm-city-finder, behind Caddy on the Aedict
box (../aedict/aedict-online, design/architecture.md). Neither logs requests, checked
2026-11-07; the server's own logs go with its container.
{% endcomment %}
## Weather

Only when you turn on the weather overlay:

- **City search.** The city name you type goes to PhotoCloud's city-search server, which I run,
  and which answers with the matching cities. The server keeps no log of the searches.
  PhotoCloud 1.17.0 and older send the name over plain, unencrypted HTTP; newer versions over
  HTTPS.
- **Forecast.** PhotoCloud fetches the forecast for the city you picked, and its weather icons,
  from OpenWeatherMap, which sees the city and your IP address. OpenWeatherMap's handling of that
  is covered by its [privacy policy](https://openweather.co.uk/privacy-policy).

## Purchases

PhotoCloud from Google Play sells its in-app purchases through Google Play. PhotoCloud learns only
which products you own, never your name, payment details or e-mail. Google's handling of your
payment data is covered by the [Google Privacy Policy](https://policies.google.com/privacy).

PhotoCloud from the Amazon Appstore is paid for up front, in Amazon's store and under Amazon's
privacy notice; the app checks nothing about the purchase online.

{% comment %}
Google's own disclosure for the Cast sender SDK (play-services-cast, googlePlay flavor only):
https://developers.google.com/cast/docs/android_sender/data_disclosure, read 2026-11-10. It logs
anonymized Cast device interactions, discovery and session events, device and app info, to
Google, encrypted, with no opt-out. Play's Data safety form declares it as App interactions.
{% endcomment %}
## Chromecast

In PhotoCloud from Google Play, when you cast, the slideshow streams from your device to the
Chromecast you pick, over your local network, through Google Play services. Google's casting
library also sends Google anonymized usage data, such as which Chromecasts were found and when a
cast started, to improve casting. The [Google Privacy Policy](https://policies.google.com/privacy)
covers casting.

## Everything Else Stays on Your Device

Your settings and your list of sources stay on your device. Sharing a photo hands it to the app
you pick. Showing a photo's location on a map opens your map app, and links open in your browser,
under those apps' and sites' own privacy policies.

## Your Rights

I keep no data about you: the city-search server answers and forgets. If you still have a
question about your data under the GDPR, write to
[support@android-photo-frame.eu](mailto:support@android-photo-frame.eu). You may
also complain to a data protection authority; in Finland that is the
[Data Protection Ombudsman](https://tietosuoja.fi/en). For anything else about the app, please use
the [issue tracker](https://github.com/mvysny/photocloud-frame-slideshow/issues).

## Google Drive and Google Photos in Older Versions

PhotoCloud 1.15.8 and older could also show photos from Google Drive and Google Photos; they
signed in with an access token, never your password, and only read your files and photos. Newer
versions use no Google API to access your data.

## Changes

When this policy changes, the new version is published on this page, with its date.

Last updated: 2026-11-10
