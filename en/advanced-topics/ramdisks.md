# Using RAM disks

RoboVM can be taxing for slow HDDs in old Mac Minis and MacBooks. You can  speed up the compilation and linking process by creating a RAM disk as follows:

```bash
SIZE=2048 ; diskutil erasevolume HFS+ 'RoboVM RAM Disk' `hdiutil attach -nomount ram://$((SIZE * 2048))`
```

This will mount a RAM disk using 2GB of memory under `/Volumes/RoboVM RAM Disk`. RoboVM will then use this RAM disk for its cache, which normally lives under `~/.robovm`.

The RAM disk feature will ensure that at least 400MB are available on the RAM disk by deleting those files that are least likely to contribute to the current build, e.g. files for a different architecture and OS. If your build requires more than 400MB, you can either increase the RAM disk size, or delete files under `/Volume/RoboVM RAM Disk` manually.

To remove your RAM disk, open Finder, then click the unmount button next to `RoboVM RAM Disk`.

![Unmounting a RAM disk](/images/using-ram-disks-unmount.png)
