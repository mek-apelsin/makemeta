# makemeta

Creates metapackages (in deb format) for a list of packages. 

# Metapackages? 

A metapackage is a package which doesn't provide anything by itself, instead it depends on a whole range of other packages. 

Typical metapackages on an Ubuntu system are:

	ubuntu-minimal: Which provides the bare minimum (except a kernel) of what an ubuntu system needs
	ubuntu-standard: A few extra packages which most people find quite handy on an cli-system.
	ubuntu-desktop: All that graphical stuff which makes a laptop and desktop so darn nice. 

# What is it for?

You've ever installed that external script, website or compiled that program that needed all those extra libraries and other packages? Can't quite remember which package was installed for which program? Metapackages might just help. 

For example, let us say you want to install the new owncloud. By looking at their installation manual[1], you see it needs ten packages, You quickly run the command below, name your new package owncloud7-prereqs, write a nice description, and install the package. Now you know whenever you want to delete owncloud it is just to clean up ownclouds "mess" and `apt-get remove owncloud-prereqs`. 

```
makemeta <<< "apache2 mysql-server libapache2-mod-php5 php5-gd php5-json php5-mysql php5-curl php5-intl php5-mcrypt php5-imagick"
```

Other usable packages are "my-cli-tools", "my-cli-graphics", "my-gui-graphics", "my-work-tools", etc. Put them up on a ppa or other repo, and you just have to up change one package (add a new "Depends" and up the version) and all your computers will upgrade and install your new tools. Makes it very easy to move to a new computer. 


[1] http://doc.owncloud.org/server/7.0/admin_manual/installation/installation_source.html


