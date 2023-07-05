[![Spytify Logo](https://user-images.githubusercontent.com/23088305/29906214-6daad21c-8de1-11e7-80f5-ef6791cc7825.png)](https://jwallet.github.io/spy-spotify/)

[![Build status](https://ci.appveyor.com/api/projects/status/s26ibv6ls9j56enr/branch/master?svg=true)](https://ci.appveyor.com/project/jwallet/spy-spotify/branch/master)
[![AppVeyor tests](https://img.shields.io/appveyor/tests/jwallet/spy-spotify/master?compact_message)](https://ci.appveyor.com/project/jwallet/spy-spotify/branch/master/tests)
[![Latest release](https://img.shields.io/github/tag/jwallet/spy-spotify.svg?label=version)](https://github.com/jwallet/spy-spotify/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/jwallet/spy-spotify/total.svg?color=yellow&label=downloads)](https://github.com/jwallet/spy-spotify/releases/latest)
[![Sub Reddit](https://img.shields.io/reddit/subreddit-subscribers/spytify.svg?label=r%2Fspytify)](https://www.reddit.com/r/spytify)
[![Donate](https://img.shields.io/badge/support-donate-ff69b4)](https://jwallet.github.io/spy-spotify/donate.html)
[![Issuehunt](https://jwallet.github.io/spy-spotify/assets/images/isohunt_badge.svg)](https://issuehunt.io/r/jwallet/spy-spotify)

Spytify is a Spotify recorder for Windows which records Spotify audio without recording or playing ads. It automatically splits songs into separate tracks and records to WAV or MP3 with media metadata, meaning you can easily start enjoying your music offline.

<p align="center"><img alt="Spotify Recorder logs" src="https://jwallet.github.io/spy-spotify/assets/images/ui_record.png" /></p>

### [How does it work?](#how-does-it-work)

Spytify records what Spotify outputs, which is a longer process than downloading a Spotify playlist with a tool.

However, Spytify ensures that all tracks will be the official released one, all sound volume normalized and with media tags and album cover. Playlist Downloaders get mostly all tracks from YouTube which means that they can't guarantee the choosen track will fit 100% the one in your playlist and they will all be the same quality.

Spytify encodes to the same quality that Spotify outputs ([Spotify Free 160kbps, Spotify Premium 320kbps](https://support.spotify.com/us/article/audio-quality/)), so the recorded copy will be indistinguishable from Spotify’s one.

**Spytify is meant to be used with a Spotify free account**, even better a fresh new one (Spotify may monitor your account activities).

### [How to install it?](#how-to-install-it)

Follow the steps shown in the F.A.Q section : [_How to install Spytify?_](https://jwallet.github.io/spy-spotify/faq.html#install-spytify)

### [How to use it?](#how-to-use-it)

A standard use is to install the Virtual Audio Cable and start a recording session on it using your favorite playlist and let it record overnight, so you avoid waiting for it to end, because Spytify does not download but records. You will then get all your songs automatically split into separate tracks without ads and with metadata.

A recorder requires a good sound card to be able to record good quality, that's why Spytify comes with a Virtual Audio Cable device, if you have issues with your sound card (volume slider and other apps sound affects the recordings, or overall recorded sound quality is worst than Spotify) you can install this virtual device using the **Speakers+** icon in Spytify settings.

Don't forget to hit the [F.A.Q.](https://jwallet.github.io/spy-spotify/faq.html) for tips on:

- [_How to install Virtual Audio Cable device for better recording quality?_](https://jwallet.github.io/spy-spotify/faq.html#install-better-audio-endpoint-device)
- [_How to isolate Spytify and Spotify on a virtual audio device to avoid background noises?_](https://jwallet.github.io/spy-spotify/faq.html#isolate-spotify-audio-endpoint)
- [_How to reroute sound/output of a virtual audio device to my main audio device to listen to it?_](https://jwallet.github.io/spy-spotify/faq.html#listen-to-virtual-device)
- [_How to connect to Spotify API for more accurate media tags?_](https://jwallet.github.io/spy-spotify/faq.html#media-tags-not-found)


### [Features](#features)

Splits the recorded sound into individual tracks using the artist and track names as the title, like so:
> Artist - Track.mp3
  
Saves all recordings under the same path:
> ../My Music/
  
Automatically adds metadata from Last.fm (or [Spotify API](https://jwallet.github.io/spy-spotify/faq.html#media-tags-not-found)) to .mp3 file:

- Last.FM : Spytify won't need to be connected to Spotify. It's safer than Spotify API, however the metadata won't be as accurate as the official API.
- Spotify API: You need to create your own [Spotify API keys](https://jwallet.github.io/spy-spotify/faq.html#media-tags-not-found) and set it in Spytify. Doing this gives better metadata results, however because you are connected to Spotify API, it's easier for them to know that you linked an app that fetches album cover. So you might get a warning from them using this API, but since Spytify does not download directly from Spotify (using the Connect API to receive OGG files which requires Premium), you have less chance to have your account suspended. Anyway, just to be sure, create a new one.

<p align="center"><img alt="Recorded songs with album cover and media tags in Windows Explorer" src="https://jwallet.github.io/spy-spotify/assets/images/saved_songs_list.png" /></p>

### [Requirements](#requirements)

Spytify runs on Windows only.

- Microsoft Framework ([.NET 4.6.1](https://www.microsoft.com/en-ca/download/details.aspx?id=49981) or higher).
- Spotify Desktop application.

A **free Spotify account** will work and its recommanded since Spotify may monitor your account, so go create a new one! However, Spotify restricts audio quality to 160 kbps. Having a Premium Spotify subscription will enable recording of up to 320 kbps audio.


## Support Spytify

😃 If you like Spytify, you can help me out for a [couple of beers](https://jwallet.github.io/spy-spotify/donate.html) 🍺 or give it a star ⭐ 

## [Download](https://github.com/jwallet/spy-spotify/releases)
