# Coldcard Desktop Simulator

## Usage

    make && ./simulator.py


## Other Startup Flags

The default is to boot up, skip the tedious PIN entry step, and start as a functional
wallet (on testnet, always with the same seed). But there are other options:

- `-w` => like a factory-fresh unit; no PIN no secrets
- `-l` => PIN is set (12-12) but no secret yet
- `-2` => enable a secondary wallet, with pin 33-33 and no secret
- `-q` => boot and drop into REPL; does nothing else, no setup
- `-f -w` => boot like a unit that hasn't left factory yet
- `-p` => pretend we don't know the seed words (xprv import) and so menus are different
- `-m` => define a 2-of-4 multisig wallet, and start off in multisig wallet menu; cosigners are
            "Me", "Myself", "And I" and empty string. BIP45 path.
        - add `--p2wsh` or `--wrap` for other two address types
- `-s` => go to the MicroSD menu at startup
- `--mk2` => emulate mark2 hardware (older micro, etc), default is current-gen (mark3)
- `--mk1` => emulate mark1 hardware
- `-g` => don't skip login sequence
- `-a` => go to the address explorer at startup
- `--xw` => go to the wallet export submenu
- `--paper` => go to the Paper Wallet menu at startup
- `--xfp F0012345` => pretend like the XFP of secret is F0012345: useful for debug of PSBT files
- `--seed "art art ... food"` => set the seed phrase to 24 words provided
- `--metal` => use USB attached Coldcard for bootrom and SE features
- `--metal --sflash` => copy SPI flash contents at boot time from real device (no writeback)
- `--nick Name` => set the pre-login nickname for the Coldcard so it will be shown
- `--delay X` => set the "login countdown" value to X minutes, also force login

See `frozen-modules/sim-settings.py` for the details of settings-related options.

## Requirements

- uses good olde `xterm` for console input and output
- this directory has additional `requirements.txt` (a superset of other requirements of the project)
- run "brew install sdl2" before/after doing python requirements
- run "make setup" then "make"
- then "./simulator.py"

# MacOS building

- Follow instructions on <https://github.com/micropython/micropython>
- probably: `brew install libffi` if not already present
- to get `pkg-config libffi` to output useful things, need this:

    setenv PKG_CONFIG_PATH /usr/local/opt/libffi/lib/pkgconfig

- but that's in the Makefile now

# Other OS

- sorry we haven't gotten around to that yet, but certainly would be possible to build
  this on Linux or FreeBSD... but not Windows.


