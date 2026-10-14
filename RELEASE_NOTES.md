# MODDYS World Radio v1.7.1

The page grows a world: every station on a globe you can spin, zoom and play - and the pager finally behaves.

## What changed

**The World View.** Beside the station count there is now a 🌍 World toggle (the `w` key does the same): the list becomes a globe of the whole catalogue. Every station the catalogue can place is a dot - and where they crowd, they gather into clusters you can open. Drag to spin the earth; zoom with the buttons, the wheel, or a pinch. Pointing at a dot shows that station's card - its name, its place, the local solar time there - and a tap on, or near, a dot opens its player. The day/night terminator rides across the map in real time, the station that is playing carries a marker, and the search box and the filters prune the dots live as you type. ◎ flies to whatever a filter found; 🎲 flies to a random playable station and tunes it in; and the "📍 N unmapped" chip lists the stations that have no spot on the map - browsable and playable right there. The dots themselves came through the same pass as the site's: bigger, with a soft halo, and a tap area that reaches well past the dot.

**The arrows take you to the page.** They always did turn it - but every turn jumped you to the very top of the page. On a phone that is the header and the search field, with the freshly loaded stations sitting below the fold, which looks exactly like "the button did nothing". A turn now lands on the results, and turning from the bottom pager (240 cards down) comes back up to the first card of the new page.

**One tap, one page - never two, never none.** Two things could turn a page: the browser's click, and a fallback for the WebViews that swallow the click after a touch. Which of them had already acted was decided by a stopwatch, so a tap landing just inside the window was swallowed (nothing happened) and one just outside it was counted twice (two pages a tap). They now share a single flag per touch: the click claims its own touch, the fallback takes it only if no click ever arrived.

**The row is laid out across all formats.** On a phone and a tablet the back arrow owns the left end, the forward arrow the right end, and the page numbers sit together in the middle - it used to spread four items with a 136px hole between the back arrow and the first number. Every control is a 44px target, the page you are on is the cyan number between the arrows, and tapping a number is a jump: page 1 and the last page are always one tap away. The same row is used above and below the list.

**No more listener pile-up.** Every keystroke in the search field re-bound the pager and added another touch listener without removing the old one - twelve on a pager after six letters, and climbing for the rest of the session. The pager is bound once now.

**Screen readers hear the page change** ("Page 2 of 174"). Nothing new is printed on screen and the stations line above still carries only the count.

**A tidier header on a phone.** The five doors (Downloads, SynthHub, Music Hub, Pattern Forge, Resonance) used to stack as five full-width rows on a narrow screen; they now wrap as one compact cluster.

**The catalogue refreshes with the page.** 48,035 stations now - including Fresh 92.7 Adelaide's mounts and a hand-picked batch from the Icecast directory, each checked to play.

**The bundled page is the current one**, byte for byte.

## Verified

- the suite that drives the real page, against this page: 251 checks, 0 failed
- the same suite against what moddys.net serves: 251 checks, 0 failed
- the site's globe suites: the in-page globe 78 checks, the standalone World View page 194 checks, 0 failed
- `tools/shim_harness.py` drives the real shell over both bridges, against the bundled page: 76 checks, 0 failed - including the pager checks inside the app and the update notice
- the layout sweep over 14 device shapes: 14 measured, 0 broken
- the bundled `index.html` is byte-identical to the one this release puts on the site, and it is read back out of the published APK rather than off a build log

## Install

Open the app: it offers this itself - **Update now**, one tap. Your stations and favourites stay.

## Cheers Moddy !
