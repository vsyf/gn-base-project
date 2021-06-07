## GN Base Project

gn depends on chromium, copy config from webrtc.

download:
```
gclient config --unmanaged git@github.com:vsyf/gn-base-project.git --name src
gclient sync
```

build:
```
gn gen out/Default --export-compile-commands
ninja -C out/Default
./out/Default/test
```
