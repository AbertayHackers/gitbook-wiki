# A guide to creating malicious macro-enabled Excel worksheets

*An tutorial by [Niall](https://wiki.hacksoc.co.uk/user/niall).*

This guide will go through the steps taken in order to create a malicious macro-enabled Excel worksheet. The tutorial will explain how to use msfvenom to create an x64 reverse shell, how to install and use luckystrike and how to set up a listener in order to detect the reverse shell. This tutorial will be catered to work on a local area network

This guide **will not** give details on how to distribute the documents created and is for **educational purposes only**.

### Pre-requisites

- Windows with Powershell V5 (update here: [Windows Management Framework 5](https://www.microsoft.com/en-us/download/details.aspx?id=50395))
- Microsoft office - at minimum Excel. Luckystrike uses Excel COM objects to build .xls documents
- Metasploit (found on Kali) or your own executable.

### Creating your reverse shell

This part of the tutorial will contain instructions on how to create your reverse shell.

[![hnz9skc.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=23fa47&media=http%3A%2F%2Fimgur.com%2FhNz9SKc.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=23fa47&media=http%3A%2F%2Fimgur.com%2FhNz9SKc.jpg)

The image above shows a terminal running the msfvenom command that will generate a x64 windows reverse shell. When entering this command, ensure that LHOST is the IP address of your Kali machine. You will want to now store your executable on a USB or transfer it over to your windows machine.
**Please note:** You may use any executable, powershell module or shell command, but this tutorial will use a simple reverse shell.

### Building Luckystrike

This part of the tutorial will walk through how to install Luckystrike in order to create our macro-enabled worksheets.

#### Method 1

Open powershell as admin and run the following:

```
iex (new-object net.webclient).downloadstring('https://raw.githubusercontent.com/Shellntel/luckystrike/master/install.ps1')
```

#### Method 2

Luckystrike can be downloaded from their github here: [LuckyStrike Github](https://github.com/Shellntel/luckystrike) Once you have downloaded the source, browse to the Luckystrike directory and run

```
./install.ps1
```

If you get the execution policy error, the fix is:

```
Set-ExecutionPolicy Unrestricted
```

Both these methods do the following:

1. Installs the PSSQLLite module if you don't have it (hence the admin rights needed)
2. Creates .\Luckystrike\
3. Creates the database (ls.db) and puts it into .\luckystrike
4. Copies luckystrike.ps1 into .\luckystrike

You should have now successfully built Luckystrike

### Creating the macro-enabled worksheet

Once the above step has been completed, browse to your Luckystrike directory and run

```
./luckystrike.ps1
```

. If all has went well, you will get the following screen: [![0goete6.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=19eaf2&media=http%3A%2F%2Fimgur.com%2F0gOEtE6.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=19eaf2&media=http%3A%2F%2Fimgur.com%2F0gOEtE6.jpg)

Now we need to add our payload to Luckystrikes catlogue, select the payload and generate the .xls document. See the following images:

[![3yl7j7g.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3cb9a5&media=http%3A%2F%2Fimgur.com%2F3yL7J7g.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3cb9a5&media=http%3A%2F%2Fimgur.com%2F3yL7J7g.jpg)
The image above shows the commands and how to add the executable to the tool. Ensure to use the absolute patch when entering the file path.

[![zmrkev5.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3dd445&media=http%3A%2F%2Fimgur.com%2FzMrkEv5.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3dd445&media=http%3A%2F%2Fimgur.com%2FzMrkEv5.jpg) Now select the payload for use.

Now generate the .xls file. [![mari3kz.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=c5db57&media=http%3A%2F%2Fimgur.com%2FMari3kz.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=c5db57&media=http%3A%2F%2Fimgur.com%2FMari3kz.jpg)

Your .xls file should be generated and stored in the path specified. Now rename it to something better and set up a listener.

### Setting up the listener

In order for our shell to connect back to our Kali machine, we need to set up a listener.

[![rc3ggl6.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3dc208&media=http%3A%2F%2Fimgur.com%2FRc3GgL6.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=3dc208&media=http%3A%2F%2Fimgur.com%2FRc3GgL6.jpg)

### Distribution

As you are in a test environment and wouldn't be doing anything illegal, simply open your excel document on the machine you created it on and enable macros when prompted.

### Success?

If successful and your document is ran and macros enabled, it will connect back to your Kali machine and your listener will look like this:

[![edyobr5.jpg](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=c97287&media=http%3A%2F%2Fimgur.com%2FEDYoBR5.jpg)](https://wiki.hacksoc.co.uk/lib/exe/fetch.php?tok=c97287&media=http%3A%2F%2Fimgur.com%2FEDYoBR5.jpg)

### Additional work

- Use a more interesting payload rather than a reverse shell
- It is possible to add payloads to existing worksheets, so create a nice encoded doc that will decrypt upon the macros being enabled
- Write your own payload
- Find a way to get the same idea working with MS Word (speak to Colin)
- Think of something interesting to do post-exploitation