# RK3566 RetroArch core repo

## Dependencies

libarchive-zip-perl ( Needed for crc32)
rsync
zip

On Ubuntu 16.04 or newer, these can be easily installed by doing:
```bash
sudo apt update -y && sudo apt-get install -y libarchive-zip-perl rsync zip
```

On Redhat 6 or newer, these can be easily installed by doing:
```bash
sudo yum install perl-Archive-Zip rsync zip
```

## Add/update core

Please make sure to strip & test the cores before submitting a PR.

Copy the core to aarch64 or arm7hf and chdir to that directory. Then run:
```bash
    cd retroarch-cores
    git fetch https://github.com/christianhaitian/retroarch-cores.git && git merge https://github.com/christianhaitian/retroarch-cores.git/rg503
    ../addcore (corename)_libretro.so (ex. nestopia_libretro.so)
    git add . && git commit -m "commit message" && git push
```

Commit and make PR.

