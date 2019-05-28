# Windows Hello

Windows Hello [obtained FIDO2 Certification](https://fidoalliance.org/microsoft-achieves-fido2-certification-for-windows-hello/)
starting with the May 2019 update of Windows10 (also known as Windows 10 version 1903 or 19H1).

This exercise uses Windows Hello as a platform authenticator.

You can run Windows 10 in a VM.

- [Download the Windows 10 .iso file](https://www.microsoft.com/en-us/software-download/windows10ISO).
Make sure you select "Windows 10 May 2019 update".
- Create the VM using [Virtualbox](https://www.virtualbox.org/wiki/Downloads) (for instance) from the .iso image.
- Enable Windows Hello during installation. Using a VM probably means you can only use a PIN (and not a fingerprint scan or face recognition).

Go to one of the demo sites, e.g. https://demo.yubico.com/webauthn and register a platform authenticator using Windows Hello.

