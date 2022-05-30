# com.valvesoftware.Steam.Utility.steamtinkerlaunch

Testing repo ahead of the tool being accepted on Flathub (maybe longer).

Will likely end up tracking certain Steam Tinker Launch commits instead of "stable" releases.

# Reporting issues

Currently all Steam Tinker Launch flatpak discussion is happening here: https://github.com/frostworx/steamtinkerlaunch/issues/27

# Want to test it?

    1. Install the [Steam Flatpak](https://beta.flathub.org/apps/details/com.valvesoftware.Steam) if you haven't. Unfortunately, this will only work with the Steam Flatpak.

    2. Open the terminal.

    3. Run `git clone https://github.com/HanPrower/com.valvesoftware.Steam.Utility.steamtinkerlaunch` in the terminal.

    4. Run `chmod +x fp-build.sh`. This is a file that just automates some of the fiddle flatpak-builder bits. Feel free to check the file first.

    5. Run `./fp-build.sh com.valvesoftware.Steam.Utility.steamtinkerlaunch.yml`. You can safely ignore the Appstream check error. If the utility fails to install, you likely don't have Flathub added for your user specifically. Run `flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo` if that is the case.

    6. Run `flatpak list --user | grep steamtinkerlaunch` to double check that it is installed.

    7. Open the Steam Flatpak. You can run it from the application menu or by running `flatpak run com.valvesoftware.Steam` in the terminal.

    8. Right click the game you want to test, then click "Properties". Afterwards select "Compatibilty" and check "Force the use of a specific compatibility tool" and select "Steam Tinker Launch".

    9. Launch the game and you should see the steamtinkerlaunch menu. Press "MAIN MENU" to look at the menu.

# Sick of testing it?

If you want to revert everything, do the following:

    1. Run `flatpak remove com.valvesoftware.Steam.Utility.steamtinkerlaunch`.

    2. Click "Properties" on any game you enabled Steam Tinker Launch for, select "Compatibilty", and uncheck "Force the use of a specific compatibility tool".

    3. Run `flatpak remote-delete --user flathub`. This will remove the Flathub remote from the user.
