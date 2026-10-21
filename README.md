# Turn Up Music — Android app

Internet radio for Android by PenGame Publishing. *Feel the beat.*

## What it does

| Feature | How it works |
|---|---|
| Single or multi-station lists | Built-in list (`app/src/main/assets/stations.json`), an optional online list, and channels the listener adds. Set `config_single_station_mode` to `true` for a one-station branded app. |
| Online or offline lists (JSON) | The built-in list always works offline. An online list is downloaded, then cached on the phone so it still loads with no signal. |
| Add channels permanently | **+** button. Saved on the phone until the listener removes them. Lists can also be imported from a `.json` file or shared. |
| Free station directory + genres | **Discover** tab searches Radio Browser, a free community directory of 50,000+ stations. Genre chips: Hip Hop, R&B, Jazz, Gospel, Soul, Reggae, Afrobeats, Pop, Rock, Electronic, House, Classical, Latin, Country, Blues, Talk, News, Atlanta. |
| Background playback | Media3 playback service with lock-screen and notification controls. |
| Auto artist & track info | Read from the stream's "now playing" data (Icecast/Shoutcast). |
| Auto album cover art | Looked up per song (iTunes Search, free) and shown in the app, the notification and the lock screen. |
| Blur & glass UI | Cover art fills the background, blurred (Android 12+), with translucent panels on top. Blur strength is adjustable. |
| Real-time visualizer | Five effects: Bars, Mirror, Wave, Pulse ring around the cover, Off. |
| Customization | **Palette** button: six accent color themes, visualizer effect, backdrop on/off and blur. |
| Share | Shares the song, artist, station and stream link to any app. |
| Auto pause on calls | Pauses for phone calls and resumes after; also pauses when headphones are unplugged. |
| Sleep timer | Moon button cycles 15 / 30 / 60 / 90 minutes. |
| Stage (full-screen visuals) | Tap the cover art or the frame button. Scenes: Glowing orbs, Floating notes, Silhouette dancers (people shapes with hair, hands and shoes) with a bouncing crowd under stage lights. Tap to burst notes, tap orbs to pop them, Snapshot saves and shares the moment. |
| Artist profile | **Artist profile** button under the song. Photo and bio (Wikipedia), the song playing, music-video previews, images, top songs with 30-second previews, and the full discography (Apple's free iTunes catalog), plus YouTube, Apple Music and Spotify links. Unknown artists get a generic template profile. **Edit profile** lets you add your own video, image and release links and a bio. |
| VR Lounge & AR | Headset button. Opens the web version's 3D lounge (three.js + WebXR) in the browser: Enter VR on a Meta Quest, or place a mini stage in your room with AR on an ARCore Android phone. Set `config_web_app_url` in `config.xml` to where you host `web/index.html`. |

## Build the APK

**Option A — no software to install (GitHub).** Upload this folder to a new GitHub repository. Open the **Actions** tab, choose **Build APK**, click **Run workflow**. When it finishes (about 5 minutes), download `TurnUpMusic-debug-apk` from the run page and install it on your phone (allow "Install unknown apps" when asked).

**Option B — Android Studio.** File → Open → choose the `TurnUpMusic` folder. Let it sync (it downloads Gradle and the libraries automatically), then press **Run** with a phone plugged in, or Build → Build APK(s).

For Google Play you need a signed release build: Build → Generate Signed App Bundle in Android Studio. Upload `playstore-icon-512.png` as the store icon.

## Reskin and customize (no coding)

| To change | Edit |
|---|---|
| App name and every on-screen word | `app/src/main/res/values/strings.xml` |
| Colors | `app/src/main/res/values/colors.xml` |
| Accent themes listeners can pick | `AccentTheme.java` (name + two colors per theme) |
| Online list link, single-station mode, cover-art lookup, starting visualizer | `app/src/main/res/values/config.xml` |
| Built-in stations | `app/src/main/assets/stations.json` |
| Genre chips on Discover | `GENRES` at the top of `MainActivity.java` |
| Logo / app icon | `res/drawable-nodpi/logo_wordmark.png`, `res/mipmap-*/ic_launcher*.png` |
| Package name (needed for your own Play listing) | `applicationId` in `app/build.gradle` |

## Web version and the VR Lounge

`web/index.html` is the complete app as one web page: radio, Stage scenes, artist profiles and the 3D VR Lounge. Upload it to your website (any https address). Then:

- Open it on a Meta Quest browser and tap **VR Lounge**, then **Enter VR**.
- Open it in Chrome on an ARCore Android phone, tap **VR Lounge**, then **Place in my room (AR)**.
- Add `#lounge` to the address to open straight into the lounge, or `#club`, `#beach`, `#nyc`, `#rooftop`, `#madrid`, `#concert`, `#rodeo`, `#coffee`, `#tv`, `#jazz`, `#aquarium`, `#bollywood`, `#divebar`, `#aspen`, `#yacht`, `#harambee` to open a specific world. `#watch=VIDEOID` opens a YouTube video in the big view.
- Sixteen worlds: Rooftop Lounge, Nightclub, Beach Party, NYC Market Street Café, Madrid Courtyard Fiesta, Hip-Hop Concert, Texas Rodeo Night, Quiet Coffee Shop, the Turn Up Music Live TV dance show, a late-night **Jazz Café** (live trio with grand piano, upright bass and drums), **Aquarium Night** (a dark viewing hall and a giant ocean window onto a coral reef: a whale shark, manta rays, sea turtles, reef sharks, groupers, schools of sardines and jacks, blue tangs, yellow tangs, angelfish and clownfish in anemones, all swimming with a real S-shaped body wave, plus jellyfish columns) and a **Bollywood Party** (a palace courtyard with a "BOLLYWOOD PARTY" marquee in chasing lights, a dance troupe moving in perfect sync on the stage, belly dancers with coin belts on glowing podiums, street performers — a juggler, a fire spinner and a fire breather, each with a crowd — hand-painted film posters, sweeping searchlights, rose petals, a dance floor and fireworks). Plus four new ones: a **Rock & Roll Dive Bar** (gig posters, neon, a glowing jukebox, a pool table, a long bar with taps and stools, and a band on a tiny stage — guitarist, bassist, drummer and singer — with a crowd up front), the **Aspen Ski Resort** (après-ski on a lodge deck at dusk: snowy peaks, pine forest, fire pits with log benches, patio heaters, ski racks, a snowman, falling snow, a chairlift and a torchlight parade down the slope), a **Yacht Party** (sunset on the teak aft deck of a superyacht: rolling sea, a jacuzzi, sun loungers, a bar, a lounge sofa, dancers on deck and up on the flybridge, gulls overhead and islands on the horizon) and the **Harambee Jamboree** (an East African celebration on the savanna at golden hour: acacia trees, giraffes strolling past, a bonfire with drummers on tall ngoma drums, the jumping dance, dancers in bright prints, market stalls with baskets, fruit, beadwork and carvings, a grill and long feast tables). Switch with the world buttons under the lounge, or the globe button inside VR. Deep links: `#madrid`, `#concert`, `#rodeo`, `#coffee`, `#tv`, `#jazz`, `#aquarium`, `#bollywood`.
- **VR menu:** in the headset, a big menu panel opens in front of you. Point with either controller and pull the trigger. Press **B or Y** (or point at the ☰ button on your left wrist) to open or close it anytime.
  - **Music:** now playing with play/pause, previous/next and volume; ☆ Save the station; browse Favorites, My stations, Genres (live station search) and My music (your uploaded songs).
  - **Video:** your uploaded videos play on the big screen with play/pause, −10s/+10s, a progress bar you can point at to jump, volume and stop. YouTube can't be drawn inside a VR headset (browsers don't allow it), so in VR a YouTube video plays its sound, and **Leave VR and watch it** takes you straight to the picture.
  - **Worlds:** jump to any of the twelve worlds. **Party:** join/leave, dance, cheer, react, mic, Be the DJ, camera, mood and Exit VR.
- Pick things up: in VR, reach for a bottle, glass, cup, record, book or beach ball and squeeze the grip (or pull the trigger). Point at something across the table and pull the trigger to bring it to your hand. Let go to drop or throw it. Shake the champagne to pop the cork. On a phone or computer, tap an item to pick it up and tap again to toss it.

VR and AR need the page served from a website. A file opened from your downloads still plays radio and shows the 3D lounge on screen, but browsers only allow headset and AR mode on https pages.

## The party, profiles and live events

- **Join the party:** in the VR Lounge tap **Join the party** (or the 👥 button inside VR). You'll see everyone else in the same world as their own avatar with a name tag. Use **Join with code** for a private party with friends.
- **My avatar:** pick from 50 characters, then add a hat, eyewear, a chain or pearls, headphones, a glow color and height. Add your name, a short bio, favorite genre and Instagram. Tap another guest's name tag to see their profile.
- **In the party:** wave, dance, cheer, send 🔥 ❤️ 😂 🎉, chat, and turn on your mic to talk (people closer to you sound louder). **Be the DJ** makes everyone who follows you hear your station.
- **Walk around:** tap the floor (or W A S D on a computer). In VR, point at the floor and pull the trigger, or use the left stick to walk and the right stick to turn.
- **Live events:** the calendar button (top of the app) or **Live events** in the lounge. Four weekly featured shows are built in. Anyone can **Host an event**: pick a world, time and station. When it starts, a red LIVE banner appears in the lounge; **Join now** takes everyone to that world, and the host is the DJ.
- **How it connects:** guests connect directly to each other. Public Nostr relays introduce guests and store the events calendar, so there's no server to run or pay for. Very large crowds (30+ in one world) may get slow, and a few strict networks block direct connections.
- **Featured hosts:** your host key is shown in **Host an event**. Add trusted keys to `hostKeys` near the top of the party code (search for `const NET`) to give their events the Featured badge.

## VIP membership, DJ booth, social and music services

- **★ VIP** (gold button): members can DJ, host events, get into the VIP section of every world, play videos for everyone, and get a gold VIP tag. Moderators (VIP + Moderator) can mute or remove guests and hide posts.
- **Owner tools:** in the VIP window, open **Owner sign-in** and paste your owner code (kept private, not in this project). Then set the price and your payment link (Stripe Payment Link, PayPal, Cash App…), and give memberships by pasting a guest's member ID. Memberships are signed with your owner key, so they can't be faked.
- **Payments:** guests tap **Join VIP**, pay through your link (their member ID is attached for Stripe), and you turn their membership on in Owner tools. Automatic activation needs a small server that listens for Stripe payments.
- **DJ booth:** two decks (your uploaded songs or radio stations), crossfader, volume, speed, filter, echo, air horn, siren and talk-over mic. **Go live** streams the mix to everyone in the party and puts you behind the booth in the world.
- **My music & videos:** upload songs and videos; they stay on the device. Play them, put videos on the big screen (also in VR), or load songs into the DJ booth.
- **Spotify, Apple Music, TIDAL, YouTube:** paste a link to play it in an embedded player and share it with the party. YouTube links shared by VIPs start a watch-together for everyone following. Guests can add their music profiles to their profile card.
- **The Wall:** posts with photos, songs and links, likes, comments, follows and sharing to other apps.

## Outfits and screens

- **Outfit maker** (in **My avatar**): restyle your character's clothes while keeping the skin, face and folds. Free guests get 4 styles (Original, Solid, Stripes, Ombré) in 8 colors, plus **Surprise me**. VIPs unlock 16 more prints (plaid, camo, leopard, zebra, tie-dye, kente, galaxy, flames, floral, sequins, denim, checkerboard, polka dots, metallic, graffiti), any color, a matte/satin/shiny finish, and:
  - **Style Maker:** type a description like "shiny gold and black kente print" and the outfit is designed from your words. It runs in the app with no account or fees. A true AI image generator would need a paid service and an API key.
  - **Photo fabric:** upload any photo and wear it as your fabric.
  Everyone in the party sees your outfit.
- **📺 Screens** (lounge toolbar): show a YouTube link, a video link, a photo, a web page or an uploaded video/photo/PDF on the main screen, or add floating screens (free: 1, VIP: 4). Use ◀ ▶ under a screen to change slides. In VR, squeeze the grip to move a screen. When a VIP presents, everyone in the party sees the screens.
  - PowerPoint, Keynote and Google Slides: export the presentation as a PDF first.
  - YouTube plays on the 3D screens on computers, with **⛶ Big view** (full screen) and **YouTube ↗** buttons on the screen. On phones and small tablets YouTube opens in the big view, with **📺 Show on the room screen** to put it back in the room. If a video's owner only allows it on youtube.com (many official music videos), you get a clear message and an **Open on YouTube** button instead of a black screen. If the sound is blocked, tap **🔊 Tap for sound**. YouTube only plays when the app is opened from its website, not from a saved file.
  - In a headset, YouTube plays its sound and web pages open in the browser; uploads, video links and slides show on the 3D screens.

## Camera: photos and videos

- **📷 Camera** (top of the app, and **Camera** on the Stage and in the Lounge): take a photo or record a video with the music and the party's sound. Options: a 3-second timer, recording your voice, and a vertical format for Stories, Reels and TikTok. On a computer, press **P** for a quick photo.
- In the main app it makes a shareable "now playing" card (cover art, song, station and a live visualizer). On the Stage and in the Lounge it captures what you see. Every shot carries the Turn Up Music logo and the song.
- **In VR:** tap the 📷 button in the button row to hold a camera in your left hand, with a live viewfinder. Press **A or X** for a photo, **B or Y** to start or stop a video.
- **My shots:** everything stays on the device until you **Save**, **Share** (phones) or **Post to The Wall**. Videos are up to 5 minutes each. In AR, use the phone's own screen recorder.

## Station list format

```json
{
  "stations": [
    { "name": "WXYZ Atlanta", "url": "https://stream.example.com/live.mp3",
      "tag": "Hip-Hop · Atlanta", "logo": "https://example.com/logo.png",
      "alts": ["https://backup.example.com/live.mp3"] }
  ]
}
```

`url` must be a direct stream (MP3, AAC, OGG or HLS `.m3u8`), not a `.pls` or a web page. `alts` is optional: backup links the app switches to on its own if the main link fails. Stations do move their servers (SomaFM's changed in 2026), so give each station a backup when you can. Upload this file anywhere public and put its link in `config.xml`, or load it from the app's menu.

## Notes

- Requires Android 5.0 or newer. The original spec listed Android 2.2–5.0; Android 2.x–4.x can't run today's streaming and security libraries, and Google Play no longer accepts apps for them.
- The visualizer asks for audio permission once, because Android requires it for any app that animates to sound. The app never records.
- Stations belong to their broadcasters. If you publish the app commercially with specific stations built in, confirm each station allows third-party apps to carry its stream.

## Hosting the party: making sure everyone hears your music

- If you're a VIP (or the owner) and nobody else is DJing, pressing play in a party makes you the DJ automatically. You'll see "You're the DJ".
- Radio stations play on each guest's own device. Songs you uploaded to My music are streamed live from your device to the party, so keep the app open while they play.
- Spotify, Apple Music and TIDAL links open the same song for each guest. Those services play full songs only for guests who are signed in to them; everyone else hears a 30-second preview.
- If a guest's phone blocks sound, they'll see a big "Tap to hear the music" button.
- Sign in as owner (or VIP) on every device you host from: DJ messages from regular guests are ignored.

## Credits

Multiplayer uses Trystero (MIT) and nostr-tools (public domain). The 3D people in the VR Lounge are 29 Microsoft Rocketbox avatars (MIT license, © Microsoft Corporation, github.com/microsoft/Microsoft-Rocketbox) with their motion-captured dance, talk, idle, sit, cheer and walk animations: everyday adults, business people, beachwear and a delivery worker. Each world downloads only its own cast (about 8–14 MB) the first time you visit it. Copy the `people` folder next to the web page when you host it. If it can't be reached, the lounge falls back to the open-source three.js example characters ("Michelle", Xbot and a Ready Player Me avatar).

Furniture, plants and some props (armchairs, sofas, pouf, potted plant, flowers, teacup, boombox, lantern, wall lamps, refrigerator, sunglasses, water bottle) and the aquarium's fish are real 3D models from the Khronos glTF Sample Assets, under CC0 or CC BY 4.0. The full list with authors is in `web/assets/CREDITS.md`. Copy the `assets` folder next to the web page when you host it.

## On phones and tablets
The Stage and VR Lounge controls start tucked into a slim bar at the bottom so you can see the room.
Tap **▲ Controls** (or swipe the bar up) to open them, and **▼ Hide controls** (or swipe down, or tap the room) to tuck them away.
The bar also has quick buttons for the world, the party, the camera and VR. Your choice is remembered.

## Stations
71 built-in stations with backup links, including internet-only stations (SomaFM's 30-plus channels, Nightwave Plaza, Radio Meuh, Worldwide FM, dublab, Rinse FM, Dance Wave!, Radio Swiss Jazz/Pop/Classic), plus FIP (Hip-Hop, Groove, Jazz, World, Reggae, Rock, Pop, New Music, Electro), WWOZ, WBGO, Jazz24, KCRW, KEXP, WFUV, WFMU, NTS, Radio Nova, TSF Jazz, NPR News, WNYC, WQXR, BBC World Service and Radio Paradise.
**Discover** searches 50,000+ stations, with genre buttons for hip-hop, R&B, pop, metal, yacht rock, neo soul, gospel, afrobeats, amapiano, dancehall, reggaeton, trap, K-pop, lo-fi, smooth jazz, salsa, bachata and more.

## Podcasts
The **Podcasts** tab browses the Apple Podcasts directory: top charts, 16 categories (Hip-Hop & R&B, Comedy, True Crime, News, Black culture, Business & money, Sports, Health, Faith, Relationships, Pop culture, Tech, History, Kids & family, En español and more) and search by show, host or topic.
Open a show to see its episodes, **+ Follow** it to keep it under My podcasts, and tap an episode to play. While an episode plays you get a seek bar, ↺ 15s / 30s ↻ skip buttons and a speed button (0.75× to 2×). Your place in every episode is remembered, and the next episode plays when one ends. In VR, the menu's Music tab has a 🎙 Podcasts list too.

## People in the lounge
50 characters, most of them women. Every world's crowd is mostly Black, Latino and Asian guests, with others mixed in.

## Talking, touching and moderating
- **Voice chat:** tap 🎤 (the Party menu inside VR) to talk. If you're not in the party yet, the mic joins it for you. Each voice comes from where that guest stands, so people near you are loud and people across the room are quiet. A 🔊 floats over whoever is talking. Your mic stays on when you change worlds.
- **Touching people in VR:** reach out and touch someone. They turn to face you and react, and a quick shove makes them stagger back. Hold the grip button on a person to walk them somewhere else; let go and they stay there. On a phone or computer, tap a person to say hi.
- **Other guests:** touch a guest in VR (or open Party → 👥 People) to see their card. From there you can mute or hide them.
- **Moderators:** the same card has **Mute for everyone** and **Remove from party**. In VR you tap Remove twice to confirm. On a phone or computer, tap the guest. A removed guest is blocked from that party for an hour, even if they rejoin under a new name on the same device. Any moderator in the room removes them again if they come back.
- **Hair and hats:** hats now fit each character's real hair, so they sit on the head instead of floating or poking through. NPCs with big afros go without a cowboy hat. Hair edges are softer and no longer show pale streaks in bright light.

## Flyers and invitations
- **Where:** open **Live events**. Your own events have a **🎨 Flyer & invites** button (moderators also get it on the featured weekly shows). While filling in **Host an event** you can tap **🎨 Make a flyer** to preview one, and the flyer maker opens by itself after you publish.
- **Four looks:** Neon Nights (synthwave), Gold Gala (black-and-gold art deco), Retro Sunset (70s), Bold Poster (one loud color, huge type). Change the color, add your own photo, and edit the headline and details.
- **Flyer or invitation:** an invitation adds the guest's name and a personal note.
- **Sizes:** Post (4:5 for Instagram and Facebook), Story (9:16) and Square.
- **Every design shows** the date, time in the viewer's time zone, world, music, host, and a QR code that opens the event (`…/Turnupmusic/#event=…`). If the event is live, it says so and **Join now** is one tap away.
- **Sending it:** **Share…** opens the phone's share sheet (Instagram, TikTok, Messages, email, anything) with the picture attached. Other options are **Download** (PNG), **Email** (on a computer it downloads the picture and opens a new email for you to attach it to), **Copy link**, and quick buttons for X, Facebook, WhatsApp and text message.
- **Saved designs:** **Save this design** keeps up to 12 designs on this device, including the photo, to reopen later.
