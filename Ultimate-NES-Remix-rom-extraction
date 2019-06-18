
# How to extract ROMs from _Ultimate NES Remix_

`by: Glazed_Belmont`


![](https://i.imgur.com/k8LbKCj.jpg)

Hi, in this tutorial, I'll show you how to extract the games in _Ultimate NES Remix_ and convert them to make them playable on an emulator.

Firstly, here's the list of the games we will be extracting:
- Balloon Fight
- Donkey Kong
- Donkey Kong Jr.
- Dr. Mario
- Excitebike
- Kid Icarus
- Kirby's Adventure
- Mario Bros.
- Metroid
- Punch-Out!!
- Super Mario Bros.
- ~~Super Mario Bros.: The Lost Levels~~
- Super Mario Bros. 2
- Super Mario Bros. 3
- The Legend of Zelda
- Zelda II: The Adventure of Link 

**So, before we start, you will need this:**
- A 3ds console with CFW (Luma)
- Access to an hex editor (HxD or Godmode9)
- A cartridge of Ultimate NES Remix
***

**Section I** : **Dumping the roms**

1) First, open Godmode9 by booting the console while holding the Start button (or the button you've assigned it to)

2) Navigate to `[C:] GAMECART`, and press A

![](https://i.imgur.com/QDyh0UL.png)

3) Hover the `.trim.3ds` and press A

![](https://i.imgur.com/ouTYPfz.png)

4) Press A on `NCSD image options...` and then press A on `Mount image to drive`

![](https://i.imgur.com/GK1oLdV.png)

5) Press A when asked to enter the path

![](https://i.imgur.com/8jVjn86.png)

6) Now, we are inside the gamecart's rom, you will see multiple things including a directory called `content0.game`, press A on that one

![](https://i.imgur.com/2A1TZRO.png)

7) Press A on the `romfs` directory

![](https://i.imgur.com/2sw2YDr.png)

8) Press A on the `emu` directory

![](https://i.imgur.com/rwYnIkv.png)

9) Hover the `rom` directory and press R+A on it

![](https://i.imgur.com/gNpNQdv.png)

10) Press A on `Copy to 0:/gm9/out`

![](https://i.imgur.com/hod0qFB.png)

Your `rom` folder will now be in `SD:/gm9/out`

**Section II : Editing the roms**

So, let me give you a bit of context before continuing with the guide, the roms we just extracted aren't playable in an emulator currently. Why, you may ask? Because they aren't using the correct header. They have a TNES header, and we need them to be using a INES header.

Normally, this would require quite a lot of research but don't worry, I have converted all the possible roms for you and prepared a list of the bytes you would have to edit.

## DISCLAIMER

**Some roms will not work even if you give them a INES header because they are FDS (Famicom Disk System) roms.**

This includes:
- `ICARUS`
- `METROID`
- `SMB2` (Lost Levels)
- `ZELDA2` (Adventure of Link)

Those are the filenames of the files inside the `rom` folder we just dumped.

***
 
**Section II : Fixing the header**

Oh boy, that's the tricky part.
For the sake of simplicity, I'll be using GM9's hex editor for my examples.

So, the first 4 bytes will **ALWAYS** be `4E 45 53 1A` and the 8th byte is always `00` , if byte 9-16 aren't all `00`, you're most likely trying to edit a FDS rom which __will not work__ if you fix the header this way.

That`s a TNES header

![](https://i.imgur.com/8hcQCXb.png)

and that's a INES header

![](https://i.imgur.com/dvoVMIH.png)

The difference is quite visible, they are totally different

So, here's the list of the INES headers that I've discovered:

The words that are `like this` are the filenames of the roms, the name after it is the game it corresponds to. If your filename isn`t on this list, then it is a FDS rom

- `BALLOON`/ Balloon fight: `4E 45 53 1A 01 01 00 00`
- `BIKE`/Excitebike: `4E 45 53 1A 01 01 01 00`
- `DK1`/Donkey Kong: `4E 45 53 1A 01 01 00 00`
- `DK2`/ Donkey Kong Jr.: `4E 45 53 1A 01 01 01 00`
- `DOCTOR`/Dr. Mario: `4E 45 53 1A 02 04 10 00`
- `UsIKARUS`/ Kid Icarus: `4E 45 53 1A 08 00 11 00`
- `KIRBY`/`UsKirby`/ Kirby's Adventure: `4E 45 53 1A 20 20 42 00`
- `MB`/ Mario Bros: `4E 45 53 1A 01 01 00 00`
- `PUNCH`/Mike Tyson's Punch-out!!: `4E 45 53 1A 00 10 90 00`
- `SMB1`/ Super Mario Bros: `4E 45 53 1A 02 01 01 00`
- `SMB3`/`UsSMB3`/ Super Mario Bros 3: `4E 45 53 1A 10 10 40 00`
- `UsSMBUSA`/`SMBUSA`/ Super Mario Bros 2 (US): `4E 45 53 1A 00 10 40 00`
- `UsMETROID`/ Metroid: `4E 45 53 1A 08 00 10 00`
- `ZELDA`/`UsZELDA`/The Legend of Zelda: `4E 45 53 1A 08 00 12 00`
- `UsZELDA2`/The Adventure of Link: `4E 45 53 1A 08 19 12 00`


So, if you have a basic knowledge of hex editing, you'll pretty much know what to do, change the highlighted bytes from the TNES screenshot to the ones corresponding to your game.

For those of you who do not have experience in hex editing, I'll make a short tutorial:

1) **FIRST OF ALL, MAKE A COPY OF THE FILE BEFORE EDITING IT** Press Y on the rom, go somewhere else in your sd card and then press Y again and press A on `copy path`

2) Press A on your rom and press A on `Show in Hexeditor` that's gonna take you to the hex editing screen.

_Basic controls in the Hexeditor_

Pressing A once will make a byte go red, that's the byte you're editing, you can freely move around with the D-pad.

Holding A while having a byte in red is going to edit it. Any input on the D-pad will either change the 1st part of the byte or the 2nd part.

`⬅️ and ➡️`  will edit the first number so if I were to press `➡️` while holding A on the byte `00`, the byte would become `10`

`⬆️ and ⬇️` will edit the second number so if I were to press `⬆️` while holding A on the byte `00` , the byte would become `01`

Also, the order of the numbers are different, it goes like this:
`0 1 2 3 4 5 6 7 8 9 A B C D E F`

3) With those controls in mind, edit each of the 8 bytes to match the corresponding header.

***

### Acknowledgements 

I'd like to thank Validusername16#9643,  he showed me how the TNES and INES worked and taught me how to convert the headers, without his help, this tutorial wouldn't have been possible.

_~_ ![](https://i.imgur.com/s2O6pJd.png) _GlaZed_Belmont_
