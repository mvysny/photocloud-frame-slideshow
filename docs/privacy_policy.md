# Privacy Policy

PhotoCloud Frame Slideshow may remember your username/password for services which do not support security tokens
(for example Samba and OwnCloud). PhotoCloud never sends your data anywhere else but the stream server itself,
solely for the purpose of authenticating and downloading images. Images are downloaded to your phone only,
they are never uploaded anywhere. The images are cached for quicker display, you can delete the caches at any time.

PhotoCloud uploads warning and error messages anonymously to Crashlytic, for the sole purpose of helping bug fixing.
Those error messages never contain any username nor password. Other than that, PhotoCloud uploads nothing nowhere else,
except for the sole purpose of downloading images (you have to let the server know that you wish to download given image) :-D

## Google-specific Privacy Policy

The user data is not read by PhotoCloud in any way. PhotoCloud does not ask for user name, password nor anything else
except for an access token, which is used by PhotoCloud to read your files (Google Drive) or photos (Google Photos).
Only read-only access is used; PhotoCloud will not modify nor append any data nor photos.

Google API scopes used by the app:

* `https://www.googleapis.com/auth/photoslibrary.readonly` to read the Photos from the Photos Library
* `https://www.googleapis.com/auth/drive.file` allows PhotoCloud to see, edit, create, and delete only the specific Google Drive files you use with this app.

Previously, PhotoCloud used to ask for `https://www.googleapis.com/auth/drive.readonly` which allows
PhotoCloud to read all files and photos in your drive, however this scope is highly restricted by Google:

* all apps requesting access to restricted APIs must complete a third-party CASA security assessment
* this assessment must also be recertified annually in order for the app to maintain access to restricted APIs.
* I don't have time for that shit.

