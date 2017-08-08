# OpenWebRTC fork of cerbero

## How do I use this?

[Using this cerbero fork to build OpenWebRTC](https://github.com/EricssonResearch/openwebrtc/wiki/Building-OpenWebRTC)

## What is cerbero?

[cerbero](http://cgit.freedesktop.org/gstreamer/cerbero/) is a build system
written by GStreamer developers to build all GStreamer dependencies, GStreamer
itself and package it up into nice platform-specific SDK-like binary files.

## Why a fork?

OpenWebRTC needs some extra dependencies that are not desirable to have in
upstream cerbero. OpenWebRTC also needs some bits and pieces built in specific
ways to meet our needs.

We like collaboration and hope the use of cerbero to build OpenWebRTC will be
mutually beneficial. *All real cerbero changes are being submitted upstream!*

## ISI build instructions

* ```cd ~ # this is important! cerbero requires you to checkout in home.```

* ```git clone git@github.com:isi-research/cerbero.git```

* ```cd cerbero```

* ```sudo mkdir -p /Library/Frameworks/OpenWebRTC.framework```

* ```sudo chown -R $UID /Library/Frameworks/OpenWebRTC.framework/```

* ```mkdir -p dist```

* ```mkdir -p /Library/Frameworks/OpenWebRTC.framework/Versions/0.3```

* ```ln -sf /Library/Frameworks/OpenWebRTC.framework/Versions/0.3 dist/darwin_x86_64```

* ```./cerbero-uninstalled -c config/osx-x86-64.cbc fetch-package --full-reset --reset-rdeps openwebrtc && ./cerbero-uninstalled -c config/osx-x86-64.cbc bootstrap && ./cerbero-uninstalled -c config/osx-x86-64.cbc package -f openwebrtc #builds for macOS```

* ```./cerbero-uninstalled -c config/cross-ios-universal.cbc fetch-package --full-reset --reset-rdeps openwebrtc && ./cerbero-uninstalled -c config/cross-ios-universal.cbc bootstrap && ./cerbero-uninstalled -c config/cross-ios-universal.cbc package -f openwebrtc #builds for iOS```

* ```sudo mv /Library/Frameworks/OpenWebRTC.framework /Library/Frameworks/OpenWebRTC.framework.build```
* ```open openwebrtc-0.3.0-x86_64.pkg #follow pkg instructions to install```
* ```open openwebrtc-devel-0.3.0-x86_64.pkg #follow pkg instructions to install```
* ```open openwebrtc-devel-0.3.0-ios-universal.pkg #select 'install for me only'```
