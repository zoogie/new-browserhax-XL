# new-browserhax-XL

## Thanks 
- webkit test cases 
- MrNbaYoh for his blogs
- Yellows8 for the hbmenu loader code: https://github.com/yellows8/3ds_browserhax_common

## Intro

New-browserhax-XL is another primary userland exploit for the new3ds browser, Skater. It's the successor to [new-browserhax](https://github.com/zoogie/new-browserhax), which bravely fell in battle against firmware 11.14. RIP.

## What's needed

A new3ds (or new2ds) on firmware:<br>
```
11.14.0-46 on all 4 new3ds regions US,EU,JP,KR
```

## Directions 

1) In the release folder, find your region (USA, EUROPE, JAPAN, KOREA) and take all files *inside* that folder and put them on the root of your sd card. Do not copy the entire region folder over, just its contents.
2) Place the homebrew launcher boot.3dsx from [here](https://github.com/fincs/new-hbmenu/releases/tag/v2.2.0) also on the root of your sd card.
3) With wifi on and working, scan [this QR](http://api.qrserver.com/v1/create-qr-code/?color=000000&bgcolor=FFFFFF&data=https%3A%2F%2Fzoogie.github.io%2Fweb%2Fnbhax-xl&qzone=1&margin=0&size=400x400&ecc=L) after pressing L+R should buttons together and tapping the QR button on the bottom screen. The link to the sploit page is https://zoogie.github.io/web/nbhax-xl/ if you want to type it in manually and/or bookmark it.
4) The exploit should then immediately flash colors and load the homebrew menu. Make sure to add homebrews to the sdmc:/3ds folder first in order to have something to run. See other guides online about what you can do with homebrew.

## Exploit details

This is a simple stack smash that occurs when a .css @import command contains a '#' (url fragment) at the beginning of the url. The webkit test demo this is based on can be found [here](https://github.com/WebKit/webkit/blob/master/LayoutTests/http/tests/css/css-imports-url-fragment.css).

## Troubleshooting

- Problem: The 3ds freezes on a yellow screen.<br>
Solution: Try again. Boot rate is about 75-80%. This has always been an issue with *hax homebrew and not specific to this implementation.* If this keeps occurring over and over, it's likely being caused by running browserhax while cfw (luma3ds + boot9strap) is already installed -- don't do this! Follow https://3ds.hacks.guide for proper instructions on how to launch .3dsx homebrew under cfw. Hard freezing with regular screens (ie no solid colored screen) can also indicate running under cfw.

- Problem: I get a "An exception occured" black screen with white text on both screens.<br>
Solution: You already have cfw and there's no reason to run browserhax. Consult [this](https://3ds.hacks.guide/finalizing-setup.html) for instructions on how to run homebrew properly under cfw.

- Problem: The 3ds freezes on some other color screen or "An error has occured" prompt shows up.<br>
Solution: Make sure you have *all* the correct files. Check your region is correct.<br>
At minimum, make sure to have the below 3 files in the sd root as shown.

```
sdmc:/arm11code.bin
sdmc:/browserhax_hblauncher_ropbin_payload.bin
sdmc:/boot.3dsx
```
Note that these are the same files used as in the previous new-browserhax, so no need to change them if they're already there.

- Problem: I still can't get the exploit to work and the three solutions above didn't help.<br>
Solution: First, tap the bottom left star icon, then select top right History tab, and delete History button at the bottom. Then go to your browser's settings and select Delete Cookies. Now create a bookmark with https://zoogie.github.io/web/nbhax-xl/ as the address (or just edit an existing bookmark). Exit the browser, then launch it again, and then finally launch that nbhax-xl bookmark you just made. It may also be helpful to power cycle the 3ds in between attempts if the exploit is still being stubborn.

## FAQ
Q: Will you support old3ds, old2ds?<br>
A: Planned. I already have a working exploit for spider but it's pretty unstable. Needs more time.

Q: Can I install [unSAFE_MODE](https://github.com/zoogie/unSAFE_MODE) with this to get cfw?<br>
A: Absolutely, be my guest : ) You can boot slotTool.3dsx and install the hacked wifi slots, then run the unSAFE_MODE exploit. No explicit directions will be given for that here, but guides should pop up soon with directions.

Q: Where did this browser exploit come from originally?<br>
A: https://github.com/WebKit/webkit/blob/master/LayoutTests/http/tests/css/css-imports-url-fragment.css

Q: I looked at the source and noticed the html file seems to import itself as a .css, wat?<br>
A: That's an html quirk that I don't quite understand myself, but it's convenient. It's actually not part of the vuln; I could've used a separate file for the .css code, but chose not to.

Q: Why did you name it new-browserhax-XL?<br>
A: I am creatively bankrupt.

Q: Will this exploit be fixed in a firmware update?<br>
A: Last time I suggested about 50% odds new-browserhax being fixed which turned out to be 100% odds. So I guess that means we average those two and get a 75% chance of it being fixed this time :p<br>I really don't know.