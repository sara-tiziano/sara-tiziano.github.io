# The Roman Wedding Retrospective — Project Overview & Context

This document captures the essential context, design language, structural hierarchy, and technical architecture of the single-page editorial wedding website. Keep this alongside `index.html` to brief future collaborators, developers, or AI assistants.

## 1. Core Wedding Details & Narrative

- **Primary Setting:** Rome, Italy & Vatican City.

- **Ceremony Venue:** **The Chapel of the Choir (_Cappella del Coro_)** inside **St. Peter's Basilica**, Vatican City.
  - _Atmosphere:_ Intimate liturgy surrounded by gilded baroque vaulting, Bernini stuccoes, historic carved wooden choir stalls, sacred organ resonance, and frankincense.

- **Transition:** Procession past Bernini's Colonnade in St. Peter's Square and crossing the Tiber River (_Ponte Sant'Angelo_).

- **Reception Venue:** **Casina Valadier**, perched atop the **Pincian Hill (_Il Pincio_)** bordering Villa Borghese.
  - _Timing:_ Sunset through midnight.

  - _Atmosphere:_ Neoclassical architecture, panoramic views overlooking Rome (Piazza del Popolo, the dome of St. Peter's against the twilight sky), outdoor terrace cocktails, _Salone degli Specchi_ dinner, and late-night dancing beneath umbrella pine trees.

## 2. Design Vision & Philosophy

- **Not Just a Photo Grid:** Designed as a museum-grade archival retrospective, sensory documentary, and editorial chronicle rather than a generic photo gallery.

- **Tone & Aesthetic:** Understated luxury, academic/archival precision, and warm Mediterranean elegance.

- **Palette:**
  - **Travertine / Limestone:** `#FAF6F0` (light, warm stone background).

  - **Parchment / Bone:** `#F4ECE1` & `#E8DEC9` (tactile card and section surfaces).

  - **Charcoal Ink:** `#191614` (high-contrast, editorial typography).

  - **Roman Terracotta:** `#B65D43` (warm Italian clay accent).

  - **Basilica Antique Gold:** `#C5A059` (subtle gilding and highlights).

  - **Twilight Blue:** `#1D222E` (dusk sky contrast).

- **Typography:**
  - Primary Headings: **Cinzel** (classical Roman inscriptional serif).

  - Narrative & Body Serifs: **Cormorant Garamond** (literary, archival).

  - Interface, Badges & Labels: **Plus Jakarta Sans** and **Monospace** metadata stamps.

## 3. Current Project State & Asset Phasing

- **The Wedding Film (Primary Focal Point):**
  - **Status:** Finished and live.

  - **Placement:** The opening centerpiece of the site, placed immediately below the title masthead.

  - **Mechanism:** YouTube IFrame Player with **muted autoplay** (adheres to browser policies across Safari, Chrome, iOS, Android) paired with an intuitive one-tap unmute HUD and volume control.

  - **Default / Custom Video ID:** Set to a placeholder (`L_LUpnjgPso`). Users can replace the URL directly through the embedded modal UI or by changing `currentVideoId` in `index.html`.

- **Photography Archive:**
  - **Status:** In progress (analog 35mm film development and medium-format grading underway).

  - **Current Representation:** An editorial status note ("The Film is Live — The Complete Photo Archive is Forthcoming"), accompanied by a 3-plate preview gallery, candid flippable Polaroids, and sensory artifacts.

## 4. Key Sections & Interactive Features

1. **Header & Ambient Sacred Audio Bar:**
   - Persistent top navigation with mobile dropdown.

   - Native Web Audio API synthesizer generating a warm D-major church choir/organ chord drone (no external audio files required, zero latency).

2. **Hero & Cinematic Film Centerpiece:**
   - Full-width archival matte frame containing the YouTube embed.

   - Floating Roman HUD with soundbar equalizer, volume scrubber, fullscreen trigger, and an interactive "Paste Your YouTube Link" modal.

3. **Archive Status Dispatch:**
   - Editorial notification explaining the film-first rollout while still negatives are being developed.

4. **The Pincian Sunset Simulator (_Il Pincio al Tramonto_):**
   - Interactive 4-stage slider simulating the shift of light from Casina Valadier's terrace:
     - _Phase I (18:30):_ Golden Hour over travertine facades.

     - _Phase II (19:25):_ Sunset directly behind the dome of St. Peter's.

     - _Phase III (20:15):_ Blue Hour across Piazza del Popolo.

     - _Phase IV (21:30):_ Notte Romana beneath Villa Borghese pines.

5. **Sensory Ephemera & Convivium:**
   - **Fragrance Pyramid:** Bespoke breakdown of top (Roman orange blossom, green fig), heart (Vatican frankincense, night jasmine), and base notes (Villa Borghese stone pines, travertine).

   - **Banquet Menu:** Courses served at Casina Valadier paired with regional Italian wines (Franciacorta, Greco di Tufo, Barolo Riserva).

   - **Spoken Liturgy Audio Simulation:** Excerpt from the Book of Ruth with a mock scrubber and sacred resonance playback.

6. **Curated Photo Preview & Lightbox Modal:**
   - 3 archival plates featuring simulated Leica M11 and Hasselblad metadata tags.

   - High-resolution lightbox viewer with equipment specs and archive ID registry.

7. **Candid 35mm & Polaroids:**
   - Tilted, interactive snapshot cards that flip on click/tap to reveal handwritten memories from wedding guests.

8. **The Living Ledger (_Libro degli Ospiti_):**
   - Interactive digital guestbook allowing visitors to submit toasts and memories, immediately rendered to the live feed with simulated timestamping.

## 5. Technical Implementation Details

- **Single-File Architecture:** All markup, Tailwind utility styles, custom CSS animations, and vanilla JavaScript live inside a single standalone `index.html` file.

- **Zero Build Step:** Runs directly in any modern browser by double-clicking `index.html`.

- **External Dependencies (loaded via CDN):**
  - Tailwind CSS (`https://cdn.tailwindcss.com`)

  - Lucide Icons (`https://unpkg.com/lucide@latest`)

  - Google Fonts (`Cinzel`, `Cormorant Garamond`, `Plus Jakarta Sans`)

  - YouTube IFrame API (`https://www.youtube.com/iframe_api`)

## 6. Guidance for Future Edits & Enhancements

- **To Replace the Video ID permanently:**
  - Open `index.html`, locate `let currentVideoId = '...';` around line 540, and insert your 11-character YouTube video ID.

- **To Add Finished Full Galleries:**
  - Replace the preview grid section (`#gallery-preview`) with chapter-based image grids (e.g., _Chapter I: The Morning & Choir Liturgy_, _Chapter II: Tiber Passage_, _Chapter III: Terrace Aperitivo_, _Chapter IV: The Dinner & Ball_).

- **To Connect the Guestbook to a Backend:**
  - Currently, guestbook entries persist only in the client session. Connect `handleMemorySubmit()` to an endpoint (e.g., Supabase, Cloudflare Workers D1, or Firebase Firestore) for permanent, multi-user storage.
