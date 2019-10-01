# 7 Android

Obviously, you will need an Android device in this exercise ;-)

## Using a roaming authenticator on the Android platform

Webauthn can also be used on the Android platform. All major browsers support Webauthn via the USB interface. This often requires an adapter, which makes this a less convenient option. Luckily, your security key by yubico also has an NFC interface.

- Install the Latest Firefox Beta or Google Chrome on your Android (7+) device.
- Go to one of the webauthn demo sites, for instance [https://demo.yubicom.com/](https://demo.yubico.com/)
- Register your security key using NFC instead of USB.

## Using your Android device as an authenticator

The Android platform is [certified](https://fidoalliance.org/android-now-fido2-certified-accelerating-global-migration-beyond-passwords/) as a FIDO2 authenticator, meaning that don't need a roaming authenticator to use webauthn on Android.

Repeat the last exercice, but use the fingerprint scanner or face recognition features of your Android device to register.

## Use your Android device as a roaming authenticator

To protect Google accounts, you can also use your Android device as a roaming authenticator.
Follw along with this [blog](https://www.blog.google/technology/safety-security/your-android-phone-is-a-security-key/) to see if that works.

## Develop an Android application with the FIDO2 API

Android has a FIDO2 API for developing apps that can authenticate using FIDO2 keys.

If you have experience with developing Android apps,
follow along with the
[FIDO2 for Android codelab](https://codelabs.developers.google.com/codelabs/fido2-for-android).
