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
- Twenty worlds: Rooftop Lounge, Nightclub, Beach Party, NYC Market Street Café, Madrid Courtyard Fiesta, Hip-Hop Concert, Texas Rodeo Night, Quiet Coffee Shop, the Turn Up Music Live TV dance show, a late-night **Jazz Café** (live trio with grand piano, upright bass and drums), **Aquarium Night** (a dark viewing hall and a giant ocean window onto a coral reef: a whale shark, manta rays, sea turtles, reef sharks, groupers, schools of sardines and jacks, blue tangs, yellow tangs, angelfish and clownfish in anemones, all swimming with a real S-shaped body wave, plus jellyfish columns) and a **Bollywood Party** (a palace courtyard with a "BOLLYWOOD PARTY" marquee in chasing lights, a dance troupe moving in perfect sync on the stage, belly dancers with coin belts on glowing podiums, street performers — a juggler, a fire spinner and a fire breather, each with a crowd — hand-painted film posters, sweeping searchlights, rose petals, a dance floor and fireworks). Plus four new ones: a **Rock & Roll Dive Bar** (gig posters, neon, a glowing jukebox, a pool table, a long bar with taps and stools, and a band on a tiny stage — guitarist, bassist, drummer and singer — with a crowd up front), the **Aspen Ski Resort** (après-ski on a lodge deck at dusk: snowy peaks, pine forest, fire pits with log benches, patio heaters, ski racks, a snowman, falling snow, a chairlift and a torchlight parade down the slope), a **Yacht Party** (sunset on the teak aft deck of a superyacht: rolling sea, a jacuzzi, sun loungers, a bar, a lounge sofa, dancers on deck and up on the flybridge, gulls overhead and islands on the horizon) and the **Harambee Jamboree** (an East African celebration on the savanna at golden hour: acacia trees, giraffes strolling past, a bonfire with drummers on tall ngoma drums, the jumping dance, dancers in bright prints, market stalls with baskets, fruit, beadwork and carvings, a grill and long feast tables). Switch with the world buttons under the lounge, or the globe button inside VR. Deep links: `#madrid`, `#concert`, `#rodeo`, `#coffee`, `#tv`, `#jazz`, `#aquarium`, `#bollywood`.
- **VR menu:** in the headset, a big menu panel opens in front of you. Point with either controller and pull the trigger. Press **B or Y** (or point at the ☰ button on your left wrist) to open or close it anytime.
  - **Music:** now playing with play/pause, previous/next and volume; ☆ Save the station; browse Favorites, My stations, Genres (live station search) and My music (your uploaded songs).
  - **Video:** your uploaded videos play on the big screen with play/pause, −10s/+10s, a progress bar you can point at to jump, volume and stop. YouTube can't be drawn inside a VR headset (browsers don't allow it), so in VR a YouTube video plays its sound, and **Leave VR and watch it** takes you straight to the picture.
  - **Worlds:** jump to any of the twelve worlds. **Party:** join/leave, dance, cheer, react, mic, Be the DJ, camera, mood and Exit VR.
- Pick things up: in VR, reach for a bottle, glass, cup, record, book or beach ball and squeeze the grip (or pull the trigger). Point at something across the table and pull the trigger to bring it to your hand. Let go to drop or throw it. Shake the champagne to pop the cork. On a phone or computer, tap an item to pick it up and tap again to toss it.

VR and AR need the page served from a website. A file opened from your downloads still plays radio and shows the 3D lounge on screen, but browsers only allow headset and AR mode on https pages.

## The party, profiles and live events

- **Join the party:** in the VR Lounge tap **Join the party** (or the 👥 button inside VR). You'll see everyone else in the same world as their own avatar with a name tag. Use **Join with code** for a private party with friends.
- **My avatar:** pick from 50 characters, then add a hat, eyewear, a chain or pearls, headphones, a glow color and height. Add your name, a short bio, favorite genre and Instagram. Tap another guest's name tag to see their profile.
- **Mixed reality (Quest passthrough and AR phones):** tap **🕶 Mixed reality** to see your real room with the lounge in it. Point at the floor and pull the trigger (or pinch) to place the stage, and it locks to that spot with an anchor. Press the ☰ on your left wrist, then **🕶 Room** to: resize (Tabletop / Room / Life-size), turn the stage, move it, **📺 Pin to wall** (aim at a real wall and the video screen hangs there; resize or unpin it), and dim your room (Clear / Dim / Club dark). The **Music, Video and Party** tabs work in MR too.
- **👑 My Empire is one tap away:** a **👑 My empire** button on the party bar, **👑 My Empire** in the VR menu's Party tab, a **👑 Empire** button in the top bar of every Mogul screen, a big My Empire tile on the job menu, the **E** key, and the link `#empire`.
- **🔎 Scavenger hunt:** tap **🔎 Scavenger hunt** (party bar, or **🔎 Start the hunt** in the VR menu's Party tab) and tap **Start hunting**. Five **Golden Records** are hidden in every world. Look around, tap them, or walk up to one; a ping gets faster and higher as you get warmer (and your controllers buzz in VR), and the window lists a clue for each record you haven't found. Each record pays $50 of Nightclub Mogul cash, a finished world pays $250, and all worlds make you a 👑 Master Hunter ($2,500). Progress saves on your device (and in your account). Records you find stay found.
- **Your own 3D avatar:** in **My avatar**, upload a `.glb` or `.vrm` (Ready Player Me files you saved before it closed on Jan 31 2026, Avaturn, VRoid, Mixamo, Blender), or paste a direct https link to a `.glb`. It is resized to fit, and the lounge's dance, walk, talk and sit moves are re-aimed onto its skeleton. Models with no skeleton sway gently. The file stays on your device (IndexedDB) and is sent only to guests in a party you join (adults only, max 8 MB / 150k triangles). A switch controls whether you see other guests' custom avatars.
- **3D Avatar Studio:** tap **🧬 3D Studio** to turn a photo into a rigged 3D character: the photo is wrapped onto a shaped 3D face (with depth), then pick build, height, skin, hair style and color, top and bottom, and shoes. Skin and hair colors can be read from the photo. The photo never leaves the device. Use it as your avatar or download the `.glb`.
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

## New worlds: Reggae Dance Hall, Downtown Tokyo Cyberpunk, International Space Station
- **Reggae Dance Hall** (`#reggae`, `#dancehall`): a Kingston yard dance at night. There's a wall of hand-built speaker boxes with cones that pump to the bass under an "IRIE VIBES SOUND" banner, plus an MC with a mic, zinc fences, a "ONE LOVE" mural and a lion mural. Around the yard are the Irie Rum Bar shack, jerk-chicken oil-drum grills with smoke, a dominoes table, palm trees, red-gold-green string lights, and a crowd dancing in the painted ring.
- **Downtown Tokyo Cyberpunk** (`#tokyo`, `#cyberpunk`): a rainy neon street with a scramble crossing on wet asphalt that reflects the neon. Vertical signs in Japanese hang over the street, and giant billboards are animated. There are holographic koi swimming overhead, hover cars streaking between towers, a ramen stall with red lanterns, vending machines, steam from manholes, and a DJ stage with the big screen. Dancers wear LED visors and neon street wear.
- **International Space Station** (`#space`, `#iss`): a party module in orbit. A big round window looks out on the curve of the Earth, with clouds, oceans, continents and a thin blue atmosphere. A glass viewport in the floor looks straight down. Gold solar wings, the truss and a docked capsule are outside. Inside are racks, laptops showing orbit data, handrails, cable runs, party LEDs, floating water globes and sweets, a floating guitar, and guests dancing in zero-g (one is upside down by the window).

## Running smoothly on Quest and phones
- Only the world you're in and the one before it stay in memory on a headset, phone or tablet (four on a computer). Worlds you've left are released and rebuilt if you go back, which takes a few seconds. Before this, memory grew with every world you visited until the Quest browser shut down.
- In VR the headset shows a black "Loading…" screen while a new world is being built, then fades back in, instead of a frozen, jumpy picture.
- In VR only the strongest few lamps in each world are switched on, because the headset draws everything twice. They all come back when you take the headset off.
- The VR world picker now fits every world on the panel (the newest ones used to fall off the bottom).

## Turn Up Social: pages, friends, walls and one account on every device
Open it with the speech-bubble button (it used to be "The Wall").
- **Feed:** posts from everyone, or just friends and people you follow. Post text, a photo, a link or the song that's playing. Like, reply and share. Tap anyone's name or picture to open their page.
- **My page** (in the style of Friendster and MySpace): a colored cover, your avatar, a mood or status line, your city, what you're into, your favorite genre, music links, and a "member since" date. It shows your posts, followers, following, friends and likes. **Top friends** shows up to 8 people you choose, and **Photos** collects your picture posts. Your **Wall** is where you post, and where other people can write to you. Tap **Edit my page** to change the mood, city, interests, cover color and top friends.
- **Friends:** when you follow someone and they follow you back, you're friends. The Friends tab lists Friends, Following and Followers.
- **Find people:** search everyone with a page by name, city, genre or interests.
- **Alerts 🔔:** new followers, likes, replies and wall posts, with a red counter.
- **In the lounge:** tap a guest and choose **View page**.
- **Shareable links:** `…/Turnupmusic/#user=<their key>` opens a page. Use **Share page** to get yours.
- **Same you on every device:** before, a tablet and a Quest were two different guests with two different looks. On **My page**, tap **Use on another device → Make a code for my other device**. On the other device, go to **My page → Use on another device**, type the 8-character code and tap **I have a code** (the code works for 10 minutes). Both devices are then the same account, with the same name, avatar, outfit, friends and VIP pass. A change on one device shows up on the other.
- **Characters match everywhere:** the Android app used to carry only 16 of the 50 characters, so on a tablet running the app other players often showed up as someone else. Now every device downloads the exact character each player chose, and the app's built-in ones are used only when there's no internet.

## User guide
`guide.html` (…/Turnupmusic/guide.html) is the full how-to guide: a 10-step quick start, then a step-by-step outline of everything in the app (getting started, radio and podcasts, your look, VR Lounge controls for phone, computer and Quest, the 25 worlds, parties, events and flyers, Turn Up Social, the DJ booth, memberships, safety, troubleshooting, and owner and moderator tools). Open it from the **?** button at the top of the app or **❓ Guide** in the lounge.

## Age protection, safety and advisory
- **Age check:** the first time the app opens it asks for a date of birth, without saying what the cut-off is. Only "18+ yes/no" is stored, never the birthday. Adults also agree to the Community Guidelines.
- **Under 18 gets music mode:** radio, podcasts, their own music and exploring the worlds alone. Parties, voice chat, text chat, Turn Up Social, live events, flyers and memberships are switched off and hidden. The answer is locked on the device (clearing the saved answer doesn't unlock it).
- **Adults only meet adults:** party guests only see and hear other guests who passed the check.
- **First-party advisory:** before your first party you see what to expect and how to mute, block, report and leave.
- **Report** (🚩) on posts, guest cards and pages, with reasons including "This person may be under 18". Reports go to moderators, who see them in the **🛡 Safety center** and can hide posts or remove people.
- **🛡 Safety center:** only hear voice from friends, blur photos from people you don't follow (on by default), show only friends' wall posts, and manage your blocked list.
- Note: a date-of-birth check relies on what people enter. For stronger checks (for example on paid plans), the owner can add an ID-verification service such as Stripe Identity, Persona or Yoti later. This isn't legal advice; check the rules where you operate (for example COPPA in the US).

## Membership plans (paid tiers)
| Plan | Default price | Unlocks |
|---|---|---|
| Free | Free | Radio, podcasts, all worlds, parties, voice, Turn Up Social, basic outfits |
| ⭐ Plus | $4.99/month | Every outfit style and your own fabric, VIP sections, premium page covers, PLUS badge |
| ★ VIP | $9.99/month | DJ booth, host events, flyers and invitations, watch together, VIP badge |
| 💎 Pro | $24.99/month | Featured badge on events, moderate your own event parties, top of Find people, PRO badge |

Each plan includes everything in the plans before it. The owner sets each plan's price and payment link under ★ VIP → Owner tools (Stripe payment links add the buyer's member ID automatically). After a payment, the owner gives the plan with **Give membership** (Plus, VIP, Pro or VIP + Moderator). Turning plans on automatically when a payment clears would need a small server connected to Stripe.

## Nightclub Mogul (built-in game, 18+)
Tap **🍾 Mogul** on the party bar, or go to **Party → 🍾 Nightclub Mogul** in VR. You can also link straight to it with `#mogul`.
- **Ten jobs**, each with its own step-by-step training: Bartender (VR mixology with real bottle pouring), Bouncer (IDs, dress code, the list, fights), DJ (beatmatching on two synth decks), Barback/Busser, Bottle Service, Promoter, Celebrity, Birthday, Club Owner and Bar Brawl.
- **Strikes and obstacles**: underage and drunk guests, fake IDs, spills, slip hazards, deadlines and fights.
- **The empire**: earn cash on shifts, then buy venues, upgrades and staff and run nights. Progress is saved on the device.
- **Bar Brawl** is our own animated bar fight, with full fight scenes:
  - real jabs, crosses, hooks, uppercuts and roundhouse kicks, and a 💥 Slam that lifts a guy over your head and puts him through the floor
  - fighters block, weave, stagger, double over and get knocked flat, with comic-book impact words, camera shake and punch sounds
  - on phones and tablets your fighter is on screen, the camera sits over your shoulder, and thumb buttons sit in the corners; in VR your own hands throw the punches
  - the bouncer's "two guys squaring up" scene is now a six-question de-escalation drill built on how real fights and real security training go: read the warning signs (going quiet, tucked chin, bladed stance), approach at an angle with open hands, move the filming crowd back, talk them down, watch for the fake-surrender cheap shot, then separate them with different exits. Your answers set how hot it gets: the two guys start with chest bumps and shoves and only trade real punches if you handle it badly
  - block, dodge and counter
  - throw mugs, bottles and bar stools, for real in VR
  - Liquid Courage power-ups
  - gangs that join in during later rounds
  - slapstick knockouts with circling stars
  In the headset your view never moves on its own, which keeps it comfortable.
- **Pro bartending**:
  - speed tips with 🔥 streak multipliers
  - flair flips (in VR, toss and catch a real bottle)
  - bottles that smash if you drop them
- **Pro DJing**:
  - color-coded scrolling waveforms
  - LOW/MID/HI kill switches and an LPF/HPF filter sweep
  - bass-swap scoring
  - 🔗 Sync
  - 🤚 Scratch
- **🏆 Daily leaderboard** per job: top earners today, reset every day (shared over TUNet).

## Zoom, watching screens, and moving around
- **Zoom**: mouse wheel, trackpad pinch, two-finger pinch, the ＋/－ buttons on the right, or the +/− keys (0 resets). Looking around slows down while zoomed in.
- **Watch up close** (📺, the 🔍 under a screen, or F): glides you in front of a screen so it fills your view, with the menus hidden. ✕ or Esc goes back. Tapping a web or YouTube screen goes up close so you can use the page.
- **In VR**: point at a screen and click a thumbstick to get a big personal copy floating in front of you.
- **Videos no longer cover people's heads.** Web and YouTube screens now sit behind the 3D scene, and the screen is a see-through window, so anyone standing in front of it shows in front.
- **How to move around**: a help sheet for each device (phone or tablet, computer, VR headset). It opens the first time on each device and any time with 🧭 or H. In VR there's a floating controls card (Menu → Party → 🧭 Controls).
- **🥊 Brawl mode** button: start a bar fight right where you stand, in any world.

## Graphics quality (✨ in the lounge controls)
- **💎 Ultra**:
  - higher render resolution (supersampling on 1× screens)
  - 4× multisampled anti-aliasing through the glow pipeline
  - a soft overhead shadow light that follows you, so every person and object casts a live shadow
  - 2048 px shadow maps
  - maximum texture sharpness (anisotropic filtering)
  - a cinematic color grade with vignette and fine grain

  It's on by default on strong computers, and steps down to Standard by itself if the frame rate drops.
- **⚖️ Standard**: the previous look.
- **🔋 Battery saver**: 1× resolution and no post effects.
- VR keeps its comfortable settings. On a PC headset, Ultra raises the VR render scale to 1.3×.

## Seated people fixed
People on bar stools, chairs, sofas and benches now settle onto the nearest real seat. They're centered on stools, and the floor no longer counts as a seat. Before, some sank into stools, sat on the floor next to a sofa, or perched beside a stool.

## New world: Luxury Penthouse Loft

- **Luxury Penthouse Loft** (`#penthouse`, `#loft`): a very large two-storey penthouse. The lower floor has a double-height living room with a chandelier, a fireplace under the big screen, a baby grand piano, an LED dance floor and a DJ booth. Under the upper floor are a foyer, a dining table for ten and a kitchen island with a wine wall. A marble staircase leads to the upper floor, which has a lounge, a library wall, a pool table, a bar and a master suite behind glass. Through the glass wall, a terrace has an infinity pool you can wade into, a fire pit and loungers. The city glitters far below.
- **Move the furniture.** Sofas, chairs, tables, stools, plants, the piano, the pool table, the bed and the small things on them can all be picked up. On a screen, tap a piece to pick it up and tap again to set it down. In VR, grab it with the grip or trigger. People sitting on a piece come along. The 🛋️↺ button puts everything back.
- Two floors: tap the floor on either level, or walk up the stairs.

## Account: save your progress

- The 👤 button (adults only) opens **Sign in / Create account**. An email address (you also confirm your date of birth, 18+) and a passcode of 8+ characters turn into two keys: one signs a saved copy and one locks it with AES-GCM. The locked copy sits on the same public relays as the live events. The passcode never leaves the device and cannot be reset.
- Profile, favorites, stations, settings and game progress save a few seconds after any change, and when the page is hidden or the device comes back online. Signing in on another device restores them and the identity key, so memberships and posts follow the person. Device-only items (graphics level, age gate, secrets) are never saved.

## Screen visuals, easy world picker, simpler song info
- While music plays, the big screen shows moving pictures that react to the beat: Orbs, Meter, Silhouettes, Tunnel, Lasers, Waves, Starfield and Kaleidoscope. **🎲 Surprise me** (the default) switches between them by itself. Pick one with the **🎛** button in the lounge controls, or **🎛** in the VR menu's Party tab. Choose **🎵 Song card** to go back to the plain song display.
- The screen only shows the **song title and artist** now. Videos and web screens still take over the screen when you start them.
- **🌍** in the lounge controls (and the **🌍 World** button on phones and tablets) opens a big list of worlds: tap one to go there. In VR, the Party tab has **🌍 Next world** for a one-tap hop.
- Your profile saves itself as you edit it. Sign in (Account) to keep it on every device.

## Karaoke, and the sign-in fix
- **🎤 Karaoke:** tap 🎤 in the lounge controls (or the 🎤 button on the phone bar, or Party → 🎤 Karaoke in VR). Pick a song, and the words light up on the big screen as the backing plays. Four public-domain songs are built in (Twinkle Twinkle, Row Row Row Your Boat, Happy Birthday, Jingle Bells chorus). **➕ Use my own song** lets you pick a music file from your device and paste lyrics (plain lines or timed [mm:ss.x] lines). Only use music you have the right to use.
- **With friends:** join the party and everyone shares one queue, sees the lyrics and hears the singer's voice. Cheer with 👏🔥❤️🎉🙌: cheers add to the singer's score. On your own, a virtual crowd cheers for you.
- **Score:** based on how much you actually sing during the lyrics (needs the mic) plus the cheers.
- **Sign-in fix:** the account button and sign-in form were not connected in the last version. They are now. If sign-in still can't connect, the message tells you how many save servers it reached.


## Pets, accessories and editing your page
- **Edit your page**: on your own page tap Edit to change your name, bio, favorite genre, link, mood, city, interests, cover and top friends.
- **Accessories**: backpack, angel or devil wings, hero cape, fox tail, halo, bunny or cat ears, little horns (My avatar window).
- **Pets**: puppy, kitten, bunny, fox, parrot, penguin and baby dragon follow you around the lounge. Name your pet and pick its color. Tap a pet to make it happy. Other guests see your pet too.

## Wellness rooms, activities and My Home
- **Four new worlds**: Meditation Room, Exercise Room, Dance Class Studio and Escape Room.
- **Wellness & play** in Nightclub Mogul: Meditation (breathing, stillness, singing bowl), Exercise (warm-up, jumping jacks, squats, plank, boxing pads, stretch), Dance Class (salsa basics) and Escape Room (randomized painting code, lamp pattern, cipher, riddle, lock). No strikes. Each raises a need and pays a little cash.
- **🏡 My Home** (party bar or world list): a Sims-style house and garden. Build with Mogul cash (36 items: furniture, fun, flowers, vegetables, trees, pond, beehive, bird house, sprinkler…). Plants grow while watered, even offline; tomatoes, apples and honey can be sold. Wildlife (11 species) moves in as biodiversity rises. Needs (Calm, Fitness, Fun, Brain, Social) decay over time and are refilled by furniture, activities, pets and parties. Real-clock day and night sky. Saved on the device (key `home`). VR: wrist menu > 🏡 Home.

## Realism pass (wellness worlds and My Home)
Meditation, Exercise, Dance Class, Escape Room and My Home have trim, window light shafts, drifting dust, normal-mapped floors, more people and real 3D models (candles, incense brazier, cones, sneakers, fridge, desk lamp, amber, skull, velvet and leather seating, an animated fox and pond fish). Home furniture uses the detailed models, with 8 new items. Ultra graphics adds denser grass, more dust and clouds, and stronger light shafts. Model credits: `assets/CREDITS.md`.

## Dance-off, trivia, mirrors, pets and the dashboard
- **🕺 Dance-off** (party bar or Mogul > Wellness & play): a Just Dance-style battle with a built-in beat, stick-figure move cards, Perfect/Good/Miss timing, combos and a rival score. VR detects arm poses.
- **🎵 Music Trivia** and bigger question banks (`QB` in the source): 55 music, 20 dance, 16 fitness, 10 mindfulness, 35 riddles, 30 cipher words, plus generated math, number-pattern and odd-one-out puzzles. Questions don't repeat until a bank is used up (stored per device).
- **🪞 Mirrors** with real reflections in the Dance Class Studio, Exercise Room and My Home (buyable item). You see your own avatar in them (it is drawn only in reflections). Only the nearest mirror you face renders live.
- **Pets** rebuilt with fur/feather/scale textures, jointed legs, blinking eyes and natural motion; the fox uses the animated Khronos Fox model.
- **Controls dashboard**: the expanded controls are grouped into labeled tile sections.

## Website layout
- `index.html`: the front page (turnupmusic.online). It links to the app and to GitHub, and forwards old share links (`/#watch=…`, `/#club`) into the app.
- `app/index.html`: the app itself (built from `build/turnup.src.html`).
- `guide.html`, `assets/`, `people/`, `img/`: shared files. The app looks for models in `../assets/` and `../people/` first.
- Custom domain: `CNAME` (added once the GoDaddy DNS records point at GitHub Pages).

## Trivia Live and karaoke upgrades
- **🎯 Trivia Live** (`TriviaLive` in the source): colored answer tiles, countdown, speed-based points with streaks, scoreboards and a podium. Solo or hosted for the whole party (new party channel `trivia`, host-authoritative). Players write their own quizzes (stored per device under `myQuizzes`) and can save quizzes a host shared.
- **Karaoke**: 7 more public-domain songs (11 total), a backing band in four styles with chords and bass fitted to the melody, pitch-based scoring with a note lane, duets with alternating lines, and a hype meter fed by cheers.

## Photo-real homes (Higgsfield)

My Home's ground, floors, walls, road, roof shingles and bark use photo textures made with Higgsfield AI (GPT Image), and the oak, pine, palm, cherry and maple trees are Higgsfield/Tripo 3D models (about 10k triangles, 1024px textures, ~0.7 MB each). They load from Higgsfield's CDN at runtime. The hand-drawn textures and trees show first and stay as the fallback, and on Low graphics.

## Model packs, My models (Sketchfab), phone expand

- **Model packs** (`HFP` in the app): several GLB models per file, loaded from Higgsfield's CDN and picked by node name (`hf:<pack>/<node>` works anywhere `asset()` is used). Packs: `living`, `decor`, `garden` (Poly Haven, CC0, real-world scale) and `pgym`, `pzen`, `ptokyo`, `pescape` (Higgsfield/Tripo 3D props). Stand-ins show until a model arrives and stay if it can't load.
- **Room textures**: the Meditation Room, Exercise Room, Tokyo street and Escape Room use Higgsfield photo textures (oak floor, plaster, tatami, shoji, rubber floor, concrete, lifting platform, wet asphalt, paving, herringbone parquet, damask, walnut panelling).
- **My models**: Sketchfab search (`api.sketchfab.com/v3/search`, downloadable only) and download (`/v3/models/{uid}/download` with the player's own API token); `.glb` or zipped `.gltf` import from the device. Stored in IndexedDB (`hm:<id>`), listed in `homeModels`.
- **Escape Room**: random six-puzzle sets from ten puzzle types, each with a "Show me the clue" camera move. Fixed a bug where "Look around" didn't actually hide the panel.
- **My Empire fix**: new $500 Pop-up Lounge starter club, cash shown, "need $X more" labels, toasts on buy/upgrade/hire, paging for owned and for-sale clubs, and handlers that re-read the wallet (no stale saves).
- **Home editing**: ✋ Move mode (tap/drag to pick up, drag or tap to place, camera-relative nudge pad, ↻ turn) and ↶ Undo / ↷ Redo for add, remove, move and turn (80 steps, money-consistent).
- **Phone expand**: the ⛶ button puts the Mogul game panel full screen (and requests landscape on Android). Bouncer cards zoom on tap.

## Neighborhood and jobs
- **My Home** has five lots (`Home.LOTS`): Maple Street (with a street, sidewalks and neighbors' houses), Beach House (animated sea), Aspen Cabin (snow, pines, mountains), Downtown Loft (rooftop with the city), Tokyo Garden House (bamboo, maples, torii, petals). Each lot saves separately (`home`, `home:beach`, …). New realistic trees (layered leaf clumps, bark, branches, palms with fronds), wind-swept grass, a gradient sky with a sun that follows the clock, and sun shadows.
- **Jobs** (`Jobs` in the source): staff in party worlds (servers with trays, photographers, security, custodians), lifeguards, guides, trainers and instructors; neighbors with routes on your street. Tapping anyone shows their name, career and a line about it.

## Kitchen, bathroom, walk-in closet and Cruising USA
- **My Home** now has side wings on every lot (open to the sky, like the main room): a **🍳 Kitchen** on the left and a **🛁 Bathroom** plus a **👗 walk-in closet** on the right, each with a doorway from the living room, its own floor, window and night light. Existing homes are furnished once, only where nothing is in the way (saves carry a `rooms` flag).
- New Build categories: **Kitchen** (counter, stove & oven, sink, island with stools), **Bathroom** (bathtub, shower, toilet, sink with mirror, towel rack) and **Closet** (wardrobe, clothes rack, sneaker wall). Using them refills needs (a cooked meal: Fun; a bubble bath: Calm…).
- **👗 My closet** (party bar, or tap a wardrobe or clothes rack at home): save the outfit you're wearing (clothes, colors, hat, eyewear, neckwear, accessory, headphones, glow) under a name, then change into any saved look with one tap. 6 hangers free, 24 for VIPs. Stored on the device as `closet` (`Closet` in the source).
- **🚗 Cruising USA**: a party-bar button and a buildable **Road-trip car** for the garden (homes come with one, except the rooftop loft). Both open Cruising USA VR (https://mrimagemakers.github.io/CrusingUSA/) in a new tab (`Cruising` in the source).
