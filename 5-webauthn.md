# 5 webauthn

Read https://webauthn.guide/ and try https://webauthn.io/

Experiment:

- Use Device Attestation by selecting Attestation type _None | Indirect | Direct_
- Use different authenticators by selecting Authenticator type _Unspecified | Cross-Platform | Platform (TMP)_

## plain client-side JavaScript

Either [view online](https://herrjemand.github.io/FIDO2WebAuthnSeries/) or run locally:

git clone https://github.com/herrjemand/FIDO2WebAuthnSeries.git

```
cd FIDO2WebAuthnSeries/
php -S localhost:8080 -t .
```

Open http://localhost:8080/ with your browser and open the JavaScript Console (e.g. with Chrome:
_View | Developer | JavaScript Console_)

## Other

- https://webauthn.me/
- http://cbor.me/
- https://webauthn.me/debugger

