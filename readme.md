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


