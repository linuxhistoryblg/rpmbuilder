# rpmbuilder
# Automated RPM building for single file distribution
rpmbuilder is a bash script which takes a single file and packages it as an rpm.

USAGE: rpmbuilder filename

WARNING: rpmbuilder MUST BE STARTED FROM THE DIRECTORY CONTAINING THE FILE YOU WISH TO PACKAGE AS AN RPM

DESCRIPTION: rpmbuilder takes a single argument, the name of the file you wish to package and uses the rpmbuild application and rpmdevtools to automate package creation. Upon successful completion the user is left with an installable RPM in a subdirectory of the user's home directory named after the packaged file. rpmbuilder automates the steps described in the howto located at https://sites.google.com/site/syscookbook/rhel/rhel-rpm-build. 

SETUP: rpmbuilder requires two files for successful operation. 1.)The rpmbuilder script itself, and 2.)The cleanspec file that rpmbuilder will use to customize a spec file for rpmbuild to use to build the rpm. The rpmbuilder script may be located anywhere the user chooses while the cleanspec file will need to go in the user's home directory.

EXAMPLE: I have a single file that I wish to package located at ~/Documents/myexamplefile. I change directory into ~/Documents/ and execute rpmbuilder as /path/to/rpmbuilder myexamplefile. The script will run and the resulting RPM will be deposited in ~/myexamplefile-BUILD/RPMS/. If I were to attempt to install the RPM (ex. rpm -ivh myexamplefile-1.0-1.el7.centos.noarch.rpm or yum localinstall myexamplefile-1.0-1.el7.centos.noarch.rpm) it would be installed directly into the /opt directory. This behavior may be modified by customizing the sed command at rpmbuilder line 70, TARGET5.
