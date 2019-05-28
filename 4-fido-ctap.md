# 4 FIDO2 and CTAP

In this exercies we will experiment with FIDO2 tokens from the command line (i.e. without a browser).

## libfido2

Install [libfido2](https://developers.yubico.com/libfido2/).

Included are command line tools for generating credentials ([fido2-cred](https://developers.yubico.com/libfido2/Manuals/fido2-cred.html
))
and assertions ([fido2-assert](https://developers.yubico.com/libfido2/Manuals/fido2-assert.html)).

## make a new credential

create a file `cred_param` containing a challenge hash (binary, base64 encoded),
relying party id,
user name,
user id (binary, base64 encoded)

See the `fido2-cred` manpage for [input](https://developers.yubico.com/libfido2/Manuals/fido2-cred.html#INPUT_FORMAT)
and [output](https://developers.yubico.com/libfido2/Manuals/fido2-cred.html#OUTPUT_FORMAT) formats:

Construct parameters for generating credentials:

```
echo credential challenge | openssl sha256 -binary | base64 > cred_param
echo relying party >> cred_param
echo user name >> cred_param
dd if=/dev/urandom bs=1 count=32 | base64 >> cred_param
```

Generate a credential:

    sudo fido2-cred -M -i cred_param -o cred_result /dev/hidraw0

Verify the result:

    fido2-cred -V -i cred_result -o cred

The last line is the attestation certificate. You can view its contents using:

    cat cred_result | tail -1 | base64 -d | openssl x509 -inform de -noout -text

## obtain a new assertion

Construct parameters for generating assertions:

```
echo assertion challenge | openssl sha256 -binary | base64 > assert_param
echo relying party >> assert_param
head -1 cred >> assert_param
```

Generate an assertion using these parameters:

    sudo fido2-assert -G -i assert_param -o assert_result /dev/hidraw0 

Extract the public key:

    tail -n +2 cred > pubkey

Verify the assertion using the public key:

    fido2-assert -V -i assert_result pubkey es256

## Using a Makefile

Alternatively, install and use these tools using a Makefile

```
git clone https://github.com/joostd/fido2-tutorial.git
cd yubico
make verify
```

## Using a VM

```
vagrant box add ubuntu/bionic64
vagrant init ubuntu/bionic64
```

      config.vm.network "forwarded_port", guest: 8080, host: 8080
      
