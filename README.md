# [Potato Gaming] How to Run AAA Titles Smoothly on a $200 Refurbished Office Laptop (Literal Trash Spec)
gamescope + gamemode quick guide

[Potato Gaming] How to Run AAA Titles Smoothly on a $200 Refurbished Office Laptop (Literal Trash Spec) [Cheapskate Life]
For my buddies
MIT LICENSE / ©Fake Yoshihiro

Yeah, turns out it's actually possible. I found a goldmine of a workaround, so I'm dropping the details here. First, check the results...

60s Clip Collection (5 games): [Link to Dailymotion]

Since some of you in the thread wanted proof filmed on a phone, here’s a handheld clip. This one's a bit longer—took me forever to get this footage lol. [Link to Dailymotion]

As for the specs, see for yourself. Just your average cheap office laptop—Ryzen CPU with an integrated APU. Got it refurbished on Amazon for about 30,000 yen (roughly $200). (I did spring for the 1TB storage option, though.)

The Technical Magic
In short: I’m using Linux with the Gamescope module, tweaked to run the game at a low resolution and upscaling it via FSR with peak efficiency. Technically, it runs at 540p and uses AI upscaling to hit 1080p. I tried using the built-in game settings for this, but it was a stuttery mess—completely unplayable. Bottom line: Don't expect this to work on Windows.

The "How-To"
1. Switch your OS to Linux. Any distro that supports gamescope and gamemode will do, but Arch-based is the easiest. CachyOS is my top pick. (Check an external guide for installation. Tip: Start with a dual-boot if you’re scared of committing—single-booting can be a hurdle for beginners.)

2. Install Steam (Flatpak version) and download your games.

3. Install the required modules.

4. # Gamescope (for Flatpak)
flatpak install flathub org.freedesktop.Platform.VulkanLayer.gamescope

# Gamemode (System module)
yay -S gamemode

4. Add this to your Steam "Launch Options": DXVK_CONFIG="dxgi.maxDeviceMemory=4096" gamemoderun game-performance gamescope -h 540 -H 1080 -r 60 -F fsr -f --force-grab-cursor -- %command%

Note: If you don't have gamemode installed, the game won't launch. If you can't (or won't) install it, use this instead: DXVK_CONFIG="dxgi.maxDeviceMemory=4096" game-performance gamescope -h 540 -H 1080 -r 60 -F fsr -f --force-grab-cursor -- %command%

5. Enjoy portable AAA gaming on your potato! Thanks for reading!

Breakdown of the Launch Options
DXVK_CONFIG="dxgi.maxDeviceMemory=4096": Basically, we’re lying to the game. We’re telling it, "Hey, you only have 4GB of VRAM." By capping it at 4096MB, the game gets smart and starts conserving textures, which makes the whole thing way more stable.

gamemoderun: This triggers the Linux gamemode module. Again, if you don't have this installed, the command will crash your game, so either install it or delete this part from the string.

The Meat of the Setup (-h 540 ... -F fsr): This forces the game engine to render at 540p, then uses FSR technology to upscale that image to 1080p. (You could go down to 320p for some games, but the text gets unreadable. 540p is the sweet spot for balance.)

--force-grab-cursor: If you just upscale, the mouse coordinates get wonky and your clicks won't register. This command enables mouse capture and relative coordinate mode, letting you actually control the game on the upscaled screen.
