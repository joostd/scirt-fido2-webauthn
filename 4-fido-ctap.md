# 4 FIDO2 and CTAP

vagrant box add ubuntu/bionic64
    2  vagrant box add ubuntu/bionic64
    3  vagrant init ubuntu/bionic64
    
      config.vm.network "forwarded_port", guest: 8080, host: 8080

https://developers.yubico.com/libfido2/
https://developers.yubico.com/libfido2/Manuals/fido2-assert.html
https://developers.yubico.com/libfido2/Manuals/fido2-cred.html



git clone https://github.com/joostd/fido2-tutorial.git
cd yubico
make verify

or

## make a new credential

create a file `cred_param` containing a challenge hash (binary, base64 encoded),
relying party id,
user name,
user id (binary, base64 encoded)


https://developers.yubico.com/libfido2/Manuals/fido2-cred.html#INPUT_FORMAT
https://developers.yubico.com/libfido2/Manuals/fido2-cred.html#OUTPUT_FORMAT



echo credential challenge | openssl sha256 -binary | base64 > cred_param
echo relying party >> cred_param
echo user name >> cred_param
dd if=/dev/urandom bs=1 count=32 | base64 >> cred_param

sudo fido2-cred -M -i cred_param -o cred_result /dev/hidraw0
fido2-cred -V -i cred_result -o cred

last line: cert

cat cred_result | tail -1 | base64 -d | openssl x509 -inform de -noout -text



## obtain a new assertion

echo assertion challenge | openssl sha256 -binary | base64 > assert_param
echo relying party >> assert_param
head -1 cred >> assert_param
sudo fido2-assert -G -i assert_param -o assert_result /dev/hidraw0 
tail -n +2 cred > pubkey
fido2-assert -V -i assert_result pubkey es256


