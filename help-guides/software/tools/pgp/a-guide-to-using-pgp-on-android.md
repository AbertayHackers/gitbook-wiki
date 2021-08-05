# A guide to using PGP on Android

This guide was written and tested on Android 5, and according to the authors of used applications, should also work for Android 4.0.3+. Additionally, for Open Keychain, permissions will be requested on the go in Android 6+.

### Ingredients

1. Open Keychain - Essential. Handles key management and the actual decryption, other apps just use it's API to work with PGP
2. Communication app of your choice. This guide will use K-9 Mail, but a [number of other options](https://www.openkeychain.org/apps/) are available.
3. Password Manager - Highly recommended, but not necessary. For convenience, use a password manager with support for the same password database format as on the desktop. All of [KeePass\(.kbd & .kbdx\)](https://play.google.com/store/apps/details?id=com.android.keepass), [PasswordSafe\(.psafe3\)](https://pwsafe.org/) and [PasswordStore](https://www.passwordstore.org/) have Android versions.

## Open Keychain

[Open Keychain](https://www.openkeychain.org/)

### Setup

1. Use [F-Droid](https://f-droid.org/repository/browse/?fdid=org.sufficientlysecure.keychain) or [Play Store](https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain) to download Open Keychain
2. Get a PGP key pair on the device

   ![Manage My Keys](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand2.png)

   1. Click on the three dots in the upper right of the screen
   2. Choose `Manage my keys`
   3. Choose the appropriate option:
      * Import key from file

        Do NOT upload your private key to a cloud unencrypted. Transfer your existing PGP key to the phone via USB instead

      * Create my key
   4. Follow the instructions in the app

3. Import your contact's keys onto the device

   ![Before imported](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand1.png)

   * Use the + in the lower right of the screen

4. Check the status of the imported contact

![After imported](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand8.png)

| Key | Verified | Unverified | Insecure |
| :--- | :--- | :--- | :--- |
| Symbol | green tick | orange ![:?:](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/icon_question.gif) | grey X |
| Background | green or photo | orange | red |

![Facebook confirmed](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand7.png)

![Facebook unconfirmed](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand3.png)

* Keys will be unverified by default, unless you import a key with your, or another verified key's signature on it

### Verifying keys

![Verify keys](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand4.png)

1. Press on a key to open contact view
2. If your contact uses QR codes, use them. Otherwise:
   1. Press the three dots in the upper right corner
   2. `Confirm with fingerprint`
   3. Compare the fingerprint of the key with one provided by your contact

      Note: Full fingerprints are rarely provided. Commonly only the **last** 8 or 16 hex digits\(aka. key ID\) are
3. Sign the key to verify it

![Compare fingerprint screen](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand5.png)

![Confirm keys](https://github.com/AbertayHackers/gitbook-wiki/tree/128fd5664a9eed6c99bbff4379d587bc2c92b512/help-guides/.gitbook/assets/pgpand6.png)

* Check **beforehand**, if the key's owner wants it published and whether you want to publicly admit knowing them. Adjust the “Synchronize with the Internet” tick accordingly
* Untick the identities you don't want to sign
* Choose with which of your keys you want to sign the key with

Further information on Open Keychain is available in the `Help` section of the app, available under the hamburger\(upper left corner\).

## K-9 mail

[K-9 mail](https://k9mail.github.io/) is a fork of the Android Mail with a long history. It was chosen for the guide thanks to it's excellent integration with Open Keychain that allows you to encrypt all emails in just 3 more clicks per email, plus some initial setup.

### Setup

K-9 Mail is available for download on [F-Droid](https://f-droid.org/repository/browse/?fdid=com.fsck.k9) and [Play store](https://play.google.com/store/apps/details?id=com.fsck.k9).

* Configure your account conventionally\(IMAP/Exchange + SMTP\). Refer to [the documentation](https://k9mail.github.io/documentation.html) when necessary
* Go to `Three dots`\(lower right corner\) &gt; `Settings` &gt; `Account settings`
* Scroll to the bottom
* Go to `Cryptography`
* Choose Open Keychain as your PGP app
  1. Open Keychain will ask you to confirm granting K-9 access to the PGP API
  2. Allow it
* Choose your key

### Writing encrypted emails

When composing a new email, you will now see a lock next to your email address. The lock will change according to PGP is used:

* A white tick on a blue circle when the email will be signed, but not encrypted
* A green lock with 3 full circles when all recipient keys have verified keys in your keychain
* A grey, crossed lock and a single red dot when no recipient keys are among those verified in the keychain

The number of dots is also displayed next to each recipient separately. You can press the lock to change the encryption mode. The default is `encrypt if possible` and in it emails will be sent encrypted and unencrypted. You can also switch it to `Don't Encrypt` or `Encrypt`. In the last case, the email will fail to send if any recipient lacks a verified key in the keychain. That situation is indicated with a red lock with a white x and a singe red dot.

After pressing send, if the lock is green, Open Keychain will fire up to ask you for your PGP passphrase. Upon entering it, K-9 will send the encrypted message.

