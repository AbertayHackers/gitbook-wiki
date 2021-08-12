# Remote access to your Abertay network drive

So, you've forgotten your [pendrive](https://en.wikipedia.org/wiki/pendrive) enough times and been left wondering where did that question 14 you _surely_ did get lost?

I doesn't have to be like that! You can copy files from the home machine to university account with ease, and this guide will show you how. All you need is your university number, the password and a computer with [Internet](https://en.wikipedia.org/wiki/Internet) access. There are three ways to go about it.

## via myAbertay

1. Open a browser
2. Go to `https://my.abertay.ac.uk`
3. Click the `myFiles` tile
4. Login as [user@uad.ac.uk](mailto:user@uad.ac.uk)
5. Profit!

## via direct link

1. Open a browser
2. Go to `https://myfiles.abertay.ac.uk/myfiles/`
3. Login as [user@uad.ac.uk](mailto:user@uad.ac.uk)
4. Profit!

![img](../../.gitbook/assets/browser_view.png)

## via WebDAV

1. Open your file manager ![img](../../.gitbook/assets/connect_to_server.png)
2. Use `File > Connect to server`
3. Fill out the form as in the example→
   1. Server:
      1. `https://myfiles.abertay.ac.uk/myfiles/hcwebdav/` for Windows and MacOS
      2. `davs://myfiles.abertay.ac.uk/myfiles/hcwebdav/` for GTK-based Linux distros
      3. `webdavs://myfiles.abertay.ac.uk/myfiles/hcwebdav/` for QT-based Linux distros
   2. User name: [user@uad.ac.uk](mailto:user@uad.ac.uk)
4. Profit!

All screenshots from [Peppermint OS](https://peppermintos.com/) which uses the Nemo file manager, so [YMMV](https://en.wiktionary.org/wiki/your_mileage_may_vary)

According to the `Help` section in [https://myfiles.abertay.ac.uk/myfiles/](https://myfiles.abertay.ac.uk/myfiles/). In fact this whole guide wouldn't have happened without it, but that's the only part I'm including without personal testing

If your Desktop Environment is Unity, Gnome, XFCE or LXDE, that's what you want. It actually depends on whether your distro uses GVFS or KIO for it's virtual folder access

If your DE is KDE Plasma or LXQT, that's what you want

Warning: KNetAttach\(the script for connecting to webdav folders in KDE Plasma\) is currently broken. You can still connect to the network drive by putting `webdavs://myfiles.abertay.ac.uk/myfiles/hcwebdav/Home drive/` into the full path in Dolphin

