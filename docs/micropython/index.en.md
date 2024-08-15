# MicroPython documentation

## Start micropython
Ensure your badge is upgraded to the latest version.
Boot the badge in de main menu and choose 'MicroPython'. The badge reboots and you get a black screen (the dark magic is inside).

By default, the badge will not reboot into MicroPython on reset.
Should you want this, you need to confirm the switch to MicroPython was successful.
You can do this like this:

```
    from fri3d import boot
    boot.persist()
```
Note that now you no longer can get back to the main menu.
To switch back you need to do this:
```
    from fri3d import boot
    boot.main_menu()
```

## Badge Examples
There are examples installed on the badge itself.

You can explore these with [ViperIDE](https://fri3dcamp.github.io/viper/)

## Flash the default fri3d micropython firmware
download firmware from
https://github.com/cheops/fri3d-ota/tree/main/ota/fri3d_badge_2024  
select the version and then the `*.zip` file in that folder

flasher app 
https://fri3d-flasher.vercel.app/#/

If your download fails, you might have more success if you put the badge in DOWNLOAD mode manually:
- PRESS + HOLD the START button
- PRESS the RESET button (while HOLDING the START button)
- the badge has now restarted in download mode

after the download you might need to reset the badge to boot normally (PRESS the RESET button)


## How to run a local file
Install `mpremote` [howto](https://docs.micropython.org/en/latest/reference/mpremote.html)

TLDR; `pip install mpremote`

```sh
mpremote resume run local_test_file.py
```
Unfortunately `Thonny` interrupts the startup of the badge when connecting, leaving some items (spi, display) in an undefined state.  
The same for `mpremote` if not supplied with the `resume` argument.

## how to copy a file to the badge
```sh
mpremote resume fs cp local_path/file.jpg :file.jpg
```

## Micropython libraries
Micropython [quick reference for the esp32](https://docs.micropython.org/en/v1.22.0/esp32/quickref.html)

Micropython standard libraries overview [doc](https://docs.micropython.org/en/v1.22.0/library/index.html)

The badge has [lvgl](lvgl) built-in.

Buttons demo [demo_buttons.py](https://github.com/cheops/badge_2024_micropython/blob/lv_indev/fri3d/modules/demos/demo_buttons.py)

Joystick demo [demo_joystick.py](https://github.com/cheops/badge_2024_micropython/blob/lv_indev/fri3d/modules/demos/demo_joystick.py)

Other interesting links
- https://github.com/peterhinch/micropython-samples
- https://github.com/mcauser/awesome-micropython

## micropython game ideas
- https://hackaday.com/2021/05/25/simple-micropython-game-is-a-30-minute-game-dev-course/
- pinball [link1](https://github.com/russhughes/s3lcd/blob/main/examples/pinball.py) or [link2](https://github.com/russhughes/st7789_mpy/blob/master/examples/pinball.py)
- [gameESP](https://github.com/cheungbx/gameESP-micropython)
- [snake](https://github.com/cheops/badge_2024_micropython/blob/s3lcd/fri3d/modules/demos/snake.py)
