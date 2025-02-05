# BG Alliance Church Lobby Kiosk

This `Web/index.html` file provides an `iframe` to a specified slideshow that is easier to control and edit than the old-school flash drive approach to the tv kiosk.

Here are some important notes about the architecture involved here.

## Auto-Launching Browser

The browser auto-launches on start-up of the device. Once it is ready, the browser opens to the `Web/index.html` file. This is controlled through the
autostart file found at `~/.config/autostart/auto-start.desktop` which holds the startup command to be executed (`chromium-browser --start-fullscreen ~/Web/index.html`).

This *should* handle any power outtages so that the browser automatically opens again without need for human interaction.

## `iframe` Sizing

The `iframe` is stretched to be the full width of the display for optimal viewing.

## Google Slides Toolbar

The toolbar typically shown across the bottom of the embedded slideshow is being removed via the `iframe` `src` attribute's GET parameter `rm=minimal`. 

## Incognito

The browser launches in Incognito mode so that, if the browser closes improperly, the Chrome/Chromium feature to reopen improperly-closed windows/tabs does not display.

## Hidden Cursor
We are auto-hiding the cursor with an `unclutter` command. See the startup script for details. **Note**: setting it to 0 seconds is super buggy and hides the mouse too quickly. Use some value > 0.

## Page Refresh
Time to refresh the page is currently 1 day. This uses the `meta` refresh tag in the `head` of the page.

## Pi Fan
As of 11-11-2022, a fan has been added to the pi to keep it from overheating and crashing. The fan is the high-pitched noise coming from the back of the tv. You're welcome...


```
[Desktop Entry]
Type=Application
Name=AutoBrowser
Exec=chromium-browser --start-fullscreen --incognito ~/Web/index.html
```
