# Migration Manager Plugin Creator
A plugin creator for Tranxition Migration Manager

Migration Manager is a great option for migrating your Windows profile. None of the other options out there really spoke to me. One drawback to Migration Manager is that it has very few pre-defined backup settings for third-party applications. Worse, the only way to add your own is with the additional file/registry rules, which isn't great for keeping things organized and maintainable. All the rules for migrating all the files and registry settings just end up in one big list.

But there are already pre-defined settings so I figured the developers must have something in place. I noticed there was a `plugins` folder and started going through it. Sure enough, those files specify the rules for backing up applications and settings.
