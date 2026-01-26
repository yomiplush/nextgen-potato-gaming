# [Potato Gaming] AAA Titles on a under $200 Office Laptop

A technical guide to making "unplayable" hardware playable.
This project leverages `gamescope` and `gamemode` to push low-end refurbished laptops to their absolute limits.

## Overview
This setup is optimized for sub-$200 refurbished office laptops—specifically those powered by Ryzen CPUs with integrated APUs. 

### The Core Logic
We offload the upscaling process from the game engine to the Linux compositor level using **Gamescope**. 
By rendering natively at 540p and upscaling to 1080p via FSR, we achieve a level of frame stability and smoothness that is simply unattainable on Windows.

---

## Proof of Concept
### * [60s Gameplay Collection (5 Titles)
* **Clips:** [© FROMSOFTWARE / ELDENRING](https://www.dailymotion.com/video/x9yiu50)
* * **Clips:** [© FROMSOFTWARE / Dark Souls III](https://www.dailymotion.com/video/x9yiu9y)
  * * **Clips:** [© CAPCOM / Resident Evil 4](https://www.dailymotion.com/video/x9yiumi)
    * * **Clips:** [© KOJIMA PRODUCTION / Death Strandings Director's Cut](https://www.dailymotion.com/video/x9yiwwa)
      * * **Clips:** [© Blizzard entertainment / Diablo IV](https://www.dailymotion.com/video/x9yix0q)
* **Handheld:** [Off-screen Footage (Direct Capture)](https://www.dailymotion.com/video/x9yisbs) 
  * *Filmed on a smartphone to prove no external GPUs or tricks were used.*

## Hardware Spec (The Potato)
* **Device:** Generic Amazon Refurbished Office Laptop
* **CPU/GPU:** Ryzen APU (Integrated Graphics)
* **Storage:** Upgraded to 1TB (Recommended for AAA libraries)
* **OS:** Linux (**CachyOS** highly recommended for performance)
<br>
<img src="https://for-github-resource.pages.dev/neofetch.webp" width="500" alt="neofetch"><br>
<img src="https://for-github-resource.pages.dev/laptop.webp" width="500" alt="laptop"><br>
---

## Installation & Setup

### 1. Environment
**Forget Windows.** You need a Linux environment that natively supports `gamescope` and `gamemode`. 
Arch-based distributions are the most straightforward for this setup.

### 2. Install Required Modules
```bash
# Gamescope (Required for Flatpak Steam)
flatpak install flathub org.freedesktop.Platform.VulkanLayer.gamescope
# Gamemode (System-wide optimization)
yay -S gamemode
```

3. Steam Launch Options
Copy and paste the following into your game's Launch Options:

```Steam Launch Options
DXVK_CONFIG="dxgi.maxDeviceMemory=4096" gamemoderun game-performance gamescope -h 540 -H 1080 -r 60 -F fsr -f --force-grab-cursor -- %command%
```

Note: If you cannot (or do not want to) install gamemode, 
remove gamemoderun from the string or the game will fail to launch.

Technical Deep Dive: The Commands

Parameter,Function
dxgi.maxDeviceMemory=4096,"Lies" to the game, capping VRAM at 4GB.<br>
This forces engines to be smarter with texture streaming, <br>
preventing crashes on shared-memory APUs."<br>
gamemoderun,Requests the OS to prioritize CPU/GPU resources for the game process.<br>
-h 540 -H 1080,Sets the internal render resolution to 540p and the output window to 1080p.<br>
-F fsr,Enables AMD FidelityFX Super Resolution for high-quality upscaling.<br>
--force-grab-cursor,"Critical. Ensures mouse input maps correctly to the upscaled resolution <br>
(prevents "invisible wall" cursor issues)."<br>
<br>
License & Disclaimer<br>
No claims, No returns<br>
MIT LICENSE / © YomiPlush<br>
<br>
Happy gaming on your potato!<br>
<br>
<img src="d4cat.webp" width="500" alt="Diablo IV memes"><br>
