# ghclogo

![20210526195830!Display_hack_bitmap](https://github.com/user-attachments/assets/ec7222b7-d693-43d5-a5d8-bdea0f94dea7)

See details at: <a href="https://garoa.net.br/wiki/Garoa_Xuning#Protetor_de_Tela">https://garoa.net.br/wiki/Garoa_Xuning#Protetor_de_Tela</a>

## Downloading the necessary files

Clone **slock** from the [suckless.org](https://suckless.org) project:

```
git clone https://git.suckless.org/slock
```

Download the patch and save it inside the `slock` directory:

```
wget -P slock https://tools.suckless.org/slock/patches/dwmlogo/slock-dwmlogo-20210324.diff
```

Clone this repository:

```
git clone https://github.com/f3hat/ghclogo.git
```

Your current directory should look like this:

<img width="480px" src="https://github.com/user-attachments/assets/2cd41be1-5788-4739-8a8b-820c6df17998" />

## Option A: Applying patch via `.diff` (from suckless.org) and `.h` (from this repository)

Run:

```
cd slock
patch -p1 < *.diff
```

This will apply the patch to the files and lines described in the `slock-dwmlogo-*.diff` file we downloaded (a simple `less *.diff` will help you inspect what exactly is being changed).

Then run:

```
rm *.def.h && cp ../ghclogo/*.def.h .
```

This will remove the `config.def.h` file modified by the patch and copy into the current directory the `config.def.h` file we downloaded.

## Option B: Applying patch only via `.diff` (from this repository)

Run:

```
cd slock
patch -p1 < ../ghclogo/*.diff
```

Nice and simple!

## Compiling

Install the libraries `xrandr.h` (a [slock](https://tools.suckless.org/slock) dependency), `xinerama.h` and `xft.h` (both dependencies of the [patch](https://tools.suckless.org/slock/patches/dwmlogo)):

```
sudo apt install libxrandr-dev libxinerama-dev libxft-dev
```
Assuming you're using a Debian-based distro.

Then run:

```
cd slock
sudo make clean install
```

## Running

Simply execute:

```
slock
```
