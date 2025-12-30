# Compact Keyboard1 - User Guide

## Welcome!

Congratulations on your new custom keyboard! This guide will help you get started, even if you've never used a custom keyboard before.

### What Makes This Keyboard Special?

This is a **custom mechanical keyboard** with special features:
- **Ortholinear Layout:** Keys arranged in a perfect grid (like a spreadsheet) instead of the staggered rows you're used to
- **Programmable Keys:** You can customize what each key does
- **RGB Lighting:** Beautiful programmable underglow lighting with different animation effects
- **Split Spacebar:** Two spacebar keys instead of one for a unique feel

## Quick Start

1. **Plug it in** to your computer via USB
2. **Start typing** - it works just like any other keyboard!
3. **RGB lights** should turn on automatically and breathe (fade in and out)
4. **That's it!** Your keyboard is ready to use

## Keyboard Specifications

- **Total Keys:** 75 keys
- **Layout Style:** Ortholinear (keys in straight columns and rows)
- **Processor:** RP2040 (the brain of the keyboard)
- **RGB LEDs:** 10 programmable color-changing lights underneath
- **Bootloader:** RP2040 (used for updating firmware)

## Keyboard Layout Explained

### What is an Ortholinear Layout?

Instead of the staggered (zigzag) rows you're used to on a regular keyboard, this keyboard has keys arranged in straight columns and rows - like a spreadsheet. This takes a little getting used to, but many people find it more ergonomic!

### Layer 0 - Default Layer (What You Use Daily)

This is the main layer with numbers, letters, and symbols. It looks and works like a normal QWERTY keyboard.

```
Row 1: 1   2   3   4   5   6   7   8   9   0   -   =   [   ]   \
Row 2: Tab Q   W   E   R   T   Y   U   I   O   P   [   ]  Back Space  Delete
Row 3: Esc A   S   D   F   G   H   J   K   L   ;   '   \   Enter      Up Arrow
Row 4: LShift Z  X   C   V   B   N   M   ,   .   /  RShift  Up  Down  Down
Row 5: LCtrl LGui LAlt   Space Bar (1.25u)   Space Bar (1.25u)   RAlt RCtrl ← ↓ →
```

**Note:** The two space bars work just like a regular spacebar - use whichever feels more comfortable!

### Layer 1 - Function & RGB Controls (Advanced Features)

To access the special functions (like controlling the RGB lights), you need to enter **Function Mode**.

#### How to Enter Function Mode:

Press and hold **Left Control** + **Left Alt** (or any modifier combination) while pressing the RGB control keys below.

```
Row 1: F1  F2  F3  F4  F5  F6  F7  F8  F9  F10 F11 F12
Row 2: (empty) RGB_TOG (empty)
Row 3: (empty) (empty) (empty) (empty) RGB_HUI RGB_SAI RGB_VAI
Row 4: (empty) (empty) (empty) (empty) RGB_MOD RGB_SPI
```

## Controlling the RGB Lights (Easy Guide!)

Your keyboard has beautiful programmable lights underneath! Here's how to control them:

### What Do These Controls Do?

| What You Want | How to Do It | Location |
|---------------|-------------|----------|
| **Turn lights on/off** | Mod + Q | Q key on Layer 1 |
| **Change color** | Mod + H (press multiple times) | H key on Layer 1 |
| **Make colors brighter** | Mod + K (press multiple times) | K key on Layer 1 |
| **Make colors more vivid** | Mod + J (press multiple times) | J key on Layer 1 |
| **Change light animation** | Mod + N (press multiple times) | N key on Layer 1 |
| **Speed up animation** | Mod + M (press multiple times) | M key on Layer 1 |

### What is "Mod"?

"Mod" means holding down a modifier key. Your keyboard has these modifier keys:
- **Left Control** (Ctrl)
- **Left Windows** (Win/GUI)
- **Left Alt** (Alt)

**Example:** To toggle the lights on/off:
1. Hold down **Left Control**
2. While holding it, press **Q**
3. Release both keys
4. The lights should turn on or off!

### Available Light Animations

Your keyboard has 5 different light shows to choose from:

1. **Static Light** - Solid color, no animation (lights stay still)
2. **Breathing** - Lights fade in and out slowly (like breathing) - *This is the default*
3. **Static Gradient** - Fixed color gradient pattern
4. **RGB Test** - Cycles through all colors for testing
5. **Alternating** - Alternates between two different colors

### Quick RGB Tutorial

**Step 1: Turn on the lights**
- Hold Ctrl + Press Q (if lights are off)

**Step 2: Change the color**
- Hold Ctrl + Press H multiple times until you like the color

**Step 3: Adjust brightness**
- Hold Ctrl + Press K multiple times (more presses = brighter)

**Step 4: Try different animations**
- Hold Ctrl + Press N multiple times to cycle through different light effects

## Updating Your Keyboard (Firmware Flashing)

**Don't worry if you're new to this!** Firmware is just the software that runs on your keyboard. Here's how to update it in simple terms.

### What You'll Need

1. **QMK Toolbox** (free software) - Download from: https://github.com/qmk/qmk_toolbox/releases
   - This is the easiest way for beginners!

2. **A .hex file** - This is your keyboard's firmware code (the instructions)

### How to Update Your Keyboard (Easy Method)

**Step 1:** Download and install QMK Toolbox on your computer

**Step 2:** Open QMK Toolbox

**Step 3:** Select your firmware file (.hex)
- Click "Open" and find your firmware file

**Step 4:** Put your keyboard in bootloader mode (ONE of these methods):
- **Method A:** Unplug your keyboard, hold the **top-left key (1)**, plug back in, release the key
- **Method B:** Hold the reset button on the bottom of your keyboard for 2 seconds

**Step 5:** Click "Flash" in QMK Toolbox

**Step 6:** Wait for it to finish (usually takes 5-10 seconds)

**Step 7:** Your keyboard will restart automatically - done!

### If Something Goes Wrong

- **Keyboard not detected?** Try a different USB cable
- **Firmware won't flash?** Make sure you're in bootloader mode (try the reset button again)
- **Still having trouble?** Check the QMK documentation: https://docs.qmk.fm/

### Advanced: Command Line Method

If you're comfortable with a terminal:
```bash
cd qmk_firmware
qmk flash -kb compact_keyboard1 -km default
```

When prompted, put your keyboard into bootloader mode using one of the methods above.

## Understanding Your Keyboard's Lights

### What Are These LEDs?

Your keyboard has **10 WS2812 GRB addressable LEDs**. In plain English: you have 10 smart color-changing lights that can individually display any color!

- **WS2812** = The type of LED chip (a smart chip that can display any color)
- **GRB** = The color format (Green, Red, Blue - how the light outputs colors)
- **Addressable** = Each LED can be controlled individually or as a group

### Light Settings You Can Customize

In the `config.h` file (for advanced users):

| Setting | What It Does | How to Change |
|---------|------------|---------------|
| `RGBLED_NUM 10` | Number of lights | Change the "10" to however many LEDs you have |
| `RGBLIGHT_DEFAULT_MODE` | Starting animation | Change to STATIC_LIGHT, BREATHING, etc. |
| `RGBLIGHT_LIMIT_VAL 255` | Maximum brightness | Lower numbers = dimmer max brightness |
| `RGB_DI_PIN GP22` | Which pin controls lights | Don't change unless you rewired! |

### Files You Might Edit

- **config.h** - Main settings file
- **rules.mk** - Feature enable/disable file

**Note:** You'll need to reflash your keyboard after making changes!

## Special Keyboard Features Explained

### Bootmagic (Easy Recovery)

**What is it?** A safety feature that lets you access special modes without needing extra buttons.

**How to use it:**
1. Hold down the **top-left key (1)** on your keyboard
2. Plug your keyboard into your computer (while still holding key 1)
3. Release key 1
4. You're now in bootloader mode (safe mode for updates)

### Debouncing (Technical but Important)

**What is it?** Your keyboard uses a 5ms debounce setting, which means it waits 5 milliseconds before registering a key press. This prevents "bouncing" (registering the same key multiple times from one press).

**In plain English:** It makes sure your keyboard registers each keystroke exactly once, not accidentally double-pressing keys.

**If keys feel sluggish:** This is normal! It's preventing errors.

### NKRO (N-Key Rollover)

**What is it?** NKRO lets you press many keys at the same time without them being ignored.

**In plain English:** You can press 10+ keys simultaneously (great for gaming!) and the keyboard will register all of them.

**Example:** Hold Shift + Control + Alt + Space + Q + W + E - the keyboard will recognize all of them!

### Other Features

- **Bootmagic Support** - Access bootloader easily (see above)
- **Media Controls** - Some keyboards support extra controls (volume, play/pause)
- **Mouse Keys** - Some keyboards can emulate a mouse (optional feature)
- **Full Customization** - You can reprogram any key to do anything

## Troubleshooting (Help!)

### "My keyboard isn't being recognized by my computer"

**Try this:**
1. Use a different USB cable (some cables only charge, don't transmit data)
2. Try a different USB port on your computer
3. Restart your computer
4. Check Device Manager (Windows) or System Information (Mac) to see if the keyboard appears

**If still not working:**
- Your keyboard might be in a bad state - try entering bootloader mode and see if it appears then
- Contact the manufacturer for support

### "The lights won't turn on"

**Try this:**
1. Make sure the lights are plugged in correctly to the keyboard
2. Try toggling them with Ctrl + Q
3. Check that the USB power is connected (lights need power!)
4. Restart your computer

**If still dark:**
- Your LED might be burned out (sometimes happens)
- Check the LED connections with a flashlight to make sure they're firmly plugged in

### "Some keys aren't responding"

**Try this:**
1. Unplug the keyboard and plug it back in
2. Make sure nothing is blocking the keys
3. Check that you're not accidentally on the function layer

**If a key still doesn't work:**
- The key switch might be broken (the physical switch under the key)
- The keyboard might need to be flashed again
- Contact the manufacturer

### "The lights keep flickering or acting weird"

**Try this:**
1. Make sure your USB cable is plugged in firmly at both ends
2. Try a different USB port (some ports provide less power)
3. Reduce the brightness with Ctrl + K (fewer presses)

**If it's still flickering:**
- Your USB power might be unstable
- Try a powered USB hub
- Try a different computer to test

### "I can't enter bootloader mode"

**Try this:**
1. Use the **key combo method:**
   - Unplug keyboard
   - Hold down the **1 key**
   - Plug in keyboard
   - Wait 2 seconds
   - Release the key

2. If that doesn't work, try the **reset button method:**
   - Look for a small button on the bottom of the keyboard
   - Use a paperclip to press it for 2 seconds
   - Release it

3. Try both methods 2-3 times

**If you're still stuck:**
- Your keyboard might have a hardware issue
- Ask for help on the QMK Discord: https://discord.gg/Uq7gcHh

### "I'm still having problems!"

**Here's where to get help:**

1. **QMK Official Documentation:** https://docs.qmk.fm/
2. **QMK Discord Community:** https://discord.gg/Uq7gcHh (super helpful!)
3. **GitHub Issues:** Check the QMK firmware repo for your keyboard
4. **Check the README:** Look for a readme.md file in your keyboard folder

## Frequently Asked Questions (FAQ)

### Q: Why do the keys look weird? (Ortholinear layout)
**A:** This is called an "ortholinear" layout - keys are in straight rows instead of staggered. It takes a few days to get used to, but many people find it more comfortable! Give it a week before deciding.

### Q: Can I use this keyboard with Mac or Linux?
**A:** Yes! QMK keyboards work with Windows, Mac, and Linux. Just plug and play!

### Q: Can I change what the keys do?
**A:** Yes, but it requires editing the keymap file and reflashing the firmware. It's fairly advanced, but you can learn from the QMK documentation.

### Q: Do the lights drain battery?
**A:** This is a wired keyboard (plugged in), so there's no battery. The lights are powered by your USB connection.

### Q: Can I make my own custom light animations?
**A:** Yes, but it requires programming knowledge. Check the QMK RGB documentation for details.

### Q: What happens if I accidentally break a key?
**A:** You can just replace the switch (the thing under the key). Most keyboards have hot-swap switches that pop out easily.

### Q: Is this keyboard loud?
**A:** This depends on the switch type (mechanical switches vary). Generally, mechanical keyboards are louder than regular keyboards. Check what switches you have!

### Q: Why is my keyboard typing double letters sometimes?
**A:** This might be a debounce issue. The 5ms debounce setting should prevent this. If it keeps happening, you might need to adjust the debounce time in config.h (but 5ms is usually good).

### Q: Can I use this with a phone or tablet?
**A:** Only if your phone/tablet supports USB keyboards (most do via a USB-C adapter). The keyboard is designed for computers though.
