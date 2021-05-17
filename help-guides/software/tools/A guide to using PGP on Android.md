# A guide to using PGP on Android

This guide was written and tested on Android 5, and according to the authors of used applications, should also work for Android 4.0.3+. Additionally, for Open Keychain, permissions will be requested on the go in Android 6+.

### Ingredients

1. [Open Keychain](https://wiki.hacksoc.co.uk/guides/pgp.android#open_keychain) - Essential. Handles key management and the actual decryption, other apps just use it's API to work with PGP
2. Communication app of your choice. This guide will use [K-9 Mail](https://wiki.hacksoc.co.uk/guides/pgp.android#k-9_mail), but a [number of other options](https://www.openkeychain.org/apps/) are available. [1)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__1)
3. Password Manager - Highly recommended, but not necessary. For convenience, use a password manager with support for the same password database format as on the desktop. All of [KeePass(.kbd & .kbdx)](https://play.google.com/store/apps/details?id=com.android.keepass), [PasswordSafe(.psafe3)](https://pwsafe.org/) and [PasswordStore](https://www.passwordstore.org/) have Android versions.

## Open Keychain

[Open Keychain](https://www.openkeychain.org/)

### Setup

1. Use [F-Droid](https://f-droid.org/repository/browse/?fdid=org.sufficientlysecure.keychain) or [Play Store](https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain) to download Open Keychain
2. Get a PGP key pair on the device[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand2.png?w=200&tok=780a3f)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand2.png?id=guides%3Apgp.android)
   1. Click on the three dots in the upper right of the screen
   2. Choose `Manage my keys`
   3. Choose the appropriate option:
      - Import key from file
        Do NOT upload your private key to a cloud unencrypted. Transfer your existing PGP key to the phone via USB instead
      - Create my key
   4. Follow the instructions in the app[2)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__2)
3. Import your contact's keys onto the device[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand1.png?w=300&tok=4ad652)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand1.png?id=guides%3Apgp.android)
   - Use the + in the lower right of the screen
4. Check the status of the imported contact

[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand8.png?w=300&tok=cfba86)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand8.png?id=guides%3Apgp.android)

| Key        | Verified                                                     | Unverified                                                   | Insecure |
| :--------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------- |
| Symbol     | green tick                                                   | orange ![:?:](https://wiki.hacksoc.co.uk/lib/images/smileys/icon_question.gif) | grey X   |
| Background | green or photo[3)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__3) | orange                                                       | red      |

[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand7.png?w=400&tok=8b2ace)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand7.png?id=guides%3Apgp.android)[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand3.png?w=400&tok=7704b8)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand3.png?id=guides%3Apgp.android)

- Keys will be unverified by default, unless you import a key with your, or another verified key's signature on it

### Verifying keys

[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand4.png?w=400&tok=3c45ca)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand4.png?id=guides%3Apgp.android)

1. Press on a key to open contact view
2. If your contact uses QR codes, use them. Otherwise:
   1. Press the three dots in the upper right corner
   2. `Confirm with fingerprint`
   3. Compare the fingerprint of the key with one provided by your contact
      Note: Full fingerprints are rarely provided. Commonly only the **last** 8 or 16 hex digits(aka. key ID) are
3. Sign the key to verify it[4)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__4)

[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand5.png?w=400&tok=3de963)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand5.png?id=guides%3Apgp.android)[![img](https://wiki.hacksoc.co.uk/_media/guides/pgpand6.png?w=400&tok=16452c)](https://wiki.hacksoc.co.uk/_detail/guides/pgpand6.png?id=guides%3Apgp.android)

- Check **beforehand**, if the key's owner wants it published and whether you want to publicly admit knowing them. Adjust the “Synchronize with the Internet” tick accordingly
- Untick the identities[5)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__5) you don't want to sign
- Choose with which of your keys you want to sign the key with

Further information on Open Keychain is available in the `Help` section of the app, available under the hamburger(upper left corner).

## K-9 mail

[K-9 mail](https://k9mail.github.io/) is a fork of the Android Mail with a long history. It was chosen for the guide thanks to it's excellent integration with Open Keychain that allows you to encrypt all emails in just 3 more clicks per email, plus some initial setup.

### Setup

K-9 Mail is available for download on [F-Droid](https://f-droid.org/repository/browse/?fdid=com.fsck.k9) and [Play store](https://play.google.com/store/apps/details?id=com.fsck.k9).

- Configure your account conventionally(IMAP/Exchange + SMTP). Refer to [the documentation](https://k9mail.github.io/documentation.html)[6)](https://wiki.hacksoc.co.uk/guides/pgp.android#fn__6) when necessary
- Go to `Three dots`(lower right corner) > `Settings` > `Account settings`
- Scroll to the bottom
- Go to `Cryptography`
- Choose Open Keychain as your PGP app
  1. Open Keychain will ask you to confirm granting K-9 access to the PGP API
  2. Allow it
- Choose your key

### Writing encrypted emails

When composing a new email, you will now see a lock next to your email address. The lock will change according to PGP is used:

- A white tick on a blue circle when the email will be signed, but not encrypted
- A green lock with 3 full circles when all recipient keys have verified keys in your keychain
- A grey, crossed lock and a single red dot when no recipient keys are among those verified in the keychain

The number of dots is also displayed next to each recipient separately. You can press the lock to change the encryption mode. The default is `encrypt if possible` and in it emails will be sent encrypted and unencrypted. You can also switch it to `Don't Encrypt` or `Encrypt`. In the last case, the email will fail to send if any recipient lacks a verified key in the keychain. That situation is indicated with a red lock with a white x and a singe red dot.

After pressing send, if the lock is green, Open Keychain will fire up to ask you for your PGP passphrase. Upon entering it, K-9 will send the encrypted message.

Pictures to the K-9 section will be added *later*.

## Alternatives

PGP in Gmail using OpenKeychain encrypt file for PGP/MIME and [Oversec](https://help.oversec.io/) for PGP/INLINE

[1)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__1) 

Android Mail is NOT one of them due to a [bug in it's PGP/MIME parser](https://github.com/open-keychain/open-keychain/issues/290)

[2)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__2) 

If you want to see more details on the settings you should use, consult [Kyle's MacPGP guide](https://hacksoc.co.uk/guides/mac-pgp#generating_your_own_pgp_keypair)

[3)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__3) 

By default verified keys are added to your address book and merged with contacts with a matching email address. Then, if you have a photo of that contact, Open Keychain will try to use it

[4)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__4) 

That is the actual, [confirmed](https://www.facebook.com/notes/protect-the-graph/securing-email-communications-from-facebook/1611941762379302) PGP key of [Facebook Inc](http://hkps.pool.sks-keyservers.net/pks/lookup?op=index&search=0x2f3898cedee958cf)

[5)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__5) 

A key can hold multiple identities for multiple email addresses

[6)](https://wiki.hacksoc.co.uk/guides/pgp.android#fnt__6) 

The official documentation of K-9 mail is unfortunately quite outdated