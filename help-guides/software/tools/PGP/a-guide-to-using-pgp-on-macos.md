# A guide to using PGP on macOS

*An install guide by Kyle.*

This guide is written for macOS Sierra and has been tested using macOS Sierra 10.12.3. This tutorial will explain: how to install PGP; how to generate your own key pair and share keys; how to encrypt and decrypt messages and finally how to encrypt and decrypt files.

It **will not** explain how PGP works or good tradecraft to deploy when using PGPAll of the links footnoted are way better than an explanation I could write! (Alice and Bob *may* come into it at some point though).

## Install GPG Suite

Head over to [GPGTools](https://gpgtools.org/) and download the latest version of the package. Go to `Finder > Downloads > GPGSuite.dmg` and double click it. A box should pop up, just like the one below.

![GPG Suite start screen in MacOS](https://i.imgur.com/PkaEhox.png)

Now, go ahead and double click the install button. An installer window will then pop up, as seen below.

![Installation 1](https://i.imgur.com/txSFbe2.png)

Click through the screen using the `Continue` button.

![8-o](../../../.gitbook/assets/icon_eek.gif) ![8-o](../../../.gitbook/assets/icon_eek.gif) ![8-o](../../../.gitbook/assets/icon_eek.gif) ***TAKE YOUR TIME WITH THIS NEXT BIT\*** ![8-o](../../../.gitbook/assets/icon_eek.gif) ![8-o](../../../.gitbook/assets/icon_eek.gif) ![8-o](../../../.gitbook/assets/icon_eek.gif)
The next screen will say how much disk space it will take up and have 3 options `Customise`, `Go Back` or `Install`. Select the `Customise` option. If you've skipped through and not done this, restart the install process. See the screenshot below.

![Installation 2](https://i.imgur.com/wqkNRgL.png)

Once the option is selected, the installer will ask you to choose which services you do or don't want to install. De-select the GPGMail option, and keep the others ticked. Then click on `Install`, as seen below.

![Installation 3](https://i.imgur.com/5iengoQ.png)
You will then be prompted for your TouchID or password to install the software.

![Installation 4](https://i.imgur.com/5vzXAoJ.png)

Once installed, the install wizard can be closed. MacOS will give you an option to move the DMG file to trash - thats a personal choice

## Generating your own PGP keypair

Go to `GPG Keychain` via Applications or Launchpad and open it up. At the top left click on `New`. A box will pop up - expand the advanced options. Now you should have a box as seen below.

![Generate Key Pair](https://i.imgur.com/kIj96Ah.png)

Now, depending on what you are using PGP for, the boxes should be completed in slightly different ways

- **Full name:** This will be shown along with your PGP public key wherever you share it. If you do not wish to be associated with your real name, do not put it here. Use a handle or online name you are known by.

- **Email address:** This is what the keypair will be tied to.

- **Upload public key option:** Your public key will be uploaded to their server. It is up to you if you want to do this. If you want to advertise your public key you can also upload it to [MIT's PGP key server](https://pgp.mit.edu/), [Symantec's keyserver](https://keyserver.pgp.com/) and loads more online places.

  In [TheGrugq's](https://twitter.com/thegrugq) [operational PGP guide](https://gist.github.com/grugq/03167bed45e774551155), he recommends: `If you are serious about the anonymity of your PGP protected communications, you need to avoid publishing your key to the keyservers. Exchange your key only with the person(s) that you will communicate with. This will mitigate against future attribution attempts.`

- **Key length:** 4096bit is default.

- **Key expires:** Another one which is a personal choice.[ TheGrugq](https://twitter.com/thegrugq) says “A more secure mitigation against key loss is to generate new keys frequently” and having a relatively short expiry time helps to enforce this.

- **Passphrase:** This is the most vital part of the process. Here is a quick explanation - taken from [@JerzyGangi's](https://twitter.com/jerzygangi) [PGP for OS X](https://notes.jerzygangi.com/the-best-pgp-tutorial-for-mac-os-x-ever/) tutorial.

  - The entire PGP encryption will rest on your passphrase. So, first and foremost… don't use a passphrase that other people know! Pick something only you will know, and others can't guess. And once you have a passphrase selected, don't give it to other people.
  - Second, do not use a password, but rather a passphrase – a sentence. For example, “Pennstate55” is less preferable than “I graduated from Penn State in 1955, ya heard?!” ***The longer your passphrase, the more secure your key.\***
  - Lastly, make sure your passphrase is something you can remember. Since it is long, there is a tendency you might forget it. Don't. The consequences to that will be dire. Make sure you can remember your passphrase.

- **Generate Key:** Once all the above sections are done, go ahead and generate your key.

- Once some random bytes have been generated, you will have a new entry in the program with your newly generated keypair.

![Cool, huh](https://i.imgur.com/Vocs50L.gif)

## How to encrypt & decrypt messages

For this section you will need a person to test this with. If you don't have anyone, fire me a message on Slack. We can exchange keys and go from there *(don't be shy!)*. Now, before you get started it is important to remember when creating messages they will be stored in plaintext in a drafts folder on a mail server if you create them online or in the mail client. `For security, that is, control over the process, a text editor is safer. For convenience most people will use their email client.` as stated yet again by [TheGrugq](https://twitter.com/thegrugq).

### Importing a key

However you have retrieved a key, it should be in a .asc format. Open up GPG Keychain and click `Import` at the top right hand side. Browse to where you have saved the .asc file. Click `Open` and the key will be imported. Nice and easy.

To verify this is legit, keys should be either given to you directly by the person, in person. OR advertised in multiple places such as on their Twitter account, via IM and on a keyserver. These should all be double checked before usage to ensure you have the correct public key.

### Encrypting a message

Messages can be encrypted using the command line or using the GUI. The GUI is easiest on macOS and the instructions are below. Firstly, open up TextEdit (providing that it does not auto sync with iCloud). Set the type to plain text (using `⌘+Shift+T`). Write out your message - again depending on the sensitivity be aware of your surroundings. Select all the message (`⌘+A`) and right click. Select the `Encrypt selection to new window` option, as seen below.

![OpenPGP in action](https://i.imgur.com/jMaDjhq.png)

A popup box will appear asking you to select a recipient. Tick the sign box too, if you wish to sign your message. If you choose to sign the message, you will be asked to enter your passphrase.

Once this is completed, a PGP message block will appear in a separate window. See below.

![PGP Message Block](https://i.imgur.com/Ao8uTfO.png)

This block can then be selected, copy and pasted into the email client of your choice to be sent to the recipient. Who can then go on to decrypt the message.

### Encrypting a file

To encrypt a file, use the command line. Go to the working directory of the file and use the command below.

```bash
gpg -r “recipient@email.com” -e filename.ext
```

This will produce a file named `filename.ext.gpg` which is encrypted with the recipient's public key.

### Decrypting a message

When you have received a PGP block message, the way to decrypt it is very similar to the way to encrypt it. Select the entire message including the Armour. Right click on it and select `Decrypt selection to a new window`. You will be prompted for your passphrase, enter it. The message will then appear in plaintext in a new window.

### Decrypting a file

Again, decrypting a file is very similar to encrypting one. Save the received file onto disk and navigate to the directory on the command line. Once this is done, run the command below to decrypt the file.

```bash
gpg -o newfile.ext -d filename.ext.gpg
```

You will then be prompted for your passphrase, enter it. The file will then be written to the filename after the `-o`. If you do not want to save the file on disk, just running `gpg -d filename.ext.gpg` will print the output to stdout.

## Conclusion

That's the end of the tutorial. Follow the links and guide and if there are any issues please fire me a message via Slack. If you use this guide and it works also let me know! For more serious usage - have a good thorough read of the operational guide linked to above. And with that, I leave you with this ![8-)](../../../.gitbook/assets/icon_cool.gif)

![Edward Snowden Moment](https://media.giphy.com/media/SAeJELaeQikfu/giphy.gif)