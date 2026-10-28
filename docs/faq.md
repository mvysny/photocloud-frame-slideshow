# FAQ (Frequently Asked Questions)

## ChromeCast icon not shown

When you start the slideshow, just touch the image, to pause the slideshow and to reveal more controls:

<a href="images/chromecast.jpg"><img src="images/chromecast.jpg" width="180px"></a>

The upper bar shows the following action buttons:

* The *Share button* which allows you to share the image to other apps
* The *Keep Screen* On button which leaves the screen on, or allows the screen to go off during the slideshow
* The *Set As Wallpaper* button which sets current photo as a background
* Finally, the *Chromecast* button which casts the slideshow to your chromecast device as well. Note that
  the Chromecast button is only visible when your phone actually sees the Chromecast device (the Chromecast device is on
  and the phone is connected to the same wifi as the Chromecast device itself). **Note**: the Chromecast connectivity
  and the Chromecast button visibility is completely in control of Google's code - the PhotoCloud app can not show/hide the button
  itself. If the button is hidden even though Chromecast is on, then there is nothing I can do.
  Please report a bug to Google guys.

The lower bar with the up-arrow will reveal the detailed EXIF data upon touch.

## Purchase not restored after reinstall

The purchase is tied to your Google Play account. Therefore, you can factory-wipe your phone and reinstall it
from scratch - as long as it's tied to your Google Play account the PhotoCloud should remain activated.

There are two separate one-time purchases possible for this app:

* The "Remove Nagging Screen" purchase which removes the "please purchase" nagging screen;
* The "Daydream" support purchase which allows Photocloud to be registered as a Daydream service on your phone.

The app should be automatically activated on all of your devices connected to the same Google account.
You definitely do not need to purchase the app separately per device; a single purchase from one device should unlock the app on all devices connected to that Google account.

Troubleshooting:

* The nagging screen is still shown even though I've made the purchase. Please make sure that you've purchased the "Remove Nagging Screen" purchase -
  purchasing the "Daydream" support won't make the nagging screen go away.
* If the nagging screen still shows, maybe the purchase hasn't been registered
  in PhotoCloud correctly - please try to reboot your phone.
* To verify the purchase, launch PhotoCloud and go into the `Settings / About` and scroll
  the About screen to the bottom:
  * The "In-App Purchases API available" should be set to
    "true" (if not, then Google Play is not available on your device)
  * "Unlocked Nagging Dialog" should be set to "true". If not, then Google
    Play is errorneously informing PhotoCloud that the purchase
    hasn't been completed. In this case the problem is in Google Play and/or Google internal systems,
    and you need to contact the Google guys to verify that the purchase went through.
    They take 30% off of PhotoCloud price, and thus they are paid to solve such issues -
    just go there and complain.
* If the "Unlocked Nagging Dialog" is "true" then PhotoCloud knows you've done the
  purchase and it is a bug if PhotoCloud still shows the nagging screen. In that case, please open
  a bug report in the [PhotoCloud Bug Tracker](https://github.com/mvysny/photocloud-frame-slideshow/issues).
* If the "Unlocked Nagging Dialog" is "false", please make sure that your user is still logged in into Google Play.
  For example, someone else could have logged in into your TV. Also, please make sure that
  the purchase shows in your Google Play's "Payments & subscriptions -> Budget & history" page.

## Getting Billing Error #5

This error:

> Billing error #5 Developer Error: Invalid argument provided to the API.
> This error can also indicate that the application was not correctly signed or properly setup for In-app Billing.
> in Google Play or does not have the necessary permissions in its manifest:
> java.lang.Throwable:Client is already in the process of connecting to billing service.

Currently there is no known solution, apart from making sure that you have the newest Google Play
installed on your phone.

## Slideshow from a subfolder

There are two ways to achieve this:

* One-time: just touch the Stream card, to reveal the *Browse* button; then use the Browser to locate the directory.
  Long-touch the directory and select the *Slideshow* option. That will start slideshow from that folder only.
* By default, choosing the *Slideshow* from the Stream card menu will slideshow all photos in that Stream.
  To limit the slideshow to only particular subfolder, *Browse* the Stream and locate the directory.
  Then, long-touch the directory and select the *Root Stream Here* option. From now on, this Stream slideshows
  will only show this folder. You can add additional folders; slideshow will then show photos from all of these folders.
  The folders will be listed in the Stream Card; just press the blue trash bin icon to remove those folders.

## Slideshow from multiple Streams

Just touch the Stream icon, located to the left corner of the Stream card.

The main screen listing four stream cards:

<a href="images/stream_cards.jpg"><img src="images/stream_cards.jpg" width="180px"></a>

You will be able to check multiple streams; then just touch the upper-right *Start Slideshow* button
to start slideshow from all of those streams.

## Adding more Streams

Open the main screen and touch the lower big white plus button. You will be able to add additional streams.

## Settings

Touch the upper-right cog wheel *Settings* button in the main screen. You can for example configure to
start slideshow from a Stream (or a combination of Streams)

* When your device boots (Android 9 and older);
* When your power cable is plugged in (Android 9 and older);

And others.

### Removing All Widgets From The Slideshow

To remove all widgets, please make sure all of the following settings are off:

* Settings / Widgets/HUD / Show Clock
* Settings / Widgets/HUD / Show Weather Forecast
* Settings / Widgets/HUD / Show EXIF in Slideshow
* Settings / Widgets/HUD / Show photo file name

See [Issue 119](https://github.com/mvysny/photocloud-frame-slideshow/issues/119) for more details.

### Photo Cache Explained

When launching a slideshow, a photo is downloaded from the server only if there's
no cached version or if the cached version is too old.
If the photo exists on the server, it is cached and displayed. If the photo no longer exists on the server,
it is removed from the cache.

So, the cache is updated/cleared only gradually, as the slideshow is running.

The definition of "too old" depends on the *Short-Lived Cache* setting:
* `Off` = a photo is old if it has been downloaded from the server 30 days ago or earlier.
* `On` = a photo is old if it has been downloaded from the server 1 day ago (yesterday) or earlier.

## Launching PhotoCloud at boot-up time

On Android 9 and older, PhotoCloud can start the slideshow when your device boots up, turning your device into a photo frame.
On Android 10 and newer it can't, see [below](#why-doesnt-photocloud-start-on-boot-on-android-10-and-newer).

On Android 9 and older this tends to be tricky, therefore please make sure to revisit all of the following
items:

1. In Settings / Slideshow, make sure that the "Auto-start Slideshow on Boot" is checked. Sometimes the Wifi may settle slowly, in that case please just check
also the "Delay auto-start Slideshow on Boot" setting.
2. You need to start the PhotoFrame app *at least once* by *touching* the PhotoCloud *launcher icon*, otherwise Android will not send the `RECEIVE_BOOT_COMPLETED` to the app
and the app will not start. This is a built-in Android security measurement and there's nothing PhotoCloud can do.
3. Please make sure that the `RECEIVE_BOOT_COMPLETED` permission is enabled for PhotoCloud and that your phone haven't accidentally removed that permission.
Typically you open the list of installed apps, find PhotoCloud and you can find the permissions there. However, this may differ on certain phones; please follow your phone's permission manager
tutorial to review the permissions.

### Why doesn't PhotoCloud start on boot on Android 10 and newer?

Android 10 and newer block apps from opening a screen while they run in the background, and an app
woken up by the boot runs in the background. The only way around it is the "Display over other apps"
permission. PhotoCloud never draws over other apps, and that permission is a favourite of scam apps, so
PhotoCloud doesn't ask for it. That's why the "Auto-start Slideshow on Boot" settings are greyed out
on Android 10 and newer.

Instead:

* After a restart, touch the *Slideshow* launcher icon (the second PhotoCloud icon). It starts the slideshow
  of the streams picked in Settings / Slideshow / "Auto-start Stream List" (all streams if none are picked).
  Photo frames are rarely restarted, so this is usually enough.
* Use PhotoCloud as the Android screen saver (Daydream) and let Android start it while charging:
  in Android's Settings / Display / Screen saver, pick PhotoCloud and "While charging". This needs
  the "Daydream" purchase. Some devices, Samsung and Google TV among them, hide or limit third-party screen savers.
* Use Tasker, which holds the "Display over other apps" permission itself,
  see [Launching PhotoCloud from Tasker](#launching-photocloud-from-tasker) below.

Starting the slideshow when the power cable is plugged in doesn't work on Android 10 and newer either, for the same
reason, so "Auto-start Slideshow on Power Connected" is greyed out there too; the screen saver and Tasker work there.
"Auto-stop Slideshow on Power Disconnected" works on every Android version. Please see
[Issue #176](https://github.com/mvysny/photocloud-frame-slideshow/issues/176) and
[Issue #185](https://github.com/mvysny/photocloud-frame-slideshow/issues/185) for more details.

## Launching PhotoCloud from Tasker

You can use the Tasker app to start the slideshow in any way you need: on boot-up, when the power cable is plugged in,
at a certain time of day, and so on.

1. In PhotoCloud, open Settings / Slideshow and pick the streams to show in "Auto-start Stream List".
   If you pick none, all streams are shown.
2. In Tasker, create a profile with the event you need, for example *Event / System / Device Boot*
   or *State / Power / Power* with the source *Any*.
3. Give the profile a task with the *App / Launch App* action and pick PhotoCloud's *Slideshow* app
   (the second PhotoCloud icon, `sk.baka.photoframe.frame.PhotoFrameActivity`).
4. When Tasker asks for the "Display over other apps" permission, grant it. Android 10 and newer
   only lets Tasker open an app from the background with this permission.

If the slideshow is already running in the background, *Launch App* brings it to the front.

NOTE: Don't use Tasker's *Send Intent* action with `sk.baka.photoframe.START_SLIDESHOW`, which older versions of this FAQ
recommended. It doesn't work on Android 10 and newer: PhotoCloud receives that intent in the background,
and Android doesn't allow it to open the slideshow from there.

## Memory & Crashes

Most often PhotoCloud crashes because Android doesn't give PhotoCloud enough memory to hold the images in. You can verify this, by going into `Settings` / `About`
and scrolling to the System Stats. On my phone, Android says that it gives PhotoCloud 512 MB of memory, however on low-cost/older phones this number might be
dramatically lower.

For a FullHD screen, the photo is shrank to 1920x1080 and since we have RGBA model which takes 4 bytes per every pixel, such a photo requires 1920x1080x4 = 8294400 bytes = whopping 8MB
of memory (RAWs take even more space since they don't support automatic shrink on load and are loaded as-they-are into memory, then resized).
PhotoCloud may at any time require to have 4 images loaded in memory: 

- one being shown currently,
- one being loaded from the stream in the background,
- two more images loaded as "previous" when you pause the slideshow

Therefore, PhotoCloud requires at least 32MB of memory only for images, plus the app itself uses a bit of memory for views and bookkeeping. Therefore, PhotoCloud requires
*at least as a bare minimum* 48MB of memory on 1080P/FullHD device; not to mention that the garbage collector is pretty shitty on Androids since it will fragment the internal memory and
at some point will fail to allocate 8MB of continuous space. The more memory PhotoCloud has, the better; PhotoCloud won't use all of the memory itself,
but more memory prevents fragmentation.

If your phone allocates less than 48MB memory to PhotoCloud, or if it so happens that PhotoCloud crashes randomly (probably because of memory fragmentation), you can work-around
this issue by letting PhotoCloud downscale the image more aggresively. By enabling the `Settings` / `Screen` / `Load with Half Resolution`, you will force PhotoCloud
to load the images at half of the resolution, taking up 4x less memory. For example, on a 1080p device, the images will be loaded at the resolution of 960x540,
which will cause them to take only 2073600 bytes (2MB). The disadvantage is that the images will not look as sharp, they will look a little blurred. But, I guess
it beats having PhotoCloud crashing all the time.

## Reporting crashes

PhotoCloud logs what it is doing, to a standard Android log. If PhotoCloud does not work properly or keeps crashing,
please open a bug report at [PhotoCloud Bug Tracker](https://github.com/mvysny/photocloud-frame-slideshow/issues).
During our conversation, I may ask for a log produced by PhotoCloud. Please follow the following steps to obtain the crash stack trace:

* [Enable debugging mode on your phone](https://developer.android.com/studio/debug/dev-options) or google for "android enable debug mode" for your phone
* Connect your phone via the USB cable with your computer
* One way to check the logs is the GUI way, by downloading the Android Studio and following [View logs with Logcat](https://developer.android.com/studio/debug/logcat)
  * [Download and install Android Studio](http://developer.android.com/sdk/index.html#download)
  * In the upper-right part there's a picker "Select Run/Debug configuration". You should see your device here. Select it.
  * [Open the logcat window](https://developer.android.com/studio/debug/logcat)
* Another way is the command-line way
  * [Download Android SDK](http://developer.android.com/sdk/index.html#download) and scroll down to the "Command line tools only" links
  * Run `adb devices` from command line - you should see your device
  * Run `adb logcat` to get the logcat

**Caution**: the log may contain sensitive information such as phone numbers you have dialed etc. Make sure to paste only the stack trace into the Github issue,
with sensitive info (file names) starred out. The most important part is the crash information itself, or an exception stack-trace as it is called. It looks like this:

```
E/AndroidRuntime: FATAL EXCEPTION: main
                  Process: sk.baka.photoframe, PID: 11590
                  java.lang.RuntimeException: Unable to instantiate application sk.baka.photoframe.App: java.lang.RuntimeException: Simulated
                      at android.app.LoadedApk.makeApplication(LoadedApk.java:823)
                      at android.app.ActivityThread.handleBindApplication(ActivityThread.java:5522)
                      at android.app.ActivityThread.-wrap2(ActivityThread.java)
                      at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1576)
                      at android.os.Handler.dispatchMessage(Handler.java:102)
                      at android.os.Looper.loop(Looper.java:241)
                      at android.app.ActivityThread.main(ActivityThread.java:6274)
                      at java.lang.reflect.Method.invoke(Native Method)
                      at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:886)
                      at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:776)
                   Caused by: java.lang.RuntimeException: Simulated
                      at sk.baka.photoframe.App.<init>(App.java:71)
                      at java.lang.Class.newInstance(Native Method)
                      at android.app.Instrumentation.newApplication(Instrumentation.java:1008)
                      at android.app.Instrumentation.newApplication(Instrumentation.java:993)
                      at android.app.LoadedApk.makeApplication(LoadedApk.java:817)
                      at android.app.ActivityThread.handleBindApplication(ActivityThread.java:5522) 
                      at android.app.ActivityThread.-wrap2(ActivityThread.java) 
                      at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1576) 
                      at android.os.Handler.dispatchMessage(Handler.java:102) 
                      at android.os.Looper.loop(Looper.java:241) 
                      at android.app.ActivityThread.main(ActivityThread.java:6274) 
                      at java.lang.reflect.Method.invoke(Native Method) 
                      at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:886) 
                      at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:776) 
```

You can easily find such exceptions simply by searching for `sk.baka.photoframe` throughout the log.

## Streams which are no longer supported

- [500px](https://500px.com/) because 500px shut down their API and the photos are no longer accessible.
  See [bug 90](https://github.com/mvysny/photocloud-frame-slideshow/issues/90) for more details.
- Instagram because Instagram shut down their API and the photos are no longer accessible. The new so-called [Instagram Graph API](https://developers.facebook.com/docs/instagram-api)
  is only available for Business or Creator accounts. See [bug 107](https://github.com/mvysny/photocloud-frame-slideshow/issues/107) for more details.
- [Google Photos](https://photos.google.com/) because since March 2025 Google's Photos Library API no longer lists the user's photos;
  an app only sees the photos it uploaded itself. Google's replacement, the Photos Picker, makes you pick at most 2000 photos
  by hand, the pick expires, and photos added to an album later never show up - useless for a photo frame.
  See [bug 134](https://github.com/mvysny/photocloud-frame-slideshow/issues/134) for more details.
- [Google Drive](https://www.google.com/drive/) because Google only lets PhotoCloud see the files explicitly shared with PhotoCloud,
  not your photos; reading the whole Drive needs a paid security assessment, renewed every year.
  PhotoCloud 1.15.8 and older can still connect to Google Drive, but never find any files nor folders.
  See [bug 199](https://github.com/mvysny/photocloud-frame-slideshow/issues/199) for more details.
  **Workaround**: sync your Google Drive photos to the device with Foldersync Pro, as described in this
  [PhotoCloud mailing list thread](https://groups.google.com/g/photocloud-frame/c/EcH-pL4qprE).

## Known Issues With Certain Types of Streams

- Flickr: PhotoCloud 1.16.0 and older show "This Photo Is No Longer Available" or skip photos in the
  slideshow ([bug 47](https://github.com/mvysny/photocloud-frame-slideshow/issues/47)); the next release fixes that.
  Since May 2025 Flickr lets apps download a free account's photos at 1024 px at most, so on a free account
  PhotoCloud shows them at that size; a Flickr Pro account gets the originals.

## Purchases Not Working On Certain TVs

PhotoCloud uses Google Play one-time subscriptions. On certain Smart TVs the Google Play
seems to be broken or doesn't work: I know of TCL Smart TVs not able to use subscriptions.
There has been also this [TCL Smart TV Subscription Error Report](https://support.google.com/googleplay/forum/AAAA8CVOtD8hM4T3dJwNE8/?hl=en-GB)
which suggests that the issue is not in PhotoCloud app itself, but rather in the Smart TV and/or
Google Play.

PhotoCloud should always report any payment error as an Android toast, and it should
also report "In-app purchase service is not available on this device :(" if Google Play
is non-functional or completely missing.

Please make sure that you have the newest PhotoCloud installed from Google Play,
since a newer version may contain in-app-purchases fixes and workarounds.

## Getting "SSL Handshake Aborted, sslv3 alert handshake failure"

This error comes from PhotoCloud 1.14.x running on Android 4.4, when it connects over https to a
server that accepts only TLS1.2 or newer: Android 4.4 doesn't enable TLS1.2 for apps.

PhotoCloud 1.15.0 and newer require Android 5.0, which enables TLS1.2 by default, so a supported
device no longer gets this error. On Android 4.4 the solution is to either use plain http to your
OwnCloud/NextCloud server, or use a newer device.

Please read more at [Nextcloud connecton failes with SSLv3 error](https://github.com/mvysny/photocloud-frame-slideshow/issues/123).

The full error message reads:

```
Failed to connect. Please make sure that the server is running, is accessible from your phone and your OwnCloud config.php's
trusted_domain list contains 'xxx'.
Error. java.io.IOException: list / failed: -1: javax.net.ssl.SSLHandshakeException: javax.net.ssl.SSLProtocolException: SSL
handshake aborted: ssl=0x6cb36970: Failure in SSL library, usually a protocol error.
error 14077410:SSL routines: SSL23_GET_SERVER_HELLO:sslv3 alert handshake failure (external/openssl/ssl/s23_clnt.c:741
0x6a45d74:0x00000000)
```

You can get the same exception in the Weather widget: "Err SSLHandshakeException Handshake Failed".
This exception started to manifest in roughly July 2023, when OpenWeatherMap
(the source of weather data for PhotoCloud) dropped support for TLS1.1, which hit Android 4.4
devices. On Android 5.0 and newer, the weather's handshake failure is most likely the
"Trust anchor" one below, which a newer PhotoCloud fixes.

Also see the [Discussion Thread](https://groups.google.com/g/photocloud-frame/c/ERYc2cXnx2I) for more details.

### "Trust anchor for certification path not found"

A different handshake failure hits devices that do support TLS1.2: the device doesn't trust the
certificate authority that signed the server's certificate. The error usually reads
`SSLHandshakeException: java.security.cert.CertPathValidatorException: Trust anchor for certification path not found`.

The usual culprit is [Let's Encrypt](https://letsencrypt.org/), which signs the weather icons from
openweathermap.org, iCloud web albums and many self-hosted Nextcloud/OwnCloud servers. Older
Android versions (and some vendor forks such as Fire OS) don't know Let's Encrypt's root
certificates ISRG Root X1 and X2, and the old cross-signature that used to cover them has expired.

PhotoCloud versions newer than 1.15.8 bundle both Let's Encrypt roots and trust them on every
Android version, so please upgrade. If the error persists, please
[open an issue](https://github.com/mvysny/photocloud-frame-slideshow/issues) with the full error message.

## Nextcloud or ownCloud not connecting

- **"protocol SSLv3 is not supported"**: PhotoCloud 1.16.0 and older can't connect to a Nextcloud
  or ownCloud server over https on Android 8 and newer, whatever its certificate. The next release
  fixes that; until then, only plain http works.
- **The slideshow freezes when the server stops answering**: PhotoCloud 1.16.0 and older wait for
  it forever. The next release gives up after a minute and goes on with the cached photos.
- **Two-factor authentication**: log in with an app password, which you create in your account's
  security settings on the server.
- **ownCloud Infinite Scale (oCIS)** lets only its own apps log in by default. PhotoCloud logs in
  with a user name and password, which oCIS accepts once its admin sets
  `PROXY_ENABLE_BASIC_AUTH=true`.
- **A self-signed certificate**: PhotoCloud shows the certificate and asks whether to trust it.
  From the next release on, it trusts it for that one server only.

The next release also shows photos from any WebDAV server, such as a Synology or QNAP NAS: add a
"Nextcloud / ownCloud / WebDAV" stream with the URL of the folder. For Synology, see
[Synology NAS & Synology Photos](#synology-nas--synology-photos).

## Getting JSchException: failed to send channel request’

This happens when you try to access SSH (secure shell, a secure way to send commands to remote machine) which has SFTP disabled.
SFTP stands for Secure File Transfer Protocol, works over SSH, and without it, SSH can not transfer files.
Please make sure SFTP is enabled on your server.

## Synology NAS & Synology Photos

Synology offers no public API for Synology Photos, but Synology Photos keeps its photos in ordinary
folders on the NAS, and PhotoCloud can show them straight from those folders.

### Over WebDAV (the release after 1.16.0)

1. On the NAS, open **Package Center**, install **WebDAV Server**, open it and enable **HTTPS**
   (port 5006). HTTP (port 5005) works too, but sends your password unencrypted.
2. Make sure the DSM user PhotoCloud logs in as can read the folder. PhotoCloud never changes
   anything, so a separate user with read-only access is enough.
3. In PhotoCloud, add a **Nextcloud / ownCloud / WebDAV** stream with the URL of the folder and that
   user's name and password:
   - Synology Photos **Shared Space**: `https://<NAS address>:5006/photo`
   - Synology Photos **Personal Space**: `https://<NAS address>:5006/home/Photos`
   - any subfolder, e.g. `https://192.168.1.10:5006/photo/2024`
4. The NAS has a self-signed certificate by default: PhotoCloud shows it and asks whether to trust
   it, and then trusts it for that one server only.

PhotoCloud sees folders, not Synology Photos albums: an album lives only in Synology Photos' own
database, which WebDAV doesn't expose. Keep each album in its own folder to get the same result.

### Over Samba or SFTP

PhotoCloud 1.16.0 and older can read the same folders over Samba (DSM: Control Panel → File
Services → SMB) or SFTP (Control Panel → File Services → FTP → SFTP).

### Synology & DLNA

Some users received "Synology DS218j DS218j 6.2-25556 does not provide content directory and is thus not browsable for photos"
when accessing Synology Diskstation via DLNA. The problem is that Synology doesn't offer the `urn:schemas-upnp-org:service:ContentDirectory:*`
DLNA service which is required for photo browsing. If you know another DLNA way of retrieving photos, please [open a ticket](https://github.com/mvysny/photocloud-frame-slideshow/issues)
and let me know.

Known workaround is to access your photos over SSH instead; please make sure to also enable SFTP as discussed above.

## Gallery not working

The "Folders" and "Moments" feature uses an internal filtering/photo retrieval mechanism of
Android which is very complicated and hard to call correctly. If those two don't work on your device, just
go to the "Phone Memory" folder. It uses a simple file-based access to your phone's
photos and should always work.

## Google Family Library

Google Play allows for some apps and games to be [shared amongst all members of your family](https://support.google.com/googleplay/answer/7007852).
Unfortunately, PhotoCloud is [not eligible for the Google Family Library program](https://support.google.com/googleplay/android-developer/thread/229982556?hl=en&msgid=229988003)
since:

* it's not a paid app
* [Not eligible for Teacher Approved Program](https://support.google.com/googleplay/android-developer/answer/10075896?hl=en)
* Google Play doesn't allow In-App Products such as "Unlock Daydream" and "Remove the Nagging Please Purchase"
  to be shared between family members.

The only way to remove the nagging "Please Purchase" image is to purchase the In-App Product
for the same Google user that is logged in to the tablet device intended to serve as a photo frame.

