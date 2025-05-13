user@Syrex:~$  export GITHUB_TOKEN=Token
user@Syrex:~$ export GITHUB_USERNAME=Syrex333
user@Syrex:~$  export PACKAGE_MANAGER=apt
user@Syrex:~$ export GPG_PACKAGE_NAME=gpg
user@Syrex:~$ $PACKAGE_MANAGER install xclip
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
user@Syrex:~$ sudo apt install xclip
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  xclip
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
Need to get 18.4 kB of archives.
After this operation, 60.4 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal/universe amd64 xclip amd64 0.13-1 [18.4 kB]
Fetched 18.4 kB in 0s (84.8 kB/s)
Selecting previously unselected package xclip.
(Reading database ... 58805 files and directories currently installed.)
Preparing to unpack .../xclip_0.13-1_amd64.deb ...
Unpacking xclip (0.13-1) ...
Setting up xclip (0.13-1) ...
Processing triggers for man-db (2.9.1-1) ...
user@Syrex:~$ alias gsed=sed
user@Syrex:~$ alias pbcopy='xclip -selection clipboard'
user@Syrex:~$ alias pbpaste='xclip -selection clipboard -o'
user@Syrex:~$ cd ${GITHUB_USERNAME}/workspace
user@Syrex:~/Syrex333/workspace$ pushd .
~/Syrex333/workspace ~/Syrex333/workspace
user@Syrex:~/Syrex333/workspace$ source scripts/activate
user@Syrex:~/Syrex333/workspace$ go get github.com/aktau/github-release

Command 'go' not found, but can be installed with:

sudo snap install go         # version 1.24.2, or
sudo apt  install golang-go  # version 2:1.13~1ubuntu2
sudo apt  install gccgo-go   # version 2:1.13~1ubuntu2

See 'snap info go' for additional versions.

user@Syrex:~/Syrex333/workspace$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [128 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [128 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease [128 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [3535 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [3925 kB]
Get:7 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [514 kB]
Get:8 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [3710 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main Translation-en [596 kB]
Get:10 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [520 kB]
Get:11 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [1040 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [3863 kB]
Get:13 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [221 kB]
Get:14 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 Packages [26.6 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [540 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1262 kB]
Fetched 20.1 MB in 4s (5267 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
52 packages can be upgraded. Run 'apt list --upgradable' to see them.
user@Syrex:~/Syrex333/workspace$ sudo apt install golang-go
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  golang-1.13-go golang-1.13-race-detector-runtime golang-1.13-src golang-race-detector-runtime golang-src
  libdpkg-perl libfile-fcntllock-perl pkg-config
Suggested packages:
  bzr | brz mercurial subversion debian-keyring bzr dpkg-dev
The following NEW packages will be installed:
  golang-1.13-go golang-1.13-race-detector-runtime golang-1.13-src golang-go golang-race-detector-runtime golang-src
  libdpkg-perl libfile-fcntllock-perl pkg-config
0 upgraded, 9 newly installed, 0 to remove and 52 not upgraded.
Need to get 61.3 MB of archives.
After this operation, 327 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Abort.
user@Syrex:~/Syrex333/workspace$ sudo apt install golang-go
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  golang-1.13-go golang-1.13-race-detector-runtime golang-1.13-src golang-race-detector-runtime golang-src
  libdpkg-perl libfile-fcntllock-perl pkg-config
Suggested packages:
  bzr | brz mercurial subversion debian-keyring bzr dpkg-dev
The following NEW packages will be installed:
  golang-1.13-go golang-1.13-race-detector-runtime golang-1.13-src golang-go golang-race-detector-runtime golang-src
  libdpkg-perl libfile-fcntllock-perl pkg-config
0 upgraded, 9 newly installed, 0 to remove and 52 not upgraded.
Need to get 61.3 MB of archives.
After this operation, 327 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 golang-1.13-src amd64 1.13.8-1ubuntu1.2 [12.6 MB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 golang-1.13-go amd64 1.13.8-1ubuntu1.2 [47.6 MB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main amd64 golang-1.13-race-detector-runtime amd64 0.0+svn332029-0ubuntu2 [713 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal/main amd64 golang-src amd64 2:1.13~1ubuntu2 [4044 B]
Get:5 http://archive.ubuntu.com/ubuntu focal/main amd64 golang-go amd64 2:1.13~1ubuntu2 [22.0 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libdpkg-perl all 1.19.7ubuntu3.2 [231 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal/main amd64 libfile-fcntllock-perl amd64 0.22-3build4 [33.1 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/main amd64 pkg-config amd64 0.29.1-0ubuntu4 [45.5 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal/main amd64 golang-race-detector-runtime amd64 2:1.13~1ubuntu2 [3836 B]
Fetched 61.3 MB in 4s (17.1 MB/s)
Selecting previously unselected package golang-1.13-src.
(Reading database ... 58817 files and directories currently installed.)
Preparing to unpack .../0-golang-1.13-src_1.13.8-1ubuntu1.2_amd64.deb ...
Unpacking golang-1.13-src (1.13.8-1ubuntu1.2) ...
Selecting previously unselected package golang-1.13-go.
Preparing to unpack .../1-golang-1.13-go_1.13.8-1ubuntu1.2_amd64.deb ...
Unpacking golang-1.13-go (1.13.8-1ubuntu1.2) ...
Selecting previously unselected package golang-1.13-race-detector-runtime.
Preparing to unpack .../2-golang-1.13-race-detector-runtime_0.0+svn332029-0ubuntu2_amd64.deb ...
Unpacking golang-1.13-race-detector-runtime (0.0+svn332029-0ubuntu2) ...
Selecting previously unselected package golang-src.
Preparing to unpack .../3-golang-src_2%3a1.13~1ubuntu2_amd64.deb ...
Unpacking golang-src (2:1.13~1ubuntu2) ...
Selecting previously unselected package golang-go.
Preparing to unpack .../4-golang-go_2%3a1.13~1ubuntu2_amd64.deb ...
Unpacking golang-go (2:1.13~1ubuntu2) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../5-libdpkg-perl_1.19.7ubuntu3.2_all.deb ...
Unpacking libdpkg-perl (1.19.7ubuntu3.2) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../6-libfile-fcntllock-perl_0.22-3build4_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-3build4) ...
Selecting previously unselected package pkg-config.
Preparing to unpack .../7-pkg-config_0.29.1-0ubuntu4_amd64.deb ...
Unpacking pkg-config (0.29.1-0ubuntu4) ...
Selecting previously unselected package golang-race-detector-runtime.
Preparing to unpack .../8-golang-race-detector-runtime_2%3a1.13~1ubuntu2_amd64.deb ...
Unpacking golang-race-detector-runtime (2:1.13~1ubuntu2) ...
Setting up golang-1.13-src (1.13.8-1ubuntu1.2) ...
Setting up golang-1.13-race-detector-runtime (0.0+svn332029-0ubuntu2) ...
Setting up libfile-fcntllock-perl (0.22-3build4) ...
Setting up golang-1.13-go (1.13.8-1ubuntu1.2) ...
Setting up libdpkg-perl (1.19.7ubuntu3.2) ...
Setting up golang-src (2:1.13~1ubuntu2) ...
Setting up golang-race-detector-runtime (2:1.13~1ubuntu2) ...
Setting up golang-go (2:1.13~1ubuntu2) ...
Setting up pkg-config (0.29.1-0ubuntu4) ...
Processing triggers for man-db (2.9.1-1) ...
user@Syrex:~/Syrex333/workspace$ go get github.com/aktau/github-release
# github.com/github-release/github-release/vendor/github.com/kevinburke/rest/restclient
../../go/src/github.com/github-release/github-release/vendor/github.com/kevinburke/rest/restclient/client.go:204:18: undefined: io.ReadAll
../../go/src/github.com/github-release/github-release/vendor/github.com/kevinburke/rest/restclient/client.go:218:18: undefined: io.ReadAll
user@Syrex:~/Syrex333/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab08 projects/lab09
Cloning into 'projects/lab09'...
remote: Enumerating objects: 261, done.
remote: Counting objects: 100% (261/261), done.
remote: Compressing objects: 100% (125/125), done.
remote: Total 261 (delta 104), reused 256 (delta 102), pack-reused 0 (from 0)
Receiving objects: 100% (261/261), 970.28 KiB | 114.00 KiB/s, done.
Resolving deltas: 100% (104/104), done.
user@Syrex:~/Syrex333/workspace$ cd projects/lab09
user@Syrex:~/Syrex333/workspace/projects/lab09$ git remote remove origin
user@Syrex:~/Syrex333/workspace/projects/lab09$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab09
user@Syrex:~/Syrex333/workspace/projects/lab09$  gsed -i 's/lab08/lab09/g' README.md
user@Syrex:~/Syrex333/workspace/projects/lab09$ $PACKAGE_MANAGER install ${GPG_PACKAGE_NAME}
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
user@Syrex:~/Syrex333/workspace/projects/lab09$ sudo apt update && sudo apt install ${GPG_PACKAGE_NAME}
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
52 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  dirmngr gnupg gnupg-l10n gnupg-utils gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv
Suggested packages:
  pinentry-gnome3 tor parcimonie xloadimage scdaemon
The following packages will be upgraded:
  dirmngr gnupg gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv
11 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 2565 kB of archives.
After this operation, 4096 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Abort.
user@Syrex:~/Syrex333/workspace/projects/lab09$ sudo apt update && sudo apt install ${GPG_PACKAGE_NAME}
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
52 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  dirmngr gnupg gnupg-l10n gnupg-utils gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv
Suggested packages:
  pinentry-gnome3 tor parcimonie xloadimage scdaemon
The following packages will be upgraded:
  dirmngr gnupg gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv
11 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 2565 kB of archives.
After this operation, 4096 B of additional disk space will be used.
Do you want to continue? [Y/n]Y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpg-wks-client amd64 2.2.19-3ubuntu2.4 [97.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 dirmngr amd64 2.2.19-3ubuntu2.4 [329 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpg-wks-server amd64 2.2.19-3ubuntu2.4 [90.1 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gnupg-utils amd64 2.2.19-3ubuntu2.4 [481 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpg-agent amd64 2.2.19-3ubuntu2.4 [232 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpg amd64 2.2.19-3ubuntu2.4 [482 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpgconf amd64 2.2.19-3ubuntu2.4 [124 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gnupg-l10n all 2.2.19-3ubuntu2.4 [51.9 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gnupg all 2.2.19-3ubuntu2.4 [259 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpgsm amd64 2.2.19-3ubuntu2.4 [217 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 gpgv amd64 2.2.19-3ubuntu2.4 [200 kB]
Fetched 2565 kB in 1s (3997 kB/s)
(Reading database ... 69148 files and directories currently installed.)
Preparing to unpack .../00-gpg-wks-client_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpg-wks-client (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../01-dirmngr_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking dirmngr (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../02-gpg-wks-server_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpg-wks-server (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../03-gnupg-utils_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gnupg-utils (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../04-gpg-agent_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpg-agent (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../05-gpg_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpg (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../06-gpgconf_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpgconf (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../07-gnupg-l10n_2.2.19-3ubuntu2.4_all.deb ...
Unpacking gnupg-l10n (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../08-gnupg_2.2.19-3ubuntu2.4_all.deb ...
Unpacking gnupg (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../09-gpgsm_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpgsm (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Preparing to unpack .../10-gpgv_2.2.19-3ubuntu2.4_amd64.deb ...
Unpacking gpgv (2.2.19-3ubuntu2.4) over (2.2.19-3ubuntu2.2) ...
Setting up gpgv (2.2.19-3ubuntu2.4) ...
Setting up gnupg-l10n (2.2.19-3ubuntu2.4) ...
Setting up gpgconf (2.2.19-3ubuntu2.4) ...
Setting up gpg (2.2.19-3ubuntu2.4) ...
Setting up gnupg-utils (2.2.19-3ubuntu2.4) ...
Setting up gpg-agent (2.2.19-3ubuntu2.4) ...
Setting up gpgsm (2.2.19-3ubuntu2.4) ...
Setting up dirmngr (2.2.19-3ubuntu2.4) ...
Setting up gpg-wks-server (2.2.19-3ubuntu2.4) ...
Setting up gpg-wks-client (2.2.19-3ubuntu2.4) ...
Setting up gnupg (2.2.19-3ubuntu2.4) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...
user@Syrex:~/Syrex333/workspace/projects/lab09$ gpg --list-secret-keys --keyid-format LONG
gpg: directory '/home/user/.gnupg' created
gpg: keybox '/home/user/.gnupg/pubring.kbx' created
gpg: /home/user/.gnupg/trustdb.gpg: trustdb created
user@Syrex:~/Syrex333/workspace/projects/lab09$ gpg --full-generate-key
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 14у
RSA keysizes must be in the range 1024-4096
What keysize do you want? (3072) 1024
Requested keysize is 1024 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Syrex333
Email address: 1
Not a valid email address
Email address: ivan.chernogorov.02@bk.ru
Comment: 123
You selected this USER-ID:
    "Syrex333 (123) <ivan.chernogorov.02@bk.ru>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? 0
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Operation cancelled
Key generation failed: Operation cancelled
user@Syrex:~/Syrex333/workspace/projects/lab09$ gpg --list-secret-keys --keyid-format LONG
user@Syrex:~/Syrex333/workspace/projects/lab09$ gpg -K ${GITHUB_USERNAME}
gpg: error reading key: No secret key
user@Syrex:~/Syrex333/workspace/projects/lab09$ GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
user@Syrex:~/Syrex333/workspace/projects/lab09$ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
user@Syrex:~/Syrex333/workspace/projects/lab09$ gpg --armor --export ${GPG_KEY_ID} | pbcopy
gpg: WARNING: nothing exported
user@Syrex:~/Syrex333/workspace/projects/lab09$ pbpaste
pbpasteuser@Syrex:~/Syrex333/workspace/projects/lab09$ open https://github.com/settings/keys

Command 'open' not found, did you mean:

  command 'wopen' from deb gworkspace.app (0.9.4-2)
  command 'gopen' from deb gnustep-gui-runtime (0.27.0-5build2)
  command 'pen' from deb pen (0.34.1-1build1)

Try: sudo apt install <deb name>

user@Syrex:~/Syrex333/workspace/projects/lab09$ xdg-open https://github.com/settings/keys

Command 'xdg-open' not found, but can be installed with:

sudo apt install xdg-utils

user@Syrex:~/Syrex333/workspace/projects/lab09$ sudo apt update && sudo apt install xdg-utils
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
41 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libauthen-sasl-perl libdata-dump-perl libencode-locale-perl libfile-basedir-perl libfile-desktopentry-perl
  libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-html-perl libio-socket-ssl-perl libio-stringy-perl
  libipc-system-simple-perl liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libnet-dbus-perl
  libnet-http-perl libnet-smtp-ssl-perl libnet-ssleay-perl libtie-ixhash-perl libtimedate-perl libtry-tiny-perl
  liburi-perl libwww-perl libwww-robotrules-perl libx11-protocol-perl libxml-parser-perl libxml-twig-perl
  libxml-xpathengine-perl perl-openssl-defaults x11-xserver-utils
Suggested packages:
  libdigest-hmac-perl libgssapi-perl libcrypt-ssleay-perl libauthen-ntlm-perl libunicode-map8-perl
  libunicode-string-perl xml-twig-tools nickle cairo-5c xorg-docs-core
The following NEW packages will be installed:
  libauthen-sasl-perl libdata-dump-perl libencode-locale-perl libfile-basedir-perl libfile-desktopentry-perl
  libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-html-perl libio-socket-ssl-perl libio-stringy-perl
  libipc-system-simple-perl liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libnet-dbus-perl
  libnet-http-perl libnet-smtp-ssl-perl libnet-ssleay-perl libtie-ixhash-perl libtimedate-perl libtry-tiny-perl
  liburi-perl libwww-perl libwww-robotrules-perl libx11-protocol-perl libxml-parser-perl libxml-twig-perl
  libxml-xpathengine-perl perl-openssl-defaults x11-xserver-utils xdg-utils
0 upgraded, 42 newly installed, 0 to remove and 41 not upgraded.
Need to get 2618 kB of archives.
After this operation, 8654 kB of additional disk space will be used.
Do you want to continue? [Y/n]Y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 libdata-dump-perl all 1.23-1 [27.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal/main amd64 libencode-locale-perl all 1.05-1 [12.3 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main amd64 libipc-system-simple-perl all 1.26-1 [22.8 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal/main amd64 libfile-basedir-perl all 0.08-1 [16.9 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal/main amd64 liburi-perl all 1.76-2 [77.5 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal/main amd64 libfile-desktopentry-perl all 0.22-1 [18.2 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal/main amd64 libtimedate-perl all 2.3200-1 [34.0 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/main amd64 libhttp-date-perl all 6.05-1 [9920 B]
Get:9 http://archive.ubuntu.com/ubuntu focal/main amd64 libfile-listing-perl all 6.04-1 [9774 B]
Get:10 http://archive.ubuntu.com/ubuntu focal/main amd64 libfile-mimeinfo-perl all 0.29-1 [41.5 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal/main amd64 libfont-afm-perl all 1.20-2 [13.2 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal/main amd64 libhtml-tagset-perl all 3.20-4 [12.5 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal/main amd64 libhtml-parser-perl amd64 3.72-5 [86.3 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal/main amd64 libio-html-perl all 1.001-1 [14.9 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal/main amd64 liblwp-mediatypes-perl all 6.04-1 [19.5 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal/main amd64 libhttp-message-perl all 6.22-1 [76.1 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal/main amd64 libhtml-form-perl all 6.07-1 [22.2 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal/main amd64 libhtml-tree-perl all 5.07-2 [200 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal/main amd64 libhtml-format-perl all 2.12-1 [41.3 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal/main amd64 libhttp-cookies-perl all 6.08-1 [18.3 kB]
Get:21 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libhttp-daemon-perl all 6.06-1ubuntu0.1 [22.0 kB]
Get:22 http://archive.ubuntu.com/ubuntu focal/main amd64 libhttp-negotiate-perl all 6.01-1 [12.5 kB]
Get:23 http://archive.ubuntu.com/ubuntu focal/main amd64 perl-openssl-defaults amd64 4 [7192 B]
Get:24 http://archive.ubuntu.com/ubuntu focal/main amd64 libnet-ssleay-perl amd64 1.88-2ubuntu1 [291 kB]
Get:25 http://archive.ubuntu.com/ubuntu focal/main amd64 libio-socket-ssl-perl all 2.067-1 [176 kB]
Get:26 http://archive.ubuntu.com/ubuntu focal/main amd64 libio-stringy-perl all 2.111-3 [55.8 kB]
Get:27 http://archive.ubuntu.com/ubuntu focal/main amd64 libnet-http-perl all 6.19-1 [22.8 kB]
Get:28 http://archive.ubuntu.com/ubuntu focal/main amd64 libtry-tiny-perl all 0.30-1 [20.5 kB]
Get:29 http://archive.ubuntu.com/ubuntu focal/main amd64 libwww-robotrules-perl all 6.02-1 [12.6 kB]
Get:30 http://archive.ubuntu.com/ubuntu focal/main amd64 libwww-perl all 6.43-1 [140 kB]
Get:31 http://archive.ubuntu.com/ubuntu focal/main amd64 liblwp-protocol-https-perl all 6.07-2ubuntu2 [8560 B]
Get:32 http://archive.ubuntu.com/ubuntu focal/main amd64 libnet-smtp-ssl-perl all 1.04-1 [5948 B]
Get:33 http://archive.ubuntu.com/ubuntu focal/main amd64 libmailtools-perl all 2.21-1 [80.7 kB]
Get:34 http://archive.ubuntu.com/ubuntu focal/main amd64 libxml-parser-perl amd64 2.46-1 [193 kB]
Get:35 http://archive.ubuntu.com/ubuntu focal/main amd64 libxml-twig-perl all 1:3.50-2 [155 kB]
Get:36 http://archive.ubuntu.com/ubuntu focal/main amd64 libnet-dbus-perl amd64 1.2.0-1 [177 kB]
Get:37 http://archive.ubuntu.com/ubuntu focal/main amd64 libtie-ixhash-perl all 1.23-2 [11.2 kB]
Get:38 http://archive.ubuntu.com/ubuntu focal/main amd64 libx11-protocol-perl all 0.56-7 [149 kB]
Get:39 http://archive.ubuntu.com/ubuntu focal/main amd64 libxml-xpathengine-perl all 0.14-1 [31.8 kB]
Get:40 http://archive.ubuntu.com/ubuntu focal/main amd64 x11-xserver-utils amd64 7.7+8 [162 kB]
Get:41 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 xdg-utils all 1.1.3-2ubuntu1.20.04.2 [61.4 kB]
Get:42 http://archive.ubuntu.com/ubuntu focal/main amd64 libauthen-sasl-perl all 2.1600-1 [48.7 kB]
Fetched 2618 kB in 12s (214 kB/s)
Extracting templates from packages: 100%
Selecting previously unselected package libdata-dump-perl.
(Reading database ... 69148 files and directories currently installed.)
Preparing to unpack .../00-libdata-dump-perl_1.23-1_all.deb ...
Unpacking libdata-dump-perl (1.23-1) ...
Selecting previously unselected package libencode-locale-perl.
Preparing to unpack .../01-libencode-locale-perl_1.05-1_all.deb ...
Unpacking libencode-locale-perl (1.05-1) ...
Selecting previously unselected package libipc-system-simple-perl.
Preparing to unpack .../02-libipc-system-simple-perl_1.26-1_all.deb ...
Unpacking libipc-system-simple-perl (1.26-1) ...
Selecting previously unselected package libfile-basedir-perl.
Preparing to unpack .../03-libfile-basedir-perl_0.08-1_all.deb ...
Unpacking libfile-basedir-perl (0.08-1) ...
Selecting previously unselected package liburi-perl.
Preparing to unpack .../04-liburi-perl_1.76-2_all.deb ...
Unpacking liburi-perl (1.76-2) ...
Selecting previously unselected package libfile-desktopentry-perl.
Preparing to unpack .../05-libfile-desktopentry-perl_0.22-1_all.deb ...
Unpacking libfile-desktopentry-perl (0.22-1) ...
Selecting previously unselected package libtimedate-perl.
Preparing to unpack .../06-libtimedate-perl_2.3200-1_all.deb ...
Unpacking libtimedate-perl (2.3200-1) ...
Selecting previously unselected package libhttp-date-perl.
Preparing to unpack .../07-libhttp-date-perl_6.05-1_all.deb ...
Unpacking libhttp-date-perl (6.05-1) ...
Selecting previously unselected package libfile-listing-perl.
Preparing to unpack .../08-libfile-listing-perl_6.04-1_all.deb ...
Unpacking libfile-listing-perl (6.04-1) ...
Selecting previously unselected package libfile-mimeinfo-perl.
Preparing to unpack .../09-libfile-mimeinfo-perl_0.29-1_all.deb ...
Unpacking libfile-mimeinfo-perl (0.29-1) ...
Selecting previously unselected package libfont-afm-perl.
Preparing to unpack .../10-libfont-afm-perl_1.20-2_all.deb ...
Unpacking libfont-afm-perl (1.20-2) ...
Selecting previously unselected package libhtml-tagset-perl.
Preparing to unpack .../11-libhtml-tagset-perl_3.20-4_all.deb ...
Unpacking libhtml-tagset-perl (3.20-4) ...
Selecting previously unselected package libhtml-parser-perl.
Preparing to unpack .../12-libhtml-parser-perl_3.72-5_amd64.deb ...
Unpacking libhtml-parser-perl (3.72-5) ...
Selecting previously unselected package libio-html-perl.
Preparing to unpack .../13-libio-html-perl_1.001-1_all.deb ...
Unpacking libio-html-perl (1.001-1) ...
Selecting previously unselected package liblwp-mediatypes-perl.
Preparing to unpack .../14-liblwp-mediatypes-perl_6.04-1_all.deb ...
Unpacking liblwp-mediatypes-perl (6.04-1) ...
Selecting previously unselected package libhttp-message-perl.
Preparing to unpack .../15-libhttp-message-perl_6.22-1_all.deb ...
Unpacking libhttp-message-perl (6.22-1) ...
Selecting previously unselected package libhtml-form-perl.
Preparing to unpack .../16-libhtml-form-perl_6.07-1_all.deb ...
Unpacking libhtml-form-perl (6.07-1) ...
Selecting previously unselected package libhtml-tree-perl.
Preparing to unpack .../17-libhtml-tree-perl_5.07-2_all.deb ...
Unpacking libhtml-tree-perl (5.07-2) ...
Selecting previously unselected package libhtml-format-perl.
Preparing to unpack .../18-libhtml-format-perl_2.12-1_all.deb ...
Unpacking libhtml-format-perl (2.12-1) ...
Selecting previously unselected package libhttp-cookies-perl.
Preparing to unpack .../19-libhttp-cookies-perl_6.08-1_all.deb ...
Unpacking libhttp-cookies-perl (6.08-1) ...
Selecting previously unselected package libhttp-daemon-perl.
Preparing to unpack .../20-libhttp-daemon-perl_6.06-1ubuntu0.1_all.deb ...
Unpacking libhttp-daemon-perl (6.06-1ubuntu0.1) ...
Selecting previously unselected package libhttp-negotiate-perl.
Preparing to unpack .../21-libhttp-negotiate-perl_6.01-1_all.deb ...
Unpacking libhttp-negotiate-perl (6.01-1) ...
Selecting previously unselected package perl-openssl-defaults:amd64.
Preparing to unpack .../22-perl-openssl-defaults_4_amd64.deb ...
Unpacking perl-openssl-defaults:amd64 (4) ...
Selecting previously unselected package libnet-ssleay-perl.
Preparing to unpack .../23-libnet-ssleay-perl_1.88-2ubuntu1_amd64.deb ...
Unpacking libnet-ssleay-perl (1.88-2ubuntu1) ...
Selecting previously unselected package libio-socket-ssl-perl.
Preparing to unpack .../24-libio-socket-ssl-perl_2.067-1_all.deb ...
Unpacking libio-socket-ssl-perl (2.067-1) ...
Selecting previously unselected package libio-stringy-perl.
Preparing to unpack .../25-libio-stringy-perl_2.111-3_all.deb ...
Unpacking libio-stringy-perl (2.111-3) ...
Selecting previously unselected package libnet-http-perl.
Preparing to unpack .../26-libnet-http-perl_6.19-1_all.deb ...
Unpacking libnet-http-perl (6.19-1) ...
Selecting previously unselected package libtry-tiny-perl.
Preparing to unpack .../27-libtry-tiny-perl_0.30-1_all.deb ...
Unpacking libtry-tiny-perl (0.30-1) ...
Selecting previously unselected package libwww-robotrules-perl.
Preparing to unpack .../28-libwww-robotrules-perl_6.02-1_all.deb ...
Unpacking libwww-robotrules-perl (6.02-1) ...
Selecting previously unselected package libwww-perl.
Preparing to unpack .../29-libwww-perl_6.43-1_all.deb ...
Unpacking libwww-perl (6.43-1) ...
Selecting previously unselected package liblwp-protocol-https-perl.
Preparing to unpack .../30-liblwp-protocol-https-perl_6.07-2ubuntu2_all.deb ...
Unpacking liblwp-protocol-https-perl (6.07-2ubuntu2) ...
Selecting previously unselected package libnet-smtp-ssl-perl.
Preparing to unpack .../31-libnet-smtp-ssl-perl_1.04-1_all.deb ...
Unpacking libnet-smtp-ssl-perl (1.04-1) ...
Selecting previously unselected package libmailtools-perl.
Preparing to unpack .../32-libmailtools-perl_2.21-1_all.deb ...
Unpacking libmailtools-perl (2.21-1) ...
Selecting previously unselected package libxml-parser-perl.
Preparing to unpack .../33-libxml-parser-perl_2.46-1_amd64.deb ...
Unpacking libxml-parser-perl (2.46-1) ...
Selecting previously unselected package libxml-twig-perl.
Preparing to unpack .../34-libxml-twig-perl_1%3a3.50-2_all.deb ...
Unpacking libxml-twig-perl (1:3.50-2) ...
Selecting previously unselected package libnet-dbus-perl.
Preparing to unpack .../35-libnet-dbus-perl_1.2.0-1_amd64.deb ...
Unpacking libnet-dbus-perl (1.2.0-1) ...
Selecting previously unselected package libtie-ixhash-perl.
Preparing to unpack .../36-libtie-ixhash-perl_1.23-2_all.deb ...
Unpacking libtie-ixhash-perl (1.23-2) ...
Selecting previously unselected package libx11-protocol-perl.
Preparing to unpack .../37-libx11-protocol-perl_0.56-7_all.deb ...
Unpacking libx11-protocol-perl (0.56-7) ...
Selecting previously unselected package libxml-xpathengine-perl.
Preparing to unpack .../38-libxml-xpathengine-perl_0.14-1_all.deb ...
Unpacking libxml-xpathengine-perl (0.14-1) ...
Selecting previously unselected package x11-xserver-utils.
Preparing to unpack .../39-x11-xserver-utils_7.7+8_amd64.deb ...
Unpacking x11-xserver-utils (7.7+8) ...
Selecting previously unselected package xdg-utils.
Preparing to unpack .../40-xdg-utils_1.1.3-2ubuntu1.20.04.2_all.deb ...
Unpacking xdg-utils (1.1.3-2ubuntu1.20.04.2) ...
Selecting previously unselected package libauthen-sasl-perl.
Preparing to unpack .../41-libauthen-sasl-perl_2.1600-1_all.deb ...
Unpacking libauthen-sasl-perl (2.1600-1) ...
Setting up libtie-ixhash-perl (1.23-2) ...
Setting up libfont-afm-perl (1.20-2) ...
Setting up libio-stringy-perl (2.111-3) ...
Setting up libhtml-tagset-perl (3.20-4) ...
Setting up libauthen-sasl-perl (2.1600-1) ...
Setting up liblwp-mediatypes-perl (6.04-1) ...
Setting up libtry-tiny-perl (0.30-1) ...
Setting up perl-openssl-defaults:amd64 (4) ...
Setting up libencode-locale-perl (1.05-1) ...
Setting up x11-xserver-utils (7.7+8) ...
Setting up libdata-dump-perl (1.23-1) ...
Setting up libipc-system-simple-perl (1.26-1) ...
Setting up libxml-xpathengine-perl (0.14-1) ...
Setting up libio-html-perl (1.001-1) ...
Setting up libtimedate-perl (2.3200-1) ...
Setting up xdg-utils (1.1.3-2ubuntu1.20.04.2) ...
Setting up liburi-perl (1.76-2) ...
Setting up libx11-protocol-perl (0.56-7) ...
Setting up libnet-ssleay-perl (1.88-2ubuntu1) ...
Setting up libhttp-date-perl (6.05-1) ...
Setting up libfile-basedir-perl (0.08-1) ...
Setting up libfile-listing-perl (6.04-1) ...
Setting up libnet-http-perl (6.19-1) ...
Setting up libfile-desktopentry-perl (0.22-1) ...
Setting up libwww-robotrules-perl (6.02-1) ...
Setting up libhtml-parser-perl (3.72-5) ...
Setting up libio-socket-ssl-perl (2.067-1) ...
Setting up libhttp-message-perl (6.22-1) ...
Setting up libhtml-form-perl (6.07-1) ...
Setting up libfile-mimeinfo-perl (0.29-1) ...
Setting up libhttp-negotiate-perl (6.01-1) ...
Setting up libhttp-cookies-perl (6.08-1) ...
Setting up libhtml-tree-perl (5.07-2) ...
Setting up libhtml-format-perl (2.12-1) ...
Setting up libnet-smtp-ssl-perl (1.04-1) ...
Setting up libmailtools-perl (2.21-1) ...
Setting up libhttp-daemon-perl (6.06-1ubuntu0.1) ...
Setting up liblwp-protocol-https-perl (6.07-2ubuntu2) ...
Setting up libwww-perl (6.43-1) ...
Setting up libxml-parser-perl (2.46-1) ...
Setting up libxml-twig-perl (1:3.50-2) ...
Setting up libnet-dbus-perl (1.2.0-1) ...
Processing triggers for man-db (2.9.1-1) ...
user@Syrex:~/Syrex333/workspace/projects/lab09$ xdg-open https://github.com/settings/keys
user@Syrex:~/Syrex333/workspace/projects/lab09$ git config user.signingkey ${GPG_SEC_KEY_ID}
user@Syrex:~/Syrex333/workspace/projects/lab09$ git config gpg.program gpg
user@Syrex:~/Syrex333/workspace/projects/lab09$ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile
user@Syrex:~/Syrex333/workspace/projects/lab09$  echo 'export GPG_TTY=$(tty)' >> ~/.profile
user@Syrex:~/Syrex333/workspace/projects/lab09$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
-- The C compiler identification is GNU 9.4.0
-- The CXX compiler identification is GNU 9.4.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/user/.hunter
-- [hunter] [ Hunter-ID: 23f1b5a | Toolchain-ID: f845a29 | Config-ID: bf2be25 ]
-- [hunter] GTEST_ROOT: /home/user/.hunter/_Base/23f1b5a/f845a29/bf2be25/Install (ver.: 1.11.0)
-- Found GTest: /home/user/.hunter/_Base/23f1b5a/f845a29/bf2be25/Install/lib/cmake/GTest/GTestConfig.cmake (found version "1.11.0")
-- Configuring done
-- Generating done
-- Build files have been written to: /home/user/Syrex333/workspace/projects/lab09/_build
user@Syrex:~/Syrex333/workspace/projects/lab09$ cmake --build _build --target package
Scanning dependencies of target print
[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
Scanning dependencies of target demo
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/user/Syrex333/workspace/projects/lab09/_build/print-0.1.0.0-Linux.tar.gz generated.
user@Syrex:~/Syrex333/workspace/projects/lab09$  travis login --auto

Command 'travis' not found, but can be installed with:

sudo snap install travis  # version 1.8.9, or
sudo apt  install travis  # version 190101-1build1

See 'snap info travis' for additional versions.

user@Syrex:~/Syrex333/workspace/projects/lab09$ git tag -s v0.1.0.0
fatal: no tag message?
user@Syrex:~/Syrex333/workspace/projects/lab09$ git tag -v v0.1.0.0
error: tag 'v0.1.0.0' not found.
user@Syrex:~/Syrex333/workspace/projects/lab09$ git tag -s v0.1.0.0
error: gpg failed to sign the data
error: unable to sign the tag
The tag message has been left in .git/TAG_EDITMSG
user@Syrex:~/Syrex333/workspace/projects/lab09$ git tag -v v0.1.0.0
error: tag 'v0.1.0.0' not found.
user@Syrex:~/Syrex333/workspace/projects/lab09$
user@Syrex:~/Syrex333/workspace/projects/lab09$  git show v0.1.0.0
fatal: ambiguous argument 'v0.1.0.0': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
user@Syrex:~/Syrex333/workspace/projects/lab09$ git push origin main --tags
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
To https://github.com/Syrex333/lab09
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/Syrex333/lab09'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
user@Syrex:~/Syrex333/workspace/projects/lab09$ git pull origin main
warning: no common commits
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 852 bytes | 284.00 KiB/s, done.
From https://github.com/Syrex333/lab09
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
fatal: refusing to merge unrelated histories
user@Syrex:~/Syrex333/workspace/projects/lab09$ git push origin main --tags
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/Syrex333/lab09/'
user@Syrex:~/Syrex333/workspace/projects/lab09$ git push origin main --tags
SUsername for 'https://github.com':Syrex333
Password for 'https://Syrex333@github.com':
To https://github.com/Syrex333/lab09
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Syrex333/lab09'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
user@Syrex:~/Syrex333/workspace/projects/lab09$ git push --force origin main --tags
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
Enumerating objects: 261, done.
Counting objects: 100% (261/261), done.
Delta compression using up to 16 threads
Compressing objects: 100% (123/123), done.
Writing objects: 100% (261/261), 970.28 KiB | 88.21 MiB/s, done.
Total 261 (delta 104), reused 261 (delta 104)
remote: Resolving deltas: 100% (104/104), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote:
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote:
remote:     - Push cannot contain secrets
remote:
remote:
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 4289b3460b8d328b76d4a9b156c9b636968b2a2c
remote:            path: the order of execution of commands:2
remote:          - commit: 6d1bedf67d6bdb83b18bd2337f8f0f953e416ff2
remote:            path: the order of execution of commands:2
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/Syrex333/lab09/security/secret-scanning/unblock-secret/2x3UuCvVxxzV1k765rMKKiebQYg
remote:
remote:
remote:
To https://github.com/Syrex333/lab09
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: failed to push some refs to 'https://github.com/Syrex333/lab09'
user@Syrex:~/Syrex333/workspace/projects/lab09$ git push --force origin main --tags
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
Enumerating objects: 261, done.
Counting objects: 100% (261/261), done.
Delta compression using up to 16 threads
Compressing objects: 100% (123/123), done.
Writing objects: 100% (261/261), 970.28 KiB | 121.29 MiB/s, done.
Total 261 (delta 104), reused 261 (delta 104)
remote: Resolving deltas: 100% (104/104), done.
To https://github.com/Syrex333/lab09
 + 811ad36...57659f4 main -> main (forced update)
