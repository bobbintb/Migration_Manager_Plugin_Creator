# Migration Manager Plugin Creator
A plugin creator for Tranxition Migration Manager

Migration Manager is a great option for migrating your Windows profile. None of the other options out there really spoke to me. One drawback to Migration Manager is that it has very few pre-defined backup settings for third-party applications. Worse, the only way to add your own is with the additional file/registry rules, which isn't great for keeping things organized and maintainable. All the rules for migrating all the files and registry settings just end up in one big list.

But there are already pre-defined settings so I figured the developers must have something in place. I noticed there was a `plugins` folder and started going through it. Sure enough, those files specify the rules for backing up applications and settings. Each plugin consists of two files:

`*.tnxd` - An XML file that contains the specifications for the UI, i.e. the description, icon, section it is located under, etc.
`*.txd` - an unknown file format that has all the good stuff.

After a bit of analysis, I reverse-engineered the `txd` file format and wrote a small program to translate it to a `yaml` file. It will be uploaded soon. Currently, to create your own plugin, you will need to create a `yaml` file and convert it to a `txd` file. I am still working on adding more functionality to the app to make the process easier. Additionally, while I have worked out the entire format and structure of the `txd` files, I don't yet know what all of the options mean or do.
