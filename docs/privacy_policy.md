# Privacy Policy

PhotoCloud Frame Slideshow may remember your username/password for services which do not support security tokens
(for example Samba and OwnCloud). PhotoCloud never sends your data anywhere else but the stream server itself,
solely for the purpose of authenticating and downloading images. Images are downloaded to your phone only,
they are never uploaded anywhere. The images are cached for quicker display, you can delete the caches at any time.

PhotoCloud collects no analytics and sends no crash reports. It talks only to the photo sources you configure,
to sign in and download your photos, and, if you turn on the weather overlay, to look up your city
(the name you type goes to PhotoCloud's own city-search server) and to fetch its forecast from OpenWeatherMap.
Nothing else leaves your device.

## Google-specific Privacy Policy

PhotoCloud versions newer than 1.15.8 no longer read Google Drive nor Google Photos, and use no Google API to access your data.

PhotoCloud 1.15.8 and older offered Google Drive and Google Photos as photo sources. For those, PhotoCloud
did not ask for user name, password nor anything else except for an access token, which it used to read your
files (Google Drive) or photos (Google Photos). PhotoCloud never modified nor appended any data nor photos.
The Google API scopes those versions ask for:

* `https://www.googleapis.com/auth/photoslibrary.readonly` to read the Photos from the Photos Library
* `https://www.googleapis.com/auth/drive.file` allows PhotoCloud to see, edit, create, and delete only the specific Google Drive files you use with this app.

Even older versions asked for `https://www.googleapis.com/auth/drive.readonly`, which allows
PhotoCloud to read all files and photos in your drive. Google restricts that scope: an app requesting it
must complete a third-party CASA security assessment, recertified annually, which PhotoCloud does not do.

