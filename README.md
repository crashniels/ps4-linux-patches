# ps4-linux-patches

## Compilation

```bash
git clone https://github.com/crashniels/ps4-linux-patches
git clone https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git
cd linux
git checkout "tags/v$(grep -m1 "^# Linux/" ../ps4-linux-patches/.config | awk '{print $3}')"
git apply ../ps4-linux-patches/linux.patch
cp ../ps4-linux-patches/.config .config
make -j$(nproc)
```

## Installation

In the same `linux` folder after compilation, do:

```bash
sudo make modules_install && sudo make install
```

## TODO

- amdgpu smu driver to show correct gpu frequency and temperature
- hdmi converter improvments: hdr, rgb range, 120hz

## Bugs

- screen save does not work properly
- hdmi audio output does not work on some monitors
- hdmi 1440p and 2160p video output does not work on some monitors
- monitor swap is not supported
- hdmi cec is not supported
