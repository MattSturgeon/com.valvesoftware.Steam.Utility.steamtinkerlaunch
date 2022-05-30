# com.valvesoftware.Steam.Utility.steamtinkerlaunch

Testing repo ahead of the tool being accepted on Flathub (maybe longer).

Will likely end up tracking certain Steam Tinker Launch commits instead of "stable" releases.

# Reporting issues

Currently all Steam Tinker Launch flatpak discussion is happening here: https://github.com/frostworx/steamtinkerlaunch/issues/27

# Want to test it?

1. Install the [Steam Flatpak](https://beta.flathub.org/apps/details/com.valvesoftware.Steam) if you haven't. Unfortunately, this will only work with the Steam Flatpak.

2. Open the terminal.

3. Run `git clone https://github.com/HanPrower/com.valvesoftware.Steam.Utility.steamtinkerlaunch` in the terminal and navigate in to the directory.

4. This bit is a bit scary... currently (30th May, 2022) we're waiting on a feature to make it upstream which is necessary to test this properly, so I've bundled that runtime in `flatpak/com.valvesoftware.Steam.flatpak`. Anything could technically be in this runtime, this is scary! You should never trust random files from the internet!! However, if you want to continue navigate in to the folder and run `flatpak --user com.valvesoftware.Steam.flatpak`

5. If you run `flatpak list` you should see Steam from a test branch, and `steam-origin` Origin.

6. Navigate back out of the `flatpak` folder, and run `chmod +x fp-build.sh`. This is a file that just automates some of the fiddly flatpak-builder bits. Feel free to check the file first.

7. Run `./fp-build.sh com.valvesoftware.Steam.Utility.steamtinkerlaunch.yml`. You can safely ignore the Appstream check error. If the utility fails to install, you likely don't have Flathub added for your user specifically. Run `flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo` if that is the case.

8. Run `flatpak list --user | grep steamtinkerlaunch` to double check that it is installed.

9. Open the Steam Flatpak. You can run it from the application menu or by running `flatpak run --branch=test --arch=x86_64 --command=/app/bin/steam-wrapper --file-forwarding com.valvesoftware.Steam` in the terminal.

10. Right click the game you want to test, then click "Properties", select "Compatibilty", and check "Force the use of a specific compatibility tool" and select "Steam Tinker Launch" from the dropdown.

11. Launch the game and you should see the steamtinkerlaunch menu. Press "MAIN MENU" to look at the menu.

# Sick of testing it?

If you want to revert everything, do the following:

1. Run `flatpak remove com.valvesoftware.Steam` and select the version from the `test` location.

2. Click "Properties" on any game you enabled Steam Tinker Launch for, select "Compatibilty", and uncheck "Force the use of a specific compatibility tool".

3. Run `flatpak remote-delete --user flathub`. This will remove the Flathub remote from the user.

# Credits

[@frostworx](https://github.com/frostworx) - glorious Steam Tinker Launch creator

[@TheEvilSkeleton](https://github.com/TheEvilSkeleton) - initial creation of the flatpak files for the project
