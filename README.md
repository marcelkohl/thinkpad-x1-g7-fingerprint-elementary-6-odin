# Fingerprint Settings
These are the steps to enable the Fingerprint authentication resources on:
- Thinkpad X1 - Gen.7
- Elementary OS 6 - Odin

This fingerprint authentication process enables the authentication on:
  - Login screen (identified by an icon on the right side of the password input)
  - Terminal (identified by text)
  - Root actions on desktop (NOT identified visually, but it works just by placing your finger on the reader)

## 1. Install necessary packages
`sudo apt-get install fprintd libfprint-2-2 libfprint-2-tod1 libpam-fprintd`

## 2. Enroll the first (right index) finger in fprintd
`fprintd-enroll`

**To enroll additional fingers, run the following**

`fprintd-enroll -f [finger-id]`

*Finger IDs: left-thumb, left-index-finger, left-middle-finger, left-ring-finger, left-little-finger, right-thumb, right-index-finger, right-middle-finger, right-ring-finger, right-little-finger*

## 3. Activate the fingerprint pam module
`sudo pam-auth-update`

Select the Fingerprint modules as you need. By default I enabled the following:
 - Fingerprint authentication
 - Unix authentication
 - Register user sessions in the systemd control group hierarchy
 - GNOME Keyring Daemon - Login keyring management
 - Inheritable Capabilities Management

## 4. Log out
Log out from your account or restart your device.

# Sources
- [archlinux fprint](https://wiki.archlinux.org/title/Fprint#Configuration)
- [Linux Mint 20 Upgrade on Lenovo Thinkpad X1 Carbon 7th Sound and Fingerprints](https://www.sysorchestra.com/linux-mint-20-upgrade-on-lenovo-thinkpad-x1-carbon-7th-sound-and-fingerprints/)
