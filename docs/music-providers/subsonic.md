# Subsonic Provider ![Preview image](../assets/icons/subsonic_icon.png){ width=70 align=right }

Music Assistant has support for music servers which work to the Open Subsonic API definition. The implementation has been tested against Gonic and Navidrome but should work with any implementation. Currently only Music is imported into the Music Assistant database but the infrastructure for handling podcasts is present when they are supported in Music Assistant. This component is contributed and maintained by [khers](https://github.com/khers)

## Configuration:
You will need to provide the following to Music Assistant:

- A base URL for the server (e.g. https://music.domain.tld)
- A port number (e.g. 80 for plain http, 443 for https, or an port where your server can be reached)
- A path used to get to the rest API (e.g. mypathroute/ if you are path routing, leave this blank unless you know you need it)
- A user name for the account you want Music Assistant to use to access your server
- The password for this account

There is also a toggle for podcasts which will have no effect now but will allow those who cannot or do not want to make podcasts available to Music Assistant.

## Known Issues / Notes
- Not all server implementations accept an empty string as a search query, however this is considered valid input per the API documentation. If search or track enumeration fails, ask the authors of your server implementation about handling empty query strings.
- This provider makes use of https://github.com/khers/py-opensonic for communicating with the server, if something is failing to work properly in Music Assistant, try to use that library to interact with your server (can you ping it?, fetch artist and albums?, can you search?).
- If you find a mismatch between what is displayed by your Subsonic compatible server and Music Assistant then refer to and contribute [here to help find a solution](https://github.com/music-assistant/hass-music-assistant/issues/2192)
- Not all Open Subsonic implementations handle tracks/albums with multiple contributing artists particularly well. If you see strange artists listed in Music Assistant, please verify that your implementation has an artist ID for all artists listed on a track or album. See the discussione [here](https://github.com/music-assistant/hass-music-assistant/issues/2965).
