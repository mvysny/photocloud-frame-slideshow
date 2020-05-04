# PhotoCloud

Android Digital Frame App for Tablet, Phone and Android TV

<a href="https://play.google.com/store/apps/details?id=sk.baka.photoframe"><img src="images/google-play-badge.png"  height="60px" /></a>

Just sit back and watch your photos with your family; convert your old Android tablet
to a digital photo frame; browse your cloud photos, hassle-free. The only digital frame
application which supports your own OwnCloud/NextCloud servers, with self-signed https certificates.

Able to retrieve and slideshow photos from the following sources:
- [OwnCloud](https://owncloud.org/)/[NextCloud](https://nextcloud.com/) server,
  even with self-signed https certificate
- [Dropbox](https://www.dropbox.com/)
- Local Gallery
- [Flickr](https://www.flickr.com/)
- [Google Drive](https://www.google.com/drive/)
- [Google Photos](https://photos.google.com/) (native support since 1.13.13)
- [Microsoft OneDrive](https://onedrive.live.com/)
- Windows Shares (Samba)
- [Mega](https://mega.nz/)
- SSH and SFTP
- DLNA/UPNP
- [Box: https://www.box.com/](https://www.box.com/) (only works on Android 5.0
  and higher because of [TLS 1.0 deprecation](https://developer.box.com/docs/tls-1))

Respects user's privacy: PhotoCloud is the only Android Digital Frame application
which supports your own personal OwnCloud/NextCloud servers (including self-signed
https certificates), your own SSH+SFTP servers, photos located on your Windows machines, etc.

Supported image types:
- bitmap: png, gif, bmp, jpg, jpeg, webp
- raw: crw, cr2, nef, raf, dng, mos, kdc, dcr (by default ignored since loading
  RAWs will generate huge network traffic; just enable raws in app's Settings)
- heif, heic. Starting from Android 9 P, HEIF/HEIC is supported natively. For Android Lollypop and higher, PhotoCloud includes an experimental HEIF/HEIC decoder library
  which you need to enable in Settings / Filters/Moments / Include HEIF/HEIC in Slideshow.

Please note:
This is just a digital frame / photo browser. It does not play any music,
does not create videos, does not replace your gallery app, it does simply one
thing - shows a slideshow of your photos - and does it simply and right.

Because of its nature, the application generates a very high network traffic -
please make sure you have WIFI enabled. The app has built-in network protection
and will abort the Slideshow if WIFI disconnects.

No annoying video commercials, simple to use. This application is at its infancy,
please let me know which features would you like me to implement, at
the [bug tracker page](https://github.com/mvysny/photocloud-frame-slideshow/issues).

## Screenshots

Streams | Slideshow | Browser
------------ | ------------- | -----
Welcome screen with the streams | A paused slideshow, showing EXIF and the location
where the photo was taken | You can browse the stream for photos and files
<a href="images/stream_cards.jpg"><img src="images/stream_cards.jpg" width="180"></a> | <a href="images/slideshow_paused.jpg"><img src="images/slideshow_paused.jpg" width="180"></a> | <a href="images/browser.jpg"><img src="images/browser.jpg" width="180"></a>

A short 3 minute introduction video:

[![PhotoCloud Introduction Video](https://img.youtube.com/vi/k0XDCYmSRuk/0.jpg)](http://www.youtube.com/watch?v=k0XDCYmSRuk "PhotoCloud Intro Video")


## Free Download At Google Play

Please [download the PhotoCloud application at Google Play](https://play.google.com/store/apps/details?id=sk.baka.photoframe) for free.

Endlessly cycles photos from any combination of the streams. You can play all
photos from the stream, or you can limit the stream to given list of directories (and subdirs).
You can also browse the files of the stream manually. The photos are automatically
cached locally; when offline, you can show slideshow from cached photos only.
Supports slideshowing photos from subdirectories.

Supports:

- ChromeCast (requires Android 4.4 and higher) - casts current slideshow to your TV from your phone
- Android TV - you can run this app straight on the TV and control it via the TV remote control

Also supports Daydream (Android 4.2 and higher only). Please see below for supported Android versions.

## Pricing

Pricing: free version shows a "please purchase" images once a while during the slideshow. There is an in-app payment which removes these images.
Another payment unlocks the "Daydream" functionality; this only works on Android 4.2 and higher, don't purchase if you have Android 4.1 or lower.

The in-app purchases are located in PhotoCloud Settings - simply touch the appropriate item to launch Google Play purchase process.
If the "Purchase" items are missing, it could be that the In-App Purchases API
is not available on your device (for example Amazon Fire tablet with Google Play). To verify that, please open the About Dialog and scroll to the bottom: in the "System stats" Section there will be
the "In-App Purchases API available:" line. If it says "false", then unfortunately the In-App Purchases API is not available on your device, which means two things:

* You can't unlock the features of this app from such device;
* Even if you use another device to purchase the features, these features still won't be unlocked on this device.

In such case please don't use in-app purchases.

# Privacy Policy

See [Privacy Policy](privacy_policy.html) for more details.

## Required permissions

- `INTERNET` - to download photos from cloud services
- `WRITE_EXTERNAL_STORAGE` - to workaround a bug in older Androids to cache photos
- `GET_ACCOUNTS` - Google Drive and App Billing requires this
- `BILLING` - In-app purchases
- `ACCESS_NETWORK_STATE` - allows PhotoCloud to monitor for WiFi and stop slideshow to avoid cellular network charges
- `RECEIVE_BOOT_COMPLETED` - to automatically start (if so configured)
- `ACCESS_WIFI_STATE` - to discover DLNA devices
- `CHANGE_WIFI_MULTICAST_STATE` - to discover DLNA devices
- `WAKE_LOCK` - to keep the phone awake during slideshow

# Devices Support

PhotoCloud works best with Android 5 onwards (API level 21). You can install newest PhotoCloud from Google Play.

## Half-supported Devices

In fact the PhotoCloud on Google Play also supports Android 4.4 and higher (API level 19 and higher),
however on Android 4 you may encounter the "SSL Handshake Aborted" issues (see FAQ for more details), therefore Android 5+ is recommended.

There is an older version of PhotoCloud published on Google Play which also
supports Android 4.1 (API level 16 and higher), but that older version is not maintained and provided as a "gesture of good will".

Unfortunately, Androids 4.0 and lower are not officially supported at the moment.
The reason for that is stated in [Issue #105](https://github.com/mvysny/photocloud-frame-slideshow/issues/105).

There is an unofficial build which targets Android 4.0.3 and higher (API level 15 and higher).
You can [get the APK from this link](https://www.baka.sk/images/photoframe-apk-googlePlay-release.apk),
however parts of the app requiring higher Android will simply crash. Such crashes will not be fixed.

## Unsupported Devices

It has been reported that [in-app payments on the Amazon Fire tablets with Google Play installed do not work](https://groups.google.com/forum/#!topic/photocloud-frame/YGF8EFPA3E4) -
the payment goes through but the annoying "Please Purchase" image stays. Please do not use PhotoCloud's in-app purchases if you plan to use the app on the Amazon Fire tablet.

# Links

* [Discussions forums](https://groups.google.com/forum/#!forum/photocloud-frame)
* [Bugs, issues, feature requests](https://github.com/mvysny/photocloud-frame-slideshow/issues)

# FAQ

Located here: [Frequently Asked Questions](faq.html)

