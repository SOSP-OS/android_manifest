SOSP Project
-------------------

Install the build packages:
-----------------------------

    sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev

Install the repo command:
-----------------------------

    mkdir -p ~/bin
    mkdir -p ~/Sosp-OS
    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    chmod a+x ~/bin/repo

GIT config (nickname, e-mail):
-----------------------------

    git config --global user.email "mail@domain.com"
    git config --global user.name "login"

To initialize your local repository use:
---------------------------------------
    cd ~/Sosp-OS
    repo init -u https://github.com/SOSP-OS/android_manifest.git -b sosp-11

Then to sync up:
----------------

    repo sync -j16 --no-clone-bundle
    
Turn on caching to speed up build :
-----------------------------------
    export USE_CCACHE=1
    ccache -M 150G
    
Start the build :
-----------------
    source build/envsetup.sh
    lunch sosp_devicecodename-userdebug
    make -j8 otapackage
