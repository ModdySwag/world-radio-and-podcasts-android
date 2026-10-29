# MODDYS World Radio & Podcasts v2.0.0

The app stops being a pure radio. The podcast directory now lives inside it - 58,795 shows you
can browse by shelf or search by typing, ranked on the phone in about 7 ms - so the one door the
header keeps is a door that opens something.

## What changed

**The podcast directory ships in the app.** `podcasts.html`, the shelf manifest, the 54,539-show
search corpus and the 81 shelf files all ride in the bundle. Browsing works with no network at
all; only a show's feed, its charts and its artwork go online. Search ranks locally, so there is
no round trip and no server watching what you looked for.

**One door in the header.** Inside the app the site doors were hidden outright, because five of
them led to pages the app does not carry and the sixth led nowhere at all. Now exactly one
survives - the podcast directory - and it opens. The Radio link at the top of the directory
brings you back.

**Under the icon the name is shorter.** "MODDYS World Radio & Podcasts" is 29 characters, and a
launcher ellipsises that at about twelve. The icon says **Radio & Podcasts**; the store listing
carries the full name.

**Charts work in the app.** The page runs from a `file://` origin, whose origin is "null", and
Apple's chart endpoints answer that with no usable CORS header - so every chart was an error
while the bundled directory worked. The WebView no longer enforces CORS against a page we ship
ourselves.

**One 404 fewer.** `radio.html` loads `app-install.js`, which was never in the bundle, so every
load logged a missing file. It ships now.

**The bundled web app is today's**, byte for byte - including the newer globe, the World View
labels and the current 71,577-station catalogue, which the bundle had been two weeks behind on.

## Verified

- `tools/shim_harness.py` drives the real shell over both bridges against the bundled page:
  **80 checks, 0 failed** - two of them new, pinning that `podcasts.html` and `radio.html` are
  followed inside the app rather than handed to the browser
- `probe-app-bundle.py` walks the whole path over `file://`, the way this WebView loads it: one
  door, the tap, the manifest and a shelf loading over `file://`, the corpus on focus, "joe rogan"
  landing on The Joe Rogan Experience, and the way back - **21 checks, 0 failed**
- the site's page suite against this page: **277 checks, 0 failed**
- the site's podcast suite: **80 checks, 0 failed**
- every bundled web file - `index.html` included - is read back out of the published APK and
  compared with the site's copy, byte for byte

## Install

Open the app: it offers this itself - **Update now**, one tap. Your stations and favourites stay.

## Cheers Moddy !
