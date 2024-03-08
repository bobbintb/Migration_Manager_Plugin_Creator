# Migration Manager Plugin Creator
A plugin creator for Tranxition Migration Manager

Migration Manager is a great option for migrating your Windows profile. None of the other options out there really spoke to me. One drawback to Migration Manager is that it has very few pre-defined backup settings for third-party applications. Worse, the only way to add your own is with the additional file/registry rules, which isn't great for keeping things organized and maintainable. All the rules for migrating all the files and registry settings just end up in one big list.

But there are already pre-defined settings so I figured the developers must have something in place. I noticed there was a `plugins` folder and started going through it. Sure enough, those files specify the rules for backing up applications and settings. Each plugin consists of two files:

`*.tndx` - An XML file that contains the specifications for the UI, i.e. the description, icon, section it is located under, etc.
`*.txd` - an unknown file format that has all the good stuff.

After a bit of analysis, I reverse-engineered the `txd` file format and wrote a small program to translate it to a `yaml` file. It will be uploaded soon. Currently, to create your own plugin, you will need to create a `yaml` file and convert it to a `txd` file. I am still working on adding more functionality to the app to make the process easier. Additionally, while I have worked out the entire format and structure of the `txd` files, I don't yet know what all of the options mean or do.

# TXD file format
The file is made of two parts, the header and the body. The header consists of seven lines:

PLACEHOLDER

The body consists of a series of rules, each ruling consisting of 13 lines:

`text1` - Text data. Could be blank, a variable, a file path, registry setting, etc., depending on the typ of rule.
`text2` - Text data. Could be blank, a variable, a file path, registry setting, etc., depending on the typ of rule.
`sectionUID` - The UID for the body of the file.
`text3` - Text data. Could be blank, a variable, a file path, registry setting, etc., depending on the typ of rule.
`itemUID` - The UID for the rule (this currect 13 line item)
`tndxUID` - The UID of the corresponding `tndx` file
`num1` - A numberic value of either 1 or 2.
`num2` - A numberic value of 1, 2, 3, or (in one rare, specific case) 4294967295.
`num3` - A numberic value. This seems to specify the main rule type.
`num4` - A numberic value. This seems to specify the secondary rule type.
`num5` - A numberic value.
`end1` - A numberic value, always 4294967295
`end2` - A numberic value, always 4294967295 (two lines of this value signify the end of a rule item.)

As you see, I still need to work out what some of these do. So far I have figured out how to backup a registry setting. I also found two errors with two of the existing `txd` files and have included the correct versions. I will detail thoe issues soon. I have included an Excel spreadsheet that I have been using to analyze the data and determine what the options and codes do. I have another with more information that I will upload soon. This is a work in progress but progress is moving quickly. I still have more information to share and add more capability to the app but the biggest issue to overcome is figuring out what all of the options are. I could really use the communities help with that and I'll share more information on that soon.
