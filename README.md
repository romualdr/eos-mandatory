# mandatory

ElementaryOS opinionated post-installation tool.

This tool aims to simplify my reinstallation of [ElementaryOS 0.3 Freya](http://beta.elementary.io/). I was tired of always doing the same steps every time i perform a reinstallation of my system.

This tool get through some commons steps:
 * [Add some VPN](#configure-vpn) (PPTP only)(optional)
 * [Install commons softwares with dedicated PPA or Debian packages](#applications-list)
 * Perform update, dist-upgrade, then reboot.
 * Install all the applications you chose earlier

It automatically check your connection and use a VPN connection if needed (and [configured](#configure-vpn)).

If a step triggers a reboot, just relaunch the tool after reboot. The tool will continue to the next step automatically.

It's easy to add an application to the tool ! Just follow [these instructions](#add-application-to-mandatory).

## Usage

To download & use it, just run this command:
```wget https://raw.github.com/romualdr/eos-mandatory/mandatory && sudo ./mandatory```

To launch the script:
```sudo ./mandatory```

```
Usage: ./mandatory [option]

Options:
    auto [yes|no]: Automatic mode (don't ask)
        auto: Will always answer by the default answer
        auto y(es): Will always answer YES
        auto n(o): Will always answer NO
    reset: Reset Mandatory (use with caution).
    help: Print this help
```

## Applications list

Mandatory comes with a list of programs/tools/icons-packs pre-configured.

The tool will ask you if you want to install each one.
It add the perfect package, PPA/repo for package or deb package if previous solutions wasn't available.

This list and the setup IS opinionated, but feel free to add your own flavour to the tool

 * Firefox Developer Edition (PPA)
 * VirtualBox 4.3 (official repo)
 * Atom (PPA)
 * Brackets (PPA)
 * Sublime Text 3 (PPA)
 * build-essential (distribution)
 * git (distribution)
 * Zeal (PPA)
 * Vala compiler (distribution)
 * WPS Office (.deb package)
 * Spotify (official repo)
 * Popcorn Time (PPA)
 * Skype (distribution)
 * VLC (distribution)
 * Elementary tweaks (PPA)
 * Java 8 (PPA)
 * Flash Plugin (PPA)
 * Restricted codecs (distribution)
 * gParted (distribution)
 * Faba + Moka (PPA)
 * Numix theme (PPA)

## Configure VPN

Edit the first lines of the script with your favorite editor.

Add VPN URL(s) and VPN credentials like this:
```
# VPNs URLs
VPNS=(
    "sg1.vyprvpn.com"
    "my1.vyprvpn.com"
)
# PPTP CREDENTIALS
VPN_USER="toto" 
VPN_PASSWORD="password"
```

Save the file and relaunch the tool !

## Add application to mandatory

At the beginning of the tool, in app_list function, you can add your own package/application to the tool.

### Distribution package
```add_application "NAME" "PACKAGE_NAME"```

### Package in a specific PPA
```add_application "NAME" "PACKAGE_NAME" "PPA_URL"```

### Package in custom repository
```add_application "NAME" "PACKAGE_NAME" "DEB_URL" "SOURCE_LIST_NAME" "GPG_KEY"```

### Custom debian package
```add_custom_deb "NAME" "DEB_NAME" "DEB_URL"```

As custom debian package can cause update issues, please use it if anything else is available.

### Add dependencies to package
``` DEPS=([DEPENDENCIES]); ```

To add dependencies, simply add this before the package line.

``` DEPS=("libgtk-3-dev");add_application "Vala compiler" "valac" ```

## TODO

 * Make VPN configuration interactive
 * Fix bugs ?
