# Updates - VDO.Ninja

{% hint style="danger" %}
A general notice to users, on beta and alpha, the echo cancellation isn't working at the moment. It is working on the main production version however.\
If using vdo.ninja/beta/ or vdo.ninja/alpha/, switch to just vdo.ninja/ if having echo problems or wear headphones at low volume.\
I'm working on a fix, but I don't have an ETA. Will update when fixed.

_\*\*_ UPDATE: I hot-patched beta and alpha with a fix. This fix disables the option to select custom audio output destinations, but resolves the echo issue. If using a self-deployed instance, you can instead add [`&noap`](../general-settings/noaudioprocessing.md) to the URLs to fix it as well; you can also enable `chrome://flags/#chrome-wide-echo-cancellation`, patch the code, or just use headphones.
{% endhint %}

#### **September 19** <a href="#august-31" id="august-31"></a>

* With VDO.Ninja, if using [`&stereo`](../general-settings/stereo.md), `&s` , `stereo=5`, or [`&proaudio`](../advanced-settings/audio-parameters/and-proaudio.md), I'm now showing a little check-box that the guests themselves can check to set their mic input to MONO mode.\
  \
  While there's a few different ways to set a mic to mono mode, they aren't always obvious to people I'm finding, especially when using `&proaudio`/`&stereo` mode. For example, some guests will appear in the left or right-audio channel, due to their mic/interface setup. It's not always obvious on how to fix this when about to go live, so I'm hoping this helps avoids those situations.\
  \
  \-- It won't interfere with the screen share modes, so they will be stereo still\
  \-- It won't show if using `&stereo=1`, as that is explicitly stereo since a value is passed.\
  \-- The guest can toggle it on and off in the settings, without needing to go into any advanced audio settings\
  \-- The remote director can still use the existing "channel count' in the advanced audio settings to override this button, unless the guest toggles it back on\
  \-- There's several other ways to set mono mode of course, including [`&monomic`](../advanced-settings/upcoming-parameters/and-monomic.md), [`&inputchannels=1`](../advanced-settings/audio-parameters/and-inputchannels.md), [`&stereo=3`](../general-settings/stereo.md), channelCount, [`&mono`](../advanced-settings/view-parameters/mono.md) (playback), [`&ec&dn&ag`](../guides/audio-filters.md), and within OBS/Windows itself.\
  ![](../.gitbook/assets/image.png)![](<../.gitbook/assets/image (1).png>)\
  \
  \*\* updated on to alpha at vdo.ninja/alpha/

#### **September 17** <a href="#august-31" id="august-31"></a>

* [`&waitimage`](../advanced-settings/newly-added-parameters/and-waitimage.md) now has its wait image 'fit' to the screen, and [`&cover`](../advanced-settings/view-parameters/cover.md) will have it 'cover' the screen.
* [`&waitimage`](../advanced-settings/newly-added-parameters/and-waitimage.md) now works with scene links; not just basic view links.\
  (\*\* on alpha)

#### **September 16** <a href="#august-31" id="august-31"></a>

* Simplified the connection type wording in the stat's menu , plus made the publisher's connection type available to the viewer's side so you can more clearly see now if a guest has ignored your request to use Ethernet.\
  ![](<../.gitbook/assets/image (16).png>)\
  \*\*\* Changes on alpha at vdo.ninja/alpha/

#### **September 12** <a href="#august-31" id="august-31"></a>

* Added [`&effects=7`](../source-settings/effects.md) (or `&effects=zoom`), which will provide a manual zoom option in the effects menu. (you can also select the zoom mode via the effects menu, if available)\
  ![](<../.gitbook/assets/image (2) (4).png>)
* Added [`&getfaces`](../advanced-settings/upcoming-parameters/and-getfaces.md) on the viewer link (or `{getFaces:true}` via the IFrame API), which will request a continuous stream of face bounding boxes, for all inbound videos and all faces contained within. The data is transmitted to the parent IFRAME, and this data can be used for moving the IFrame window around, if you wish to make your own custom face-tracker or whatever else.\
  ![](<../.gitbook/assets/image (11) (1).png>)
* ``[`&effects=1`](../source-settings/effects.md) on the sender side (or `&effects=facetracking`) will auto-center the user's face in the center of their video, zooming in as needed. It takes a moment to initiate, but it offers a gentle PTZ-like effect.\
  \-- note: I previously had `&effects=1`, but it wasn't that good, so this is a more polished attempt. It's also available from the effects drop down menu now as a selectable option, as before I was hiding it.\
  ![](<../.gitbook/assets/image (3) (1).png>)\
  \-- important note: Both `&getfaces` and `&effects=1` requires the use of the Chromium experimental face detection API, as I'm using the built-in browser face-tracking model for this. You can enable the API flag here: `chrome://flags/#enable-experimental-web-platform-features` My hope is that this feature will eventually be enabled by default within Chromium, as loading a large ML model to do face detection otherwise is a bit heavy; you may need to enable this within the OBS CLI if wishing to use it there?\
  \*\*\* Changes on alpha at vdo.ninja/alpha/

#### **September 9** <a href="#august-31" id="august-31"></a>

* Added mobile touch support to the tap-to-focus (only mouse support previously).
* Minor issue with drag-to-zoom fixed.
* Fixed issue with not being able to reset video settings to default after changing them.
* [`&autohide`](../parameters-only-on-beta/and-autohide.md) works better now; also on mobile, the `&autohide` makes the control bar transparent on timeout, to avoid conflicts with tap-to-zoom/focus logic.
* It's easy to adjust video settings on mobile, as there is a large space to scroll without accidentally clicking a setting slider. Also more bottom padding, making it easier to click close in landscape mode.
* Made the [`&sticky`](../general-settings/sticky.md) redirect confirmation prompt less ugly, and I now don't ask if the URL already matches the saved session's URL.
* Made some changes/fixes to the recently new switchMode ([`&previewmode`](../advanced-settings/upcoming-parameters/and-previewmode.md)) function of the director room (hopefully no bugs?).\
  \*\* changes on alpha @ vdo.ninja/alpha/

#### **September 7** <a href="#august-31" id="august-31"></a>

* Added some notice icons to the PTZ controls, which show a tooltip on hover that explains remote PTZ only works if the remote window is visible.\
  ![](<../.gitbook/assets/image (1) (1) (3).png>)
* made the audio / video director control settings scrollable (max height \~500px), so you can more easily see the video while making changes to it.\
  ![](<../.gitbook/assets/image (8) (2).png>)
* Increased the size of Canadian and German turn relay servers (4x larger), and completed other backend maintenance.

#### **September 6** <a href="#august-31" id="august-31"></a>

* ``[`&showconnections`](../advanced-settings/upcoming-parameters/and-showconnections.md) will display the total number of p2p connections of a remote stream. Works with the director's room and the automixer. Might help give comfort over privacy/security during a stream.
* Total number of p2p remote connections (viewers) of a stream source will also appear in the stats menu, even without [`&showconnections`](../advanced-settings/upcoming-parameters/and-showconnections.md). Could be useful for debugging CPU/bandwidth issues.
* Connections may represent video/audio streams, or just a data-connection. Meshcast-hosted streams might not be accounted for, depending on how the viewer is connecting.\
  ![](<../.gitbook/assets/image (10).png>)
* Added `showChat` and `showDirectorChat` as HTTP/WSS API options for sending messages to guest(s). Useful if you want to hotkey a streamdeck command with some welcome message for guests.
* Added events notifications relating to the director's guest-mute, guest-video-mute, and guest-position-change actions, along with any remote-video-mute updates to the HTTP/WSS API (by request for the bitfocus companion app)

\*\* on alpha

#### **September 2** <a href="#august-31" id="august-31"></a>

* [Noise gate](../source-settings/noisegate.md) remote control has been tweaked a bit; the correct state is loaded now on a director's page refresh
* Added an option to control the [compressor](../source-settings/and-compressor.md) remotely (3 states for the compressor; Off/On/Limiter)\
  ![](<../.gitbook/assets/image (3) (1) (2).png>)
* Fixed issues on alpha, including now where the [labels](../general-settings/label.md) for guests were not always positioning correct if audio-only
* \*\* changes on alpha @ vdo.ninja/alpha/

#### **August 31** <a href="#august-31" id="august-31"></a>

* Added a button in the director's room. It lets you toggle between a Preview layout and the normal Director layout; the Preview layout will mirror what a basic [`&scene=0`](../advanced-settings/view-parameters/scene.md) link would look like. Useful if you want to switch to a guest-like mode as a director, and then switch back as needed to the director's room to make adjustments. - to enter this mode by default, [`&previewmode`](../advanced-settings/upcoming-parameters/and-previewmode.md) can be used by the director \*\* on alpha at vdo.ninja/alpha/\
  ![](<../.gitbook/assets/image (1) (2) (4).png>)
* ``[`&noisegatesettings`](../advanced-settings/upcoming-parameters/and-noisegatesettings.md) has been added to vdo.ninja/alpha/, which is used in conjunction with [`&noisegate`](../source-settings/noisegate.md). This feature lets you tweak the noise-gate's variables, making it more or less aggressive as needed. example:\
  `https://vdo.ninja/alpha/?noisegate&noisegatesettings=10,25,3000`\
  ``It takes a comma separated list:\
  \-- First value is target gain (0 to 100), although 0 to 40 is probably the recommended range here\
  \-- second value is the threshold value where the gate is triggered if below it. \~ 100 is loudly speaking, \~ 20 is light background noise levels, and under 5 is quiet background levels.\
  \-- third value is how 'sticky' the gate-open position is, in milliseconds. Having this set to a few seconds should prevent someone from being cut off while speaking or if taking a short pause.

#### August 25

* Added new sender-side parameters that can customize how you want VDO.Ninja to balance resolution vs frame rate, specifically when bitrate or CPU is insufficient to offer both at the same time.\
  \-- for video, [`&contenthint=detail`](../advanced-settings/upcoming-parameters/and-contenthint.md)``\
  ``-- for screen-shares, [`&screensharecontenthint=motion`](../advanced-settings/upcoming-parameters/and-screensharecontenthint.md), which will override [`&contenthint`](../advanced-settings/upcoming-parameters/and-contenthint.md) for just screen-shares if set also.\
  The two options for video are `detail` or `motion`. Screen shares generally tends towards `detail` by default, and camera sources are tend towards `motion` by default. `detail` will try to prioritize resolution over frame rate, so the frame rate may drop a lot used. `motion` will try to maximize frame rate, but may drop the resolution a lot. There's no way to force both on as there's no magic bullet if your CPU or network cannot keep up. note: If using [`&codec=vp9`](../advanced-settings/view-parameters/codec.md) on the viewer side, the frame rate may drop as low as even 5-fps.\
  \-- Also for audio, I've added [`&audiocontenthint=music`](../advanced-settings/upcoming-parameters/and-audiocontenthint.md) The two options are `speech` and `music`. No idea what it does exactly, but when using `music` there seems to be a fixed bitrate of 32-kbps sent out by default, where as with `speech` it is variable, using less bandwidth when not speaking.\
  These parameters have been tested on Chrome, but other browsers may vary in behavior. Safari seems to just ignore things, for example. \*\* changes on alpha

#### August 23

* Updated the translation files on GitHub and on vdo.ninja/alpha/, so recently added UI elements can have alternative translations added
* Custom scenes will now be sorted based on alphanumerical value. (rather than order of connection). \*\* on alpha\
  ![](<../.gitbook/assets/image (1) (2) (5).png>)

#### August 22

* When you toggle the customize-scene-link function as a director, some of those items will now be applied to the guests' solo link also. (just the ones I think are relevant)
* [`&sharper`](../advanced-settings/upcoming-parameters/and-sharper.md) and `&sharpen` are now aliases of [`&dpi=2`](../advanced-settings/view-parameters/dpi.md), which should 'up to' double the amount of playback video resolution, if the dynamic resolution optimization is enabled at least, in certain cases. This is a lot like [`&scale=100`](../advanced-settings/view-parameters/scale.md), but perhaps _slightly_ more efficient in some cases. This is mainly for when you intend to have a large screen-shares in a scene, where you don't want the tiny guest videos to be a 100% scale, but 50% scale is fine (up from 25% scale). `&dpi` already exists on production, but by adding these aliases, I hope it's more discoverable.
* As an alternative to `&sharper`, I've also added [`&sharperscreen`](../advanced-settings/upcoming-parameters/and-sharperscreen.md), which sets `&scale=100`, but _only_ for screen-shares. (virtual cameras not included). This is probably even more efficient than `&scale=100` or `&sharper`, and it's designed for when screen-sharing a lot of text. Text looks a bit soft when streaming video at 1:1 pixel resolution.\
  It's recommended to only use these parameters within the context of a scene link, and not on guest links, due to the higher CPU / bandwidth it may use.
* Chunked mode on alpha lets you switch cameras/audio now, without them breaking; muting video still breaks things tho. (chunked mode remains a WIP) \*\* changes push to alpha
* Put up a YouTube video (second in a series so far) where I am investigating the performance of a cellular bonding device and its software, specifically as it relates to VDO.Ninja uses. If on a bad connection, doing remote streaming, or just want some added stream reliability, cellular-bonding seems worth considering. [https://www.youtube.com/watch?v=-BNpoWhzKHw](https://www.youtube.com/watch?v=-BNpoWhzKHw)

#### August 17

* Added the option to customize the [`&grid`](../advanced-settings/design-parameters/grid.md) (`&ruler`/`&thirds`) effect by passing an image link. (can help center guests)\
  \-- transparent PNG or an SVG file are the recommended options.\
  \-- it will stretch to cover the camera preview-area, so probably best to keep things 16:9 aspect if needed.\
  \-- URL can be URL-encoded, for more complex URLs. Simple URLs might work without.\
  \-- technically this can be used as an overlay for other things, but it only works with the self-preview.\
  \-- leave the passed value empty if you wish to have the white basic rule-of-thirds show as default.\
  example: `https://vdo.ninja/alpha/?thirds=./media/thirdshead.svg`\
  ``\*\* on alpha.\
  ![](<../.gitbook/assets/image (7) (1).png>)
* Added [`proxy.vdo.ninja/alpha/`](https://proxy.vdo.ninja/alpha/) as an alternative to `vdo.ninja/?proxy`. If's a more user-friendly version of [`&proxy`](../newly-added-parameters/and-proxy.md). \*\* Just on alpha for now

#### August 16

* ``[`&activespeaker=3`](../advanced-settings/view-parameters/activespeaker.md) and `4` added; which are the same as `1` and `2`, except it will not switch to show audio-only sources (just video only). As a recap, active speaker mode shows the person(s) who are actively speaking, and hides those who aren't.
* Fixed a bug/race condition in Chrome where the web-audio audio effects pipeline and having to 'click-to-play' didn't always unmute all the audio. (`&activespeaker` mode when viewed as a scene, in chrome, for example. Wasn't an issue in OBS)
* Changed chunked mode a small bit, so the video stream uses the same frame rate and resolution of the original video source, rather than a fixed resolution/frame rate.
* Chunked mode should work with audio-only or video-only tracks now
* Solo links are setup to use [`&solo`](../advanced-settings/upcoming-parameters/and-solo.md) instead of `&scene` now; it's the same outcome, except `&solo` tells the system not to apply custom 'layouts' to them. Links updates in the director's room and the mixer app.\
  \*\* changes on the alpha version of VDO.Ninja at [https://vdo.ninja/alpha/](https://vdo.ninja/alpha/)
* Added details on how to fix camera permissions denied, improving the messaging with an image and doc link. \* on alpha\
  ![](<../.gitbook/assets/image (1) (7).png>)

#### August 11

* Right clicking the screen-share icon will give you an option to open the screen share in a new tab, all pre-configuerd. Useful if you want to share multiple windows while in a group room, or don't want to see your own screen share while talking to others.\
  ![](<../.gitbook/assets/image (3) (3).png>)
* Bugs with [`&screensharetype=3`](../newly-added-parameters/and-screensharetype.md) have been resolved, I think. (this mode supports desktop-audio capture without echo issues)

#### August 9

* ``[`&aspectratio`](../advanced-settings/upcoming-parameters/and-aspectratio.md) now works with screen shares, so you can force crop an incoming screen share to be a certain aspect ratio. If [`&screenshareaspectratio`](../advanced-settings/upcoming-parameters/and-screenshareaspectratio.md) is used, (`&ssar`), it will apply to just screen shares. If `&ssar` does not have a value passed, it's assumed to be set as "default", which overrides `&aspectratio` option, if used also. \*\* on alpha, ie: vdo.ninja/alpha/?ar=2.0

#### August 6

* The API / IFRAME sandbox page for developer using VDO.Ninja got a style update and facelift by @Sam MacKinnon Ty,\
  \* it's on alpha at [https://vdo.ninja/alpha/iframe](https://vdo.ninja/alpha/iframe) and GitHub.\
  ![](<../.gitbook/assets/image (6).png>)

#### August 5

* When the director talks to you in solo-talk mode, the other guests in the room now drop to 25% volume. This way the guest the director is talking to can hear the director more clearly. (by request) \* on alpha, [https://vdo.ninja/alpha/](https://vdo.ninja/alpha/)

#### August 3

* ``[`&hidecodirectors`](../advanced-settings/upcoming-parameters/and-hidecodirectors.md) will hide the co-directors from appearing in the director's room. You might have a few co-directors join you, but they might be taking up space, so this is a way to prevent that. It simply hides the boxes; they are still there at a code level.
* Added [https://updates.vdo.ninja/](https://updates.vdo.ninja/), which will mirror the updates from this discord 📑│updates channel, which should be helpful for those not using Discord to see development progress. (basic, but will undergo more updates). The Discord in general has been undergoing improvements; the mods here have been working hard to keep the discord and documentation functional, so thank you to them.
* Added [`&mobile`](../advanced-settings/upcoming-parameters/and-mobile.md) and [`&notmobile`](../advanced-settings/upcoming-parameters/and-notmobile.md) as a couple options to vdo.ninja/alpha/ I already have [`&flagship`](../advanced-settings/upcoming-parameters/and-flagship.md), [`&noscale`](../newly-added-parameters/and-noscale.md), and [`&forceios`](../advanced-settings/mobile-parameters/and-forceios.md) as a few options to configure mobile devices, but mobile/notmobile are more generic options that will optimize a guest/push link based on whether VDO.Ninja thinks they are a smartphone or not. `&mobile` might help reduce CPU issues, and `&notmobile` might be able to improve video quality (in case you want to override the automatic defaults, which already detects if a device is mobile or not).

#### August 1

* Chat messages that contain URLs will now have those URLs be clickable (opens into a new window)\
  ![](<../.gitbook/assets/image (1) (1) (2).png>)
* The pop-out chat feature has had a bug fixed and minor polish applied
* When using the IFrame API to control bitrates, I have added an optional called "lock" that lets you affix the bitrate you set so the rest of VDO.Ninja doesn't try to constantly override it. `{bitrate: 2500, lock:true}` for example. I also assume `lock=true` by default, so no changes are needed really to start benefiting from this. (previously you had to disable the auto-mixer to lock a bitrate).
* Also added `{manualBitrate: xxx}` to the IFrame API , which is a bit like `bitrate`, but keeps track of what the current target bitrate should be. When you set `manualBitrate=false`, it will apply the expected target value. Also, it won't work when used in conjunction with custom audio bitrates, whereas bitrate will.
* There's a third new bitrate option, which is `targetBitrate`, which lets the automixer keep doing its thing, but it sets a new max target bitrate. The target bitrate will still be applied when set, but the automixer may lower it if needed when it decides to, but it's the new target for 'unlocked' max speed. Some browser will ignore it though, if it's set higher than the bitrate that was manually set the via URL, so it's probably something you don't want to use along with `&bitrate`.

#### July 27

* Fixed the new OBS [`&remote=xx`](../general-settings/remote.md) not working correctly when a password was set (on alpha and GitHub)

#### July 24

* Fixed a bug where if the director is highlighted, newly loaded scenes would be blank.
* Added two-way solo talk as an option to the http/wss VDO.Ninja API.
* Also, - added the ability for VDO.Ninja to _**Remotely Control OBS Studio**_ while streaming/directing; useful for IRL maybe?\
  \-- The menu button to control OBS auto-shows in the director's view or push-mode, if OBS Studio is set to give VDO.Ninja "full" permissions.\
  \-- The menu button can also be added manually, for even guests, using [`&controlobs`](../advanced-settings/upcoming-parameters/and-obs.md)``\
  ``-- [`&obsoff`](../advanced-settings/design-parameters/and-obsoff.md) can be used to set permissions to fully off (also disables tally light and scene optimizations tho) when added to the OBS browser source link.\
  \-- The OBS instance still needs [`&remote={optional-passcode-here}`](../general-settings/remote.md) added to the URL for remote commands to work. If \&remote is left blank, it gives anyone permissions to control it. If a value is passed to `&remote`, the sender needs to have a matching \&remote value or manually enter they need to manually enter passcode in the pop up control menu.\
  \-- If the OBS browser source has its permissions set to something other than full (lower than level 5), the control menu will still show what info it has -- current scene, recording/streaming state, etc; depending on level. The lower the level, the less info is available to show; can't remotely change anything though.\
  \-- It supports multiple OBS instances and will label them according to the [`&label=xxx`](../general-settings/label.md) value set on the scene/view link, or whatever the unique connection ID is.\
  \
  All this is on alpha, at [https://vdo.ninja/alpha/](https://vdo.ninja/alpha/)\
  ![](<../.gitbook/assets/image (2) (1) (4).png>)![](<../.gitbook/assets/image (3) (5).png>)

#### July 23

* The [`&webp`](../advanced-settings/view-parameters/webp.md) mode has been modified a bit. Main change is that you now enable it by add `&webp` to the sender's URL, and [`&codec=webp`](../advanced-settings/view-parameters/codec.md) to the viewer's URL (otherwise, it falls back to normal video mode). No need for \&broadcast anymore. (as a reminder, this mode sends the video as a series of low-quality images, rather than a more efficient video stream).
* I've removed the toggle in the director's room for this `&webp` feature, as [`&chunked`](../newly-added-parameters/and-chunked.md) mode is replacing its purpose there, but you might still want to use this mode when the viewer-side does not support video playback or hardware acceleration. Specifically, this option lets you bring motion images (aka, crude video) into the Streamlabs mobile app, as a browser source, where other forms of video decoding is not supported.
* I've also created a new viewer-side option called [`&slideshow`](../advanced-settings/upcoming-parameters/and-slideshow.md) . This option decodes incoming video (first video to load), but plays them back as series of full-window images. That is, a single image element, that gets updated 24 times a second, instead of playing the video back within an efficient video element. I have no idea why you might want this option, as it pretty crude up and uses up a lot of CPU, but you can right-click to save a single frame from the video to disk, as a PNG file. This might be useful if you need to take a lot of snap shots of some video and don't want to have to hassle with cropping a window-grab. Quality of the images is pretty high; near lossless.\
  \*\* on alpha\
  ![](<../.gitbook/assets/image (5).png>)

#### July 21

* The [`&grid`](../advanced-settings/design-parameters/grid.md) overlay option now works in non-room mode
* Added the toggles for `&grid` and [`&avatar`](../advanced-settings/upcoming-parameters/and-avatar.md) to the director's link customization section.
* Added [`&smallshare`](../advanced-settings/upcoming-parameters/and-smallshare.md) as a new option, which makes the screen share behave like a webcam share. ie: not larger in size vs other windows, for the publisher or the viewers. This is a push-side parameter. This is useful if a VR guests screen sharing an app of themselves, versus using a virtual camera. It can also be useful for gaming, where a larger screen share might bog down the system of the sender more than needed.\
  \*\*\* on alpha at vdo.ninja/alpha/

#### July 20

* Updated the local audio controls to have a NOISE GATE option.\
  \-- This is a new noise gate, that lowers your mic volume to 10% of its current value based on volume-level activity. If you haven't made a significant sound in few seconds, the noise gate kicks in, and will re-enable when a significant noise is detected. It will take about 300-ms for the volume to recover once the noise triggers it back on, which can be a small bit harsh/distracting at times.\
  \-- [`&noisegate`](../source-settings/noisegate.md) or `&noisegate=1` (`&gating`/`&ng`) will enable it by default (if using it in a room, currently); and `&noisegate=0` will hide the option from the menu.\
  \-- The older existing `&noisegate=1` option I moved to `&noisegate=4`, as this new version is replacing it. I'm keeping the older version around as an option though.\
  ![](<../.gitbook/assets/image (7).png>)
* Fixed some of the labels for the local audio labels; camel-case is replaced with words, and true/false replaced with on/off.
*   Fixed an issue where iPhones's video output would freeze when the director would feature-highlight any other participant.

    \*\* on alpha at vdo.ninja/alpha

#### July 19

* Added the ability to "tap to focus" when a camera supports focusing. You'll want to switch the camera over to manual focus (via settings->video->focusMode) before it will be active, but then you can just touch on the screen to have it auto-focus on that spot. Note: It's a bit slow and not 100% accurate and may conflict with the zoom, if used. **on alpha at vdo.ninja/alpha**
* Improved the advanced video settings; focus, exposure, white-balance. The auto and manual modes are now a checkbox, and I worked out a few of the odd behaviour issues that Chrome + Logitech webcams were having when try to set modes/values. \*\*\* on alpha at vdo.ninja/alpha\
  ![](<../.gitbook/assets/image (2) (1).png>)

#### July 16

*   Added an option to post a snapshot of your local camera to a HTTPS/POST URL (blob/jpeg)\


    ```
    https://vdo.ninja/alpha/?postimage=URL_TO_POST_IMAGE_TO_AS_BLOCK&postinterval=INTERVAL_IN_SEC
    ```

    \
    so, for example, [`https://vdo.ninja/alpha/?postimage=https%3A%2F%2Ftemp.vdo.ninja%2F&postinterval=30`](https://vdo.ninja/alpha/?postimage=https%3A%2F%2Ftemp.vdo.ninja%2F\&postinterval=30) posts to a sample test server I have up. The URL is URL encoded, but not always necessary.\
    \
    If posting to my test server, the image can be accessed at `https://temp.vdo.ninja/images/STREAMID.jpg`. There's caching enabled mind you, so you'll want to post-fix the current timestamp to the URL to disable that per request.\
    \
    For example, `https://temp.vdo.ninja/images/yiMkpMg.jpg?t=3412341234`\
    \
    This feature could be useful to checking out a stream before actually connecting to it, as that's my intent with it, but it is also something you can use with Octoprint, where you need an IP camera jpeg source as input.\
    \
    \*\* on alpha, at [`https://vdo.ninja/alpha/`](https://vdo.ninja/alpha/)``

#### July 14

* The [`&website`](../source-settings/and-website.md) function now lets you start/stop and change website sources; no longer is it just one site and that's it. (only the director previously could change websites constantly). I suppose you could use this to remotely change inputs in an OBS browser source via a remote website, as I think the YouTube implementation supports synced playback/scrubbing.
* There's toggle in the director's room now to add [`&scale=100`](../advanced-settings/view-parameters/scale.md) to the scene links. Might improve sharpness a bit, at the cost of increased CPU/network load.
* Fixed an issue where if a guest was viewing the director in full-window mode, and the director changed the total room bitrate value, the new [`&totalroombitrate`](../advanced-settings/view-parameters/totalroombitrate.md) value would be ignored by that guest until they exited the full-window mode.
* Also fixed an issue where if setting a custom total room bitrate value higher than 4000 via the URL ([`&totalroombitrate`](../advanced-settings/view-parameters/totalroombitrate.md)), the slider to adjust the TRB value will be extended so the max range is that of the URL value if higher than 4000.\
  \
  \*\* on vdo.ninja/alpha/ for testing.

#### July 10

* Tweaked the mic meter on vdo.ninja/alpha (3x more intense) and added a visual meter to the settings menu; should help judging if you're mic is active easier. (by request)
* In case curious, I've been working on quite a few core-components and larger new features for VDO.Ninja this week. ie: chunked video improvements, IFrame API enhancements, refactoring code for future ui dev efforts, and some invite management features. I'll probably update more on those things once they are further along or complete.

#### July 3

* Unless manually specified ([`&screensharequality`](../source-settings/screensharequality.md) or [`&screenshare`](../source-settings/screenshare.md)), I have the screen share resolution matching the webcam resolution now. This avoids a sudden CPU spike when screen sharing; still room for improvement tho.
* For the time being, I have [`&limittotalbitrate`](../source-settings/limittotalbitrate.md) only applying to guests, rather than all viewers. I need to revisit this at some point soon.\
  \
  \*\* changes on alpha

#### July 1

* The WSS API (wss://api.vdo.ninja) has been expanded to include hang up events for publishers, along with viewer-side events for incoming connections/streams. These efforts will lead to a richer StreamDeck integration.
* Add [`&background`](../advanced-settings/upcoming-parameters/and-background.md), which accepts a URL-encoded image URL to make as the app's default background. For example, [`https://vdo.ninja/alpha/?appbg=./media/logo_cropped.png`](https://vdo.ninja/alpha/?appbg=./media/logo\_cropped.png) . The image will scale in size to cover the VDO.Ninja app's background. [`&chroma`](../advanced-settings/design-parameters/chroma.md) can still be used to set the background color, if using transparencies. There already exists [`&bgimage`](../advanced-settings/upcoming-parameters/and-bgimage.md), which will set the default background image for videos; this however will set a background image for the entire page.\
  ![](<../.gitbook/assets/image (2) (5) (1).png>)\
  \
  \*\* These changes are on alpha

#### June 30

* Fixed a bug with [`&statsinterval=100`](../advanced-settings/parameters-only-on-beta/and-statsinterval.md) not updating on sender side (only viewer side before). This updates how frequent the stats updates.
* Added the ability to dynamically change the scale of a video to the IFRAME API. accepts scale, plus optionally uuid or a stream ID as a a target.
* Added [`&base64js`](../advanced-settings/upcoming-parameters/and-base64js.md), which lets a user add raw java script to the URL to run on page load. `https://vdo.ninja/alpha/?jsb64=YWxlcnQoJ2hpJyk=` to test.\
  \
  \*\* changes on alpha

#### June 28

* Added support for [`&buffer`](../advanced-settings/view-parameters/buffer.md) and [`&sync`](../advanced-settings/view-parameters/sync.md) to the viewer when using [`&chunked`](../newly-added-parameters/and-chunked.md) mode on the sender. If on an unstable connection, setting the buffer to a few seconds can help avoid pauses in the video playback, as there will be some buffer to use. (a bit experimental still -- so it might be more a WIP still ).
* Added a new url param called [`&include`](../advanced-settings/upcoming-parameters/and-include.md), which is like [`&view`](../advanced-settings/view-parameters/view.md), except it's for including streams that do not exist in the room you are in, assuming those streams are not in another room and have matching passwords. So, useful for adding basic push-streams that you might want to be in multiple rooms at the same time, but not actually be locked to any room. (`&view`, conversely, is pretty exclusive; that or nothing.)
* Been playing around a new flag called [`&flagship`](../advanced-settings/upcoming-parameters/and-flagship.md), which will optimize the mobile experience for more capable smartphones; essentially, streaming higher quality video to other guests versus the normal mobile-performance mode.
* I've also modified the non-flagship mode, for low-end mobile devices, to use the [`&limittotalbitrate`](../source-settings/limittotalbitrate.md) flag by default (500-kbps). [`&limittotalbitrate`](../source-settings/limittotalbitrate.md) hasn't been that heavily tested yet, but it's part of v22 and might be better than [`&totalroombitrate`](../advanced-settings/view-parameters/totalroombitrate.md); currently I'll increasingly use them together I think though. They are both the same concept, except one is viewer-side controlled, and the other is sender-side controlled; both limit the bitrate that guests in the room see based on the number of guests in the room.\
  \
  \*\* changes to alpha, at [https://vdo.ninja/alpha/](https://vdo.ninja/alpha/)

#### June 25

* The api.vdo.ninja remote control API is expanded to send push event notifications to web-socket listeners when the local mic/speaker/camera is muted. This was added on request for making the bitfocus companion app smarter about keeping track of mute states. (on alpha)

#### June 16

* Option to randomly generate a room name has been added to the room-creation page - minor fixes to the mixer have been applied; (lots more to do)
* [`&aspectratio`](../advanced-settings/upcoming-parameters/and-aspectratio.md) + [`&crop`](../other-parameters.md) (sender side options) has been updated to work with more camera/sources. If you do `vdo.ninja/alpha/?webcam&aspectratio=0.5625` for example, you'll get portrait mode. Not compatible with Safari though.
* Video/audio stats for Firefox have been improved; resolution, framerate, codec, bitrate.
* [`&meshcastcodec=h264`](../meshcast-settings/and-meshcastcodec.md) won't fail when using Firefox and Meshcast
* [`&chunked`](../newly-added-parameters/and-chunked.md) recording in the director's room works correctly\
  \
  \*\* These changes are on beta @ vdo.ninja/beta

#### June 9

* Viewers of [`&meshcast`](../newly-added-parameters/and-meshcast.md) streams can use [`&buffer=500`](../advanced-settings/view-parameters/buffer.md) now; on alpha

#### June 8

*   When screen sharing, if the resolution that's requested by the viewer is roughly 100% full scale, (a value based on their window viewing size), the system will now snap the resolution up to 100% (like [`&scale=100`](../advanced-settings/view-parameters/scale.md)). This should help with video sharpness (text, etc), when the added burden of slightly more CPU load is worth it. Won't snap if the different is great though.

    \
    For example, if a viewer is on a 720p display, watching 1080p content from a director, that's not close enough to make it worthwhile for the director to send 1080p. But if the viewer's window was 1050p, then sending the full 1080p video is worthwhile. This is mainly because scaling seems look nicer when done on the viewer's end, instead of the sender's side.

    \
    Only applies to screen shares, as text-scaling is kind of ugly, and it seems to be commonly desired to make fonts less ugly when screen-sharing. Scaling will still occur, but it won't be as ugly when done by the viewer. Sending 100% all the time works too, via `&scale=100`, but is pretty inefficient and needlessly heavy on the CPU in most cases.
* Fixed on issue where is screen sharing as a director, before turning on your camera, didn't show the screen for guests always.
* If the director isn't a performer, I've added the option to still add a director to/from groups. The group buttons show up in the control bar; where you can add them either via \&groups=1,2 or via the api.vdo.ninja / companion service.\
  \--- Toggling the director in/out of a group via the API is new. (NULL targets director).\
  \--- If [`&showdirector`](../viewers-settings/and-showdirector.md) is used, it will not use the control-bar for group buttons 1 to 8\
  \--- It technically is possible to use groups via the API or URL other than 1 to 8, but I only offer buttons to add guests to groups 1 to 8.\
  ![](<../.gitbook/assets/image (84).png>)
* Using the [`&api`](../general-settings/api.md) remote API option, you now can get STATE values as the reply to a GET/POST/WSS request.\
  So if you do `https://api.vdo.ninja/c6sWHN9zzX/group/null/1`, with `&api=c6sWHN9zzX` added to the director's URL, you will toggle the director in and out of GROUP 1.\
  The response of the HTTP GET request though will be `true` or `false` or `timeout`, based on whether the director was added to the group, removed from the group, or whether it failed. This new feature can be used with a Streamdeck (or other controller) to have the button's color of the Streamdeck match the state of the action.\
  [https://github.com/steveseguin/Companion-Ninja/blob/main/README.md#callbacks--state-responses](https://github.com/steveseguin/Companion-Ninja/blob/main/README.md#callbacks--state-responses)\
  ![](<../.gitbook/assets/image (15).png>)\
  \
  \*\*\* This is only supported on vdo.ninja/alpha/ currently

#### June 7

* When holding `CTRL` and selecting multiple videos to record as a director (in control room), it won't ask for the video bitrates multiple times now; just once for all the selected videos. (this hot fix has been applied to production and beta). This feature is useful for recording multiple videos in sync.

#### June 6

* Fixed an issue where if you did `right-click -> record` of a inbound-video, and then hung up without stopping the recording, the recording wouldn't stop and finalize. (on alpha)

#### June 4

*   Added the ability to have multiple unique audio output destinations per VDO.Ninja instance.

    \
    To use at the moment, right-click a VDO.Ninja video in chrome/edge/electroncapture, (on the alpha-version of VDO.Ninja), and you'll see a menu option to change the audio output destination. This selected output destination overrides the default audio output destination set in the VDO settings menu, and it's specific to just the video that you right-clicked.

    \
    This option allows you to have one audio stream output to a virtual cable, and another output to your headset, for example.

    \
    Over the next few days I will probably change up how the menu works, as its pretty crude right now,. This feature also doesn't work in Safari/Mobile or if audio processing is disabled, so that UX aspect needs work. Hoping it's a good start for now though; testing welcomed.\
    ![](<../.gitbook/assets/image (57).png>)\
    \*\* on vdo.ninja/alpha/

#### June 2

* [`&sensor`](../source-settings/sensor.md) now also includes speed and altitude data (on production)
* Added a demo/sample on how to overlay speed + acceleration on top of video playback (compatible with a mobile phone sender) `vdo.ninja/examples/sensoroverlay?view=STREAMID`
* Added a new option to explicitly list what sensor data you want to capture and transmit, when using `&sensor` [`&sensorfilter=gyro,lin,acc,mag,pos,ori`](../advanced-settings/upcoming-parameters/and-sensorfilter.md) For the above demo, you can use [`&sensorfilter=pos,lin`](../advanced-settings/upcoming-parameters/and-sensorfilter.md) to just send the data you need, reducing the load on the phone/network. (on alpha)
* Right-clicking a link in VDO.Ninja will now offer the option to show the link as a QR Code. This makes it easy to copy any link over to a your mobile phone or to create a shareable QR code with guests. (on alpha)\
  ![](<../.gitbook/assets/image (2).png>)![](<../.gitbook/assets/image (1) (9).png>)
* Implemented a workaround for a novel Chrome bug where specifying a custom audio channel in the director's room (C1, C2, etc) would break the custom audio output device support. \* Fix pushed to alpha.

#### June 1

* Added the [`&meshcastscale`](../advanced-settings/upcoming-parameters/and-meshcastscale.md) (`&mcscale`) parameter; this will scale down the Meshcast video output via the URL, post camera capture setup. Because of how Meshcast works, this is a sender-side parameter. You may wish to use this to lower the resolution if your camera has a fixed capture resolution. (Alternatively, if you need to dynamically adjust the resolution, that option already exists via camera settings via width/height slider adjustments) `https://vdo.ninja/alpha/?meshcast&mcscale=50`
* Fixed a conflict when using [`&director`](../viewers-settings/director.md) parameter + [`&webcam`](../source-settings/and-webcam.md)/[`&website`](../source-settings/and-website.md)/[`&screenshare`](../source-settings/screenshare.md) parameters at the same time (the later parameters get disabled now, avoiding conflicts)
* If using a view-push link combo, just to be safe, I have the viewer re-request unloaded streams automatically at a interval now. For unattended viewing sessions.
* Pausing a video while it is in 'full window' mode, will actually pause it now.
* Added a "channelCount" option to the audio controls, which will let the director/sender toggle between Stereo and Mono audio channels, _IF_ [`&stereo`](../general-settings/stereo.md)/[`&proaudio`](../advanced-settings/audio-parameters/and-proaudio.md) is added to the sender's URL and the sender supports +2-channels. So, if you're using `&stereo` on your guests, and you can only hear one of your guests on the left or right channel, you can use this to down-mix their microphone to a mono channel only.\
  \
  Due to some tricky technical challenges, this feature involves down mixing with web-audio nodes, and stereo can't be enabled if `&stereo` isn't in the URL. It might also make all audio from that guest mono at the moment. (adding [`&mono`](../advanced-settings/view-parameters/mono.md) to the view URL also works, but that will make all sources in the view link mono)\
  ![](<../.gitbook/assets/image (2) (5).png>)\
  \
  \*\* all updates on alpha at [`https://vdo.ninja/alpha`](https://vdo.ninja/alpha)``