# yymm's Helix Layout for four rows

QMK commit latest(2018-09-06): 7f7c278

## Layout

QWERTY
```
 ,------------------------------------------.                  ,-----------------------------------------.
 | ESC   |   Q  |   W  |   E  |   R  |   T  |                  |   Y  |   U  |   I  |   O  |   P  |  -_  |
 |-------+------+------+------+------+------|                  |------+------+------+------+------+------|
 |Tab/Ctl|   A  |   S  |   D  |   F  |   G  |                  |   H  |   J  |   K  |   L  |   ;  |  '"  |
 |-------+------+------+------+------+------|                  |------+------+------+------+------+------|
 | Shift |   Z  |   X  |   C  |   V  |   B  |                  |   N  |   M  |   ,  |   .  |   /  |  \|  |
 |-------+------+------+------+------+------+-----------+------+------+------+------+------+------+------|
 | ADJUST|      |      |      | Alt  |Raise |Space/Lower| Bksp |Enter | GUI  |      |      |      |      |
 `-------------------------------------------------------------------------------------------------------'
```

EUCALYN
```
 ,------------------------------------------.                  ,-----------------------------------------.
 | ESC   |   Q  |   W  |   ,  |   .  |   ;  |                  |   M  |   R  |   D  |   Y  |   P  |  -_  |
 |-------+------+------+------+------+------|                  |------+------+------+------+------+------|
 |Tab/Ctl|   A  |   O  |   E  |   I  |   U  |                  |   G  |   T  |   K  |   S  |   N  |  '"  |
 |-------+------+------+------+------+------|                  |------+------+------+------+------+------|
 | Shift |   Z  |   X  |   C  |   V  |   F  |                  |   B  |   H  |   J  |   L  |   /  |  \|  |
 |-------+------+------+------+------+------+-----------+------+------+------+------+------+------|------|
 | ADJUST|      |      |      | Alt  |Raise |Space/Lower| Bksp |Enter | GUI  |      |      |      |      |
 `-------------------------------------------------------------------------------------------------------'

```

## Layers

|Priority|number|name|description|
| ---- | ---- | --- | --- |
|high|16|Adjust|Functions|
||4|Raise|Numeric charactors|
||3|Lower|Other charactors|
|low|0|Qwerty|QWERTY layout(base)|

### Lower
```
 ,-----------------------------------------.             ,-----------------------------------------.
 |      |   1  |   2  |   3  |   4  |   5  |             |   6  |   7  |   8  |   9  |   0  |      |
 |------+------+------+------+------+------|             |------+------+------+------+------+------|
 |      |      |      |      |      |  =+  |             |  `~  |      |  UP  |      |      |      |
 |------+------+------+------+------+------|             |------+------+------+------+------+------|
 |      |      |      |      |      |  [{  |             |  }]  | LEFT | DOWN | RGHT |      |      |
 |------+------+------+------+------+------+-------------+------+------+------+------+------+------|
 |      |      |      |      |      |      |      |      |      |      |      |      |      |      |
 `-------------------------------------------------------------------------------------------------'
```

### Raise
```
 ,-----------------------------------------.             ,-----------------------------------------.
 |      |   !  |   @  |   #  |   $  |   %  |             |   ^  |   &  |   *  |   (  |   )  |      |
 |------+------+------+------+------+------|             |------+------+------+------+------+------|
 |      |      |      |      |      |      |             | MS_LT| MS_DN| MS_UP| MS_RT| MS_WU| MS_WD|
 |------+------+------+------+------+------|             |------+------+------+------+------+------|
 |      |      |      |      |      |      |             | MS_CL| MS_RC|      |      |      |      |
 |------+------+------+------+------+------+-------------+------+------+------+------+------+------|
 |      |      |      |      |      |      |      |      |      |      |      |      |      |      |
 `-------------------------------------------------------------------------------------------------'
```

### Adjust (Lower + Raise)
```
 ,-----------------------------------------.             ,------------------------------------------.
 |      | Reset|      |      |      | Mac  |             | Win  |      |Qwerty|Eucalyn|Dvorak|      |
 |------+------+------+------+------+------|             |------+------+------+-------+------+------|
 |      |      |      |Aud on|Audoff|      |             |      |RGB ON| MODE+| HUE+  | SAT+ | VAL+ |
 |------+------+------+------+------+------|             |------+------+------+-------+------+------|
 |      |      | Next | Vol- | Vol+ | Play |             |      |RGBRST| MODE-| HUE-  | SAT- | VAL- |
 |------+------+------+------+------+------+-------------+------+------+------+-------+------+------|
 |      |  F1  |  F2  |  F3  |  F4  |  F5  |  F11 |  F12 |  F6  |  F7  |  F8  |  F9   |  F10 |      |
 `--------------------------------------------------------------------------------------------------'
```

## Customize

see `rules.mk`
```
# Helix keyboard customize
# you can edit follows 7 Variables
HELIX_ROWS = 4              # Helix Rows is 4 or 5
OLED_ENABLE = yes           # OLED_ENABLE
LOCAL_GLCDFONT = yes        # use each keymaps "helixfont.h" insted of "common/glcdfont.c"
LED_BACK_ENABLE = yes       # LED backlight (Enable WS2812 RGB underlight.)
LED_UNDERGLOW_ENABLE = no   # LED underglow (Enable WS2812 RGB underlight.)
LED_ANIMATIONS = yes        # LED animations
IOS_DEVICE_ENABLE = no      # connect to IOS device (iPad,iPhone)

MOUSEKEY_ENABLE = yes       # Mouse keys(+4700)
```

see `config.h`
```
#ifdef MOUSEKEY_ENABLE
  #define MOUSEKEY_DELAY 0
  #define MOUSEKEY_INTERVAL 0
  #define MOUSEKEY_MAX_SPEED 2
  #define MOUSEKEY_TIME_TO_MAX 50
  #define MOUSEKEY_WHEEL_MAX_SPEED 1
  #define MOUSEKEY_WHEEL_TIME_TO_MAX 100
#endif

#ifdef TAPPING_TERM
#undef TAPPING_TERM
#endif // TAPPING_TERM
#define TAPPING_TERM 200
```

## Compile

go to qmk top directory.
```
$ cd qmk_firmware
$ git clone https://github.com/yymm/my-helix-profile-four-rows
```

build
```
$ make helix:my-helix-profile-four-rows
```

flash to keyboard
```
$ make helix:four_rows:avrdude
```
