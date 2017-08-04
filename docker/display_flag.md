# how to use -e DISPLAY flag on osx

```zsh
brew install socat
brew cask install xquartz
open -a XQuartz

socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"
# in another window
docker run -e DISPLAY=192.168.59.3:0 jess/geary
```

Note that the $DISPLAY variable is set in the XQuartz shell. In my case, the value was /private/tmp/com.apple.launchd.HxHsgt3DEr/org.macosforge.xquartz:0

[https://github.com/moby/moby/issues/8710](https://github.com/moby/moby/issues/8710)



