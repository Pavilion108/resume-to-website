# 
PROJECT: E-MAGE LAB — Complete Build Brief v3.0
EMERGENT AI — FULL CONTEXT PROMPT


You are a senior creative technologist, award-winning 
frontend architect, and AI systems engineer. Your benchmark 
references are sites recognized on awwwards.com, lusion.co, 
bruno-simon.com, and peachworlds.com. Build everything to 
that standard.

GITHUB REPO: https://github.com/Pavilion108/Dev_Luncher.git
Clone it. Build everything below. Commit and push when done.

COMMIT MESSAGE:
"feat: E-Mage Lab v3 — 12 living 3D templates + 
 showcase + builder"

───────────────────────────────────────────────────────────────
MONOREPO STRUCTURE


/
├── apps/
│   ├── showcase/          → Website 1 — E-Mage Lab
│   └── builder/           → Website 2 — Dev Laboratory
├── packages/
│   ├── templates/         → 12 living HTML template engines
│   └── ui/                → Shared component library
├── pnpm-workspace.yaml
└── README.md

TECH STACK:
- Framework:     Next.js 14 App Router (both apps)
- Language:      TypeScript strict mode — zero any, 
                 zero suppressed errors
- Styling:       Tailwind CSS
- 3D / WebGL:    Three.js + React Three Fiber (@react-three/fiber)
                 + Drei (@react-three/drei)
- Animation:     GSAP 3 (ScrollTrigger, TextPlugin, DrawSVG)
                 + Framer Motion
- Scroll:        Lenis smooth scroll (lerp: 0.08)
- PDF Parse:     pdf-parse
- Code Editor:   Monaco Editor
- Fonts:         Playfair Display + Inter + Space Grotesk
                 (via next/font)
- Package Mgr:   pnpm workspaces


DEVELOPER-ONLY ADMIN ACCESS SYSTEM
(No external auth service — private env key method)


The builder tool (/apps/builder) is private. Only the 
developer (the controller) can access it. Implement this:

METHOD: Secret key URL guard — simple, zero dependencies,
        zero external services.

HOW IT WORKS:
1. In .env.local add:
   ADMIN_SECRET_KEY=emagelab_dev_2025_pavilion108

2. In /apps/builder/middleware.ts:
   - Intercept ALL routes under /builder
   - Check for cookie: emage_access=ADMIN_SECRET_KEY value
   - If cookie missing or wrong → redirect to /locked page

3. /locked page:
   - Clean dark page, E-Mage Lab logo centered
   - Single password input field (no label, no hint)
   - On submit: POST /api/auth
     - Compares input to process.env.ADMIN_SECRET_KEY
     - If match → set httpOnly cookie emage_access, 
       redirect to /upload
     - If wrong → shake animation, no error message 
       (just "..." — security by silence)

4. Cookie expires: 7 days (developer won't re-enter often)

5. Add a hidden keyboard shortcut in showcase site:
   Type "EMAGE" anywhere on the page (keysequence listener)
   → opens a small bottom-right toast:
     "Developer Portal →" with a link to builder URL
   This is invisible to normal visitors.

RESULT:
- Showcase site: 100% public, no auth
- Builder tool: completely private, 
  accessible only with the secret key
- No Vercel auth, no NextAuth, no database — 
  just an env variable you control forever


THE 12 LIVING PROFESSIONAL CLASSIC TEMPLATES
WITH 3D TOUCH


PHILOSOPHY OF THESE TEMPLATES:
These are not themes. They are worlds. Each one is a 
cinematic, living, breathing identity built for a specific 
type of professional. Classic in structure, bold in 
execution, alive in animation. Every template receives 
window.RESUME_DATA and renders a complete portfolio site.

UNIVERSAL RULES FOR ALL 12 TEMPLATES:
- Fully self-contained .html — zero server, zero framework
- All CSS + JS + animations inlined
- Reads from window.RESUME_DATA (schema below)
- Sticky nav: transparent → solid on scroll
- Smooth scroll (native CSS scroll-behavior: smooth)
- Mobile-first responsive: 640/768/1024/1280px
- prefers-reduced-motion: disable all motion
- will-change: transform on all animated elements
- Sections: Hero · About · Skills · Experience · 
            Projects · Contact
- 3D TOUCH RULE: Every template must have at minimum
  one Three.js or CSS 3D perspective interaction in the 
  hero section

RESUME_DATA SCHEMA:
{
  name:       string,
  role:       string,
  email:      string,
  phone:      string,
  location:   string,
  summary:    string,
  photo:      string,   // base64 or URL
  experience: [{
    company:   string,
    role:      string,
    startDate: string,
    endDate:   string,
    bullets:   string[]
  }],
  education: [{
    institution: string,
    degree:      string,
    year:        string
  }],
  skills:   string[],
  projects: [{
    name:        string,
    description: string,
    link:        string
  }],
  social: {
    linkedin:  string,
    github:    string,
    portfolio: string
  }
}



TEMPLATE 01 — "HIGHLAND" (template-highland.html)
Classic: Mountain executive portfolio



BACKGROUND:
https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=1920

DESIGN CONCEPT:
The grand executive. Full-viewport dramatic mountain 
landscape. Commanding presence. Dark overlay rgba(0,0,0,0.55). 
Circular profile photo centered. Name in bold white 
Playfair Display 72px. Role in large golden italic below. 
Minimal hamburger nav top-right. Golden square initials 
logo top-left.

3D TOUCH:
Three.js scene overlaid on the background image. 
5-8 floating 3D geometric crystals (IcosahedronGeometry, 
wireframe: true, gold #C8941A) drift slowly at different 
depths in the z-axis. Mouse movement creates subtle 
parallax — crystals move at different speeds based on 
their z-depth. Feels like floating in mountain air.

LIVING ANIMATIONS:
- Ken Burns: background zoom 1.0→1.06 + horizontal drift, 
  30s CSS loop
- Parallax: foreground pine silhouette SVG at 0.3× scroll, 
  peaks at 1× via CSS translateY
- Fog: SVG feTurbulence filter animated across mountains, 
  opacity 0.12, slow horizontal drift
- Profile: breathing pulse scale 1.0→1.02, 4s infinite
- Crystals: slow rotation on all axes, drift using 
  simplex noise offsets

PALETTE: #C8941A gold · #FFFFFF white · #1A1A1A charcoal
SKILLS: Animated fill progress bars, 0%→actual on scroll
EXPERIENCE: Vertical left-border timeline, gold dot markers
PROJECTS: 3-column card grid with hover lift shadow
CONTACT: Centered, social icon row



TEMPLATE 02 — "ECLIPSE" (template-eclipse.html)
Classic: Dark dramatic creative professional



BACKGROUND: Pure CSS + SVG — no image
Black full-screen. Two large SVG panther eye shapes 
built entirely in code. Pupils, irises, eyelids — all paths.

DESIGN:
Black hero. White centered name 68px bold. Gold rectangular 
hairline border frame around role subtitle. Below: clean 
white sections. Horizontal nav (Home · About · Services · 
Portfolio · Experience · Blog · Contact). Profile: name left, 
photo center, skill bars right. Portfolio grid with filter 
tabs. Experience: vertical year timeline right side.

3D TOUCH:
Three.js - camera looks into a deep dark void. Floating 3D 
text of the person's name rendered as a 3D extruded mesh 
(TextGeometry, depth: 8) slowly rotates in the void behind 
the eye SVGs. Gold material (#F5C400). Like seeing your 
identity carved in space.

LIVING ANIMATIONS:
- Eyes blink: SVG eyelid paths close→open, 8s cycle
- Pupils: dilation pulse scale, 6s ease-in-out
- Gold frame: shimmer scan sweep, 3s loop
- 3D name: slow Y-axis rotation, 20s loop
- Scroll: sections fade + slide up, IntersectionObserver

PALETTE: #000000 · #F5C400 gold · #FFFFFF · #F0F0F0



TEMPLATE 03 — "VELOCITY" (template-velocity.html)
Classic: Forward-moving bold achiever



BACKGROUND:
https://images.unsplash.com/photo-1448375240586-882707db888b?w=1920

DESIGN:
Full-screen dark forest road to vanishing point. Wordmark 
top-left (name + red dot). Nav top-right. Center: small 
italic subtitle, massive bold white display title (role, 
120px), two-line tagline, social icon row.

3D TOUCH:
Three.js - render a road that extends to infinity using 
PlaneGeometry with a repeating road texture (CSS-generated 
gradient stripes). Camera positioned at driver eye level. 
Road animates forward using texture offset — continuous 
drive illusion. Speed feels like momentum. Your career 
in motion.

LIVING ANIMATIONS:
- Forward drive: Three.js road texture scrolls forward, 
  20s loop
- Forest background: CSS scale 1.0→1.08 slow zoom
- Tree sway: ±1.5deg rotate, 6s infinite, sides offset 3s
- Scroll indicator: "SCROLL DOWN ↓" vertical text, 
  right edge, fade loop
- Light rays: diagonal overlay streaks, opacity pulse

PALETTE: #FFFFFF · #E8303A red · #1A1A1A



TEMPLATE 04 — "AURORA" (template-aurora.html)
Classic: Visionary creative technologist



DESIGN CONCEPT:
Deep midnight navy hero. Northern lights aurora effect 
built in pure CSS — flowing curtains of green/teal/purple 
light bands. Hexagonal profile photo frame with glowing 
teal border. White clean sans-serif typography.

3D TOUCH:
Three.js - above the aurora, render a sparse star field 
using Points geometry (2000 points, small white spheres). 
Camera slowly pans upward — infinite star drift. 
Mouse tilt makes stars shift ±15px on x/y axes. 
Gives depth to the night sky.

LIVING ANIMATIONS:
- Aurora bands: 5 div layers, blurred gradients 
  (green→teal→purple), each animates translateX and 
  opacity independently, 8–15s loops
- Stars: Three.js Points, slow upward drift + mouse parallax
- Hex frame: rotating glow border, 6s loop
- Entry: sections slide up + fade, IntersectionObserver

PALETTE: #0A0E27 midnight · #00FFB2 teal · 
         #7B2FFF purple · #FFFFFF

SKILLS: Hexagonal icon grid
EXPERIENCE: Horizontal scroll timeline with draggable track
PROJECTS: Masonry grid layout



TEMPLATE 05 — "OBSIDIAN" (template-obsidian.html)
Classic: Luxury editorial senior executive



DESIGN CONCEPT:
Premium all-black. Luxury brand meets tech portfolio. 
Full-bleed black. Thin gold #B8962E hairline borders. 
Name in massive condensed white type full viewport width. 
Role in spaced gold uppercase (letter-spacing: 0.4em). 
Typography-first: maximum impact, minimum elements.

3D TOUCH:
Three.js - render a slowly rotating 3D obsidian sphere 
(SphereGeometry, MeshStandardMaterial, color: #1C1C1C, 
roughness: 0.1, metalness: 0.9) in the background-right 
of hero. Subtle environment map reflection. One directional 
gold light source. Like a black mirror reflecting ambition.

LIVING ANIMATIONS:
- Hero text: each letter animates in individually, 
  stagger 0.05s, slide up + fade (GSAP TextPlugin)
- Gold hairlines: draw left→right on section entry, 
  CSS width 0→100% transition
- Profile: slow vertical reveal via clip-path animation
- Obsidian sphere: continuous slow rotation, Y-axis
- Custom cursor: gold dot that scales 3× on hover

PALETTE: #000000 · #B8962E antique gold · 
         #FFFFFF · #1C1C1C surface

SECTIONS: Full-viewport hero · Numbered index/TOC 
          (magazine style) · About · Skills (text list 
          with percentages) · Selected Work · Contact



TEMPLATE 06 — "REVERIE" (template-reverie.html)
Classic: Creative designer / UX portfolio



DESIGN CONCEPT:
Inspired by Bruno Simon and Lusion's immersive approach. 
Soft pastel gradient background (lavender→rose→peach) that 
subtly shifts hue over time. Clean white card layout below 
hero. Dreamy, soft, deeply professional. For designers, UX 
researchers, and creative directors.

HERO:
Centered. Name in bold 80px. Role in 24px italic below. 
Background: CSS animated gradient mesh, slow hue rotation.

3D TOUCH:
React Three Fiber scene (rendered as a standalone Three.js 
script for the self-contained HTML). Floating 3D abstract 
shapes — mix of TorusGeometry, DodecahedronGeometry, and 
ConeGeometry. Pastel colors matching hero palette. Shapes 
float using sin/cos noise functions. Mouse hover causes 
nearest shape to gently dodge away (repulsion physics). 
Feels like reaching into a dream.

LIVING ANIMATIONS:
- Gradient mesh: CSS hue-rotate keyframe, 20s loop
- 3D shapes: float + mouse repulsion physics
- Nav: appears with frosted glass blur on scroll
  (backdrop-filter: blur(12px))
- Cards: hover causes subtle 3D tilt 
  (CSS perspective + rotateX/Y on mousemove)
- Skills: circular progress rings animated on scroll entry

PALETTE: #E8DCFF lavender · #FFD6E0 rose · 
         #FFF0DC peach · #2D2D2D dark text



TEMPLATE 07 — "MERIDIAN" (template-meridian.html)
Classic: Corporate finance / consulting / banking



DESIGN CONCEPT:
Premium corporate. Deep navy (#0A1628) + crisp white + 
gold accents. Glass morphism cards (frosted glass panels 
over a subtle grid background). Clean structured layout. 
This is the template for investment bankers, consultants, 
finance professionals, and C-suite executives.

HERO:
Left-aligned. Name 64px bold white. Role 24px gold. 
Summary text below. CTA buttons side by side. Right side: 
3D element (see below). Background: subtle animated 
grid/dot pattern.

3D TOUCH:
Three.js — render a professional 3D bar chart of the 
person's career progression. Bars rise from 0 to their 
heights on page load with an easing animation. 
X-axis: career years. Y-axis: abstract "impact level". 
Gold (#C8941A) bars with glass material. Rotates slowly 
on Y-axis. Hovering a bar shows a tooltip with the 
company name from experience data. 
Data, made visual. Power, made tangible.

LIVING ANIMATIONS:
- Career bars: animate upward on load with stagger + 
  bounce easing
- Glass cards: subtle shimmer on hover 
  (CSS pseudo-element sweep)
- Grid background: slow pan in one direction, infinite
- Skill bars: fill left→right on scroll, gold gradient
- Section transitions: fade + slide right (not up — 
  horizontal movement feels corporate, decisive)

PALETTE: #0A1628 navy · #C8941A gold · 
         #FFFFFF white · rgba(255,255,255,0.08) glass



TEMPLATE 08 — "PHANTOM" (template-phantom.html)
Classic: Tech / developer / blockchain / web3



DESIGN CONCEPT:
Dark web3/crypto/developer aesthetic. Pure black background. 
Matrix-style green (#00FF41) code rain in background. 
Clean monospace typography (Space Mono). Terminal-inspired 
sections. For senior engineers, blockchain developers, 
security researchers, and full-stack builders.

HERO:
Full-viewport. Code rain behind content.
Name appears with a typing cursor animation — types out 
character by character. Role appears second, same effect. 
Green text on black. Clean, raw, powerful.

3D TOUCH:
Three.js — render a wireframe globe (SphereGeometry, 
wireframe: true, green #00FF41) slowly rotating in the 
hero background-right. Latitude/longitude lines only. 
Looks like a tech radar scanning the world. 
Small glowing dots pulse at random coordinates — 
represents global reach, distributed systems, 
the nature of the web.

LIVING ANIMATIONS:
- Code rain: canvas-based matrix rain, column speed varied
- Globe: continuous Y-axis rotation, 25s loop
- Globe dots: pulse scale 1→2, opacity fade, random timing
- Name typing: character by character, cursor blinks after
- Skill tags: appear as floating terminal command badges
  (like: `--typescript` `--react` `--python`)
- Experience: styled as git commit log 
  (hash · date · company · role)

PALETTE: #000000 · #00FF41 matrix green · 
         #FFFFFF · #1A1A1A surface



TEMPLATE 09 — "SOLSTICE" (template-solstice.html)
Classic: Marketing / brand strategy / creative director



DESIGN CONCEPT:
Warm desert golden hour. Full-viewport sand dune landscape 
at sunset. Deep amber and terracotta tones. Warm, inviting, 
bold. For marketers, brand strategists, CMOs, creative 
directors, and business development professionals.

BACKGROUND:
https://images.unsplash.com/photo-1509316785289-025f5b846b35?w=1920
(desert dunes golden hour)

HERO:
Centered. Dark terracotta overlay rgba(40,20,10,0.6). 
Name in bold white Playfair Display 80px. Role in warm 
amber italic. Circular photo with terracotta glow border.

3D TOUCH:
Three.js — render slow-moving sand particle system. 
Thousands of tiny amber/gold particles (BufferGeometry, 
PointsMaterial) drift from right to left like desert wind. 
Particle speeds vary — some fast gusts, some slow drifts. 
On mouse movement, particles near the cursor scatter away 
then float back. Feels like standing in warm desert wind.

LIVING ANIMATIONS:
- Sand particles: wind drift, mouse scatter + return
- Background: subtle warm color grade pulse 
  (hue shifts slightly warmer → cooler, 8s loop)
- Photo border: slow glow pulse, terracotta→amber
- Sections: warm fade in (no slide — warmth is still)
- Skills: circular arc progress (like sun position)

PALETTE: #FF6B35 terracotta · #FFB347 amber · 
         #FFFFFF · #1A0A00 deep brown



TEMPLATE 10 — "NEXUS" (template-nexus.html)
Classic: Data scientist / AI engineer / researcher



DESIGN CONCEPT:
Neural network visualization as the living background. 
Dark surface (#0D0D0D) with animated nodes and connection 
lines — looks like a neural network or knowledge graph. 
Blue/cyan accent (#00BFFF). Clean data-forward layout. 
For data scientists, ML engineers, researchers, and 
product managers in tech.

HERO:
Left-aligned. Name 64px bold white. Role in cyan. 
Right side: neural network animation (see below). 
Background: subtle dark grid.

3D TOUCH:
Three.js — render a full 3D neural network. 
20-30 sphere nodes (SphereGeometry radius 0.15) connected 
by LineSegments. Nodes float at different z-depths. 
Connections draw and undraw as if data flows between them 
(animated opacity pulses travel along edges like signals). 
Camera slowly orbits the network. Mouse hover: camera 
tilts toward cursor. Feels like looking inside an AI mind.

LIVING ANIMATIONS:
- Neural network: nodes pulse, edge signals travel, 
  camera orbit
- Skills section: displayed as a 2D force-directed graph 
  (D3.js bubbles, skill as node, size = proficiency level)
- Experience: data cards with stat numbers that count up 
  on scroll entry
- Projects: hover reveals a code snippet overlay 
  (3 lines of relevant code, monospace, cyan)

PALETTE: #0D0D0D · #00BFFF cyan · 
         #FFFFFF · #1A2A3A dark blue surface



TEMPLATE 11 — "MONARCH" (template-monarch.html)
Classic: Luxury / fashion / arts / high-end brand



DESIGN CONCEPT:
Inspired by Bottega Veneta, Loro Piana editorial sites. 
Monochrome black and white photography aesthetic. 
Full-bleed black. Serif typography at scale. 
Gold (#B8962E) used sparingly as a crown element. 
For fashion professionals, luxury brand managers, 
art directors, gallery curators, and creative executives.

HERO:
Black full-viewport. Profile photo takes full right half 
of screen in grayscale (CSS filter: grayscale(1)). 
Left half: large editorial text. Name in 96px condensed 
serif (Playfair Display Condensed). Role in gold spaced 
caps. Single underline separator in gold.

3D TOUCH:
Three.js — single large 3D gold crown geometry floating 
in the top-left corner background. Built from custom 
BufferGeometry points defining a crown silhouette extruded 
in 3D. Gold MeshStandardMaterial, high metalness: 0.95, 
roughness: 0.05. Rotates very slowly — one full rotation 
per 60s. Catches a single spotlight. Regal. Absolute.

LIVING ANIMATIONS:
- Photo: appears with slow vertical desaturate reveal 
  (starts color, transitions to grayscale on load)
- Crown: rotate on Y-axis, spotlight flicker subtle
- Gold underlines: draw left→right on section entry
- Projects: full-bleed image cards, hover reveals 
  case study text overlay with slide up
- Typography: each section heading reveals with 
  mask-clip animation (text reveals left→right)

PALETTE: #000000 · #B8962E gold · 
         #FFFFFF · #1C1C1C soft black



TEMPLATE 12 — "ZENITH" (template-zenith.html)
Classic: Minimal Japanese / architecture / engineering



DESIGN CONCEPT:
Inspired by Japanese aesthetic: ma (negative space), 
wabi-sabi (imperfect beauty), shibui (quiet luxury). 
White background (#FAFAF8 warm white). 
Ink brush SVG animations. Sparse. Every element earns 
its place. For architects, structural engineers, 
product designers, and anyone whose work speaks through 
precision. The quietest template. The most powerful.

HERO:
Pure white. Name in 80px thin weight Playfair Display — 
almost light. Role in 14px tracked gray uppercase. 
A single ink brush stroke SVG animates across the full 
width below the name on load (SVG path stroke-dashoffset 
animation). Slow. Deliberate. Unforgettable.

3D TOUCH:
Three.js — single perfect white sphere (SphereGeometry, 
MeshPhongMaterial, white, shininess: 200) centered in 
the far background. It casts a soft shadow on a 
PlaneGeometry floor. Camera is static. The sphere breathes 
(scale 1.0→1.02, 6s sine loop). A single directional light 
moves in a 30s arc — like a sun crossing overhead. The 
shadow moves with it. Still. Perfect. Alive.

LIVING ANIMATIONS:
- Ink brush: SVG path stroke reveal on load, 2.5s ease
- Sphere: breathe + moving sun shadow
- Sections: appear with a single horizontal ink line 
  drawing from left before content fades in
- Skills: minimal numbered list, each number counts up
- Experience: clean table layout, no borders except 
  bottom hairline gold on each row
- Scroll: Lenis smooth scroll feels like turning 
  pages in a handbound book

PALETTE: #FAFAF8 warm white · #1A1A1A near-black · 
         #C8941A gold (used once, hero accent only) · 
         #888880 warm gray


WEBSITE 1 — E-MAGE LAB SHOWCASE
/apps/showcase
REFERENCE: https://www.igloo.inc/


FUNCTIONAL DESIGN PHILOSOPHY:
This site IS igloo.inc — but for living portfolios. 
Full-screen cinematic sections. Heavy type. Confident 
sparse copy. Every scroll moment is earned. Endless 
scroll — sections flow into each other seamlessly. 
Lenis smooth scroll (lerp: 0.075) on the entire page. 
GSAP ScrollTrigger drives all section animations. 
NO PAGINATION. NO SECTIONS THAT FEEL SEPARATE. 
One unbroken cinematic journey from top to bottom.

────────────────────────────────────────────────────────
SECTION 1 — HERO (Full Viewport, 100vh)
────────────────────────────────────────────────────────

BACKGROUND:
Three.js WebGL scene, dynamically imported.
Dark atmospheric layered mountain scene with slow camera 
drift on X and Y axes (±0.3 units, 15s sine loop). 
Mouse-tracked 3D tilt: entire scene rotates ±3deg 
following cursor (lerped, smooth). Three.js Points — 
gold dust particles (#C8941A, size: 0.8, opacity: 0.25) 
drifting upward slowly.

HEADLINE (Playfair Display bold, 88px desktop / 48px mobile, 
          white, centered):

"Your Resume Deserves
 To Live."

SUBHEADLINE (Playfair Display italic, 26px, gold #C8941A,
             centered, line-height: 1.4):

"A website that breathes, moves, and speaks your story —
 crafted for professionals who refuse to be forgotten."

BODY (Inter light, 17px, #B8B8B8, centered, 
      max-width: 560px):

"The static resume had its era. That era ended.
 Every pixel of your new portfolio moves with intention.
 Recruiters don't read anymore — they feel.
 Give them something to feel."

CTA BUTTONS (centered, gap: 16px):
[ See The Templates ↓ ] 
  — outlined, white border 1px, hover: fills white, 
    text turns dark, smooth-scrolls to Section 3

[ Build Your Site → ]   
  — filled amber gradient #C8941A→#E8A020, 
    text white, hover: brightness 1.1 + scale 1.02
    onClick: mailto:Home.pavilion1975@gmail.com
    ?subject=E-Mage Lab — I Want My Site
    &body=Hi, I found E-Mage Lab and I'm interested 
    in getting my portfolio built. My name is [name] 
    and I'm a [role].

SCROLL INDICATOR:
Animated chevron down, bounce loop 2s, 
opacity fade in after 3s delay.

────────────────────────────────────────────────────────
SECTION 2 — THE MANIFESTO
(Full Viewport, dark #080808)
────────────────────────────────────────────────────────

GSAP ScrollTrigger: section pins for 150vh of scroll. 
Text reveals line by line as user scrolls (not on load).
Each line slides up and fades in sequentially with 
ScrollTrigger scrub: 1.

LARGE MANIFESTO TEXT (centered, Playfair Display):

Line 1 (56px bold white):
"The world moved on."

Line 2 (56px bold white, 0.8s after line 1):
"Your resume didn't."

Line 3 (56px bold gold #C8941A, italic, 1.6s after):
"We fix that."

PAUSE. Then the body text fades in below (Inter 19px, 
#C0C0C0, max-width: 640px, line-height: 1.8, centered):

"There is a new currency in the professional world —
 and it is not your GPA, your certifications, 
 or the bullet points on a white A4 page.

 It is presence. Digital, visual, felt in seconds.

 The ones rising fastest are not necessarily the most 
 qualified. They are the most visible. The most alive 
 in the feed, the inbox, the recruiter's browser tab.

 E-Mage Lab was built for the professionals who understand 
 this shift — and refuse to show up looking like 1998."

BELOW BODY — Three rotating PULL QUOTES on a timer 
(swap every 5s with crossfade):

Quote 1 (gold italic, 28px Playfair Display):
"In the age of AI, the ones who stand out
 are the ones who look alive."

Quote 2:
"Your career is a story worth telling well.
 A PDF is not good enough for that story anymore."

Quote 3:
"First impressions don't wait. Neither should your 
 portfolio."

────────────────────────────────────────────────────────
SECTION 3 — TEMPLATE SHOWCASE
(Endless scroll within the section — not paginated)
────────────────────────────────────────────────────────

SECTION HEADING (56px Playfair Display, centered, white):
"Choose Your World."

SUBTITLE (Inter 18px, #A0A0A0, centered):
"Twelve professional identities. 
 Classic in craft. Alive in every pixel."

INSPIRATIONAL LINE BELOW SUBTITLE 
(Inter 15px, italic, gold, centered):
"Not just a website — a declaration of who you are."

LAYOUT:
Horizontal scroll track inside this section.
The 12 template cards are laid out horizontally.
On desktop: user scrolls RIGHT through the cards 
(GSAP ScrollTrigger horizontal scroll, pinned section).
On mobile: standard vertical scroll.

Each card is the SIZE of a browser viewport (90vw × 70vh).
There are 12 cards + 3 "Coming Soon" = 15 total.

EACH TEMPLATE CARD:

Outer card:
- Mac-style browser chrome (traffic light dots, URL bar 
  showing template name: "emagelab.io/highland")
- Dark card surface #111111
- Border: 1px solid rgba(200,148,26,0.2)
- Hover: border becomes rgba(200,148,26,0.8), 
  card lifts with transform translateY(-8px) + 
  box-shadow 0 24px 48px rgba(200,148,26,0.15)

Inner iframe:
- Loads actual template HTML file with placeholder data:
  { name: "Your Name", role: "Your Role", 
    email: "you@email.com", 
    skills: ["Your Skills", "Leadership", "Strategy"],
    summary: "Your story lives here.",
    experience: [{ company: "Your Company", 
                   role: "Your Role", 
                   startDate: "2020", endDate: "Present",
                   bullets: ["Your achievements go here"] }]
  }
- iframe is ALIVE — animations play inside it
- CSS: transform scale(0.45) inside a fixed-size wrapper
  so it renders full-size internally but appears 
  as a living miniature
- Lazy load: IntersectionObserver, only load iframe 
  src when card enters viewport
- iframe brightness: 0.85 default, 1.0 on card hover

Card bottom strip:
- Left: Template number + name badge 
  ("01 · HIGHLAND", gold text)
- Right: Two buttons:
  [ Preview ↗ ] — opens template in fullscreen modal
  [ Choose This → ] — mailto link with template name 
    in subject line

FULLSCREEN MODAL:
- Dark overlay rgba(0,0,0,0.95)
- iframe fills 95vw × 95vh, unscaled (100% size)
- Template fully alive at full resolution
- Close button top-right "✕"
- Template name badge top-left
- "Order This Template →" button bottom-center
  (mailto link)
- ESC key closes modal

GHOST COPY BETWEEN TEMPLATE CARDS:
Between every 3-4 cards, inject a full-width dark 
inspiration panel (same width as a card):

Panel 1 (after card 3):
Gold italic quote, 36px Playfair Display:
"One template. Your truth.
 The rest is just noise."

Panel 2 (after card 6):
"Most portfolios whisper.
 These ones speak.
 Some of them shout."

Panel 3 (after card 9):
"The designer who built your competitor's site 
 used the same resume format as you.
 Not anymore."

Panel 4 (after card 12):
"New worlds are loading.
 The best is always next."

COMING SOON CARDS (3 cards after the 12):

Card 13: "THE ARCHITECT"
Blurred preview (blur: 12px). Lock icon. Gold badge.
Tagline: "For those who build empires, not just careers."

Card 14: "THE PHANTOM"
Blurred. Lock icon.
Tagline: "Seen by few. Remembered by all."

Card 15: "THE ASCENDANT"
Blurred. Lock icon.
Tagline: "Your next chapter. Currently rendering."

────────────────────────────────────────────────────────
SECTION 4 — HOW IT WORKS
────────────────────────────────────────────────────────

HEADING: "Three Steps. One Masterpiece."

GSAP ScrollTrigger: each step stagger-reveals 
as user scrolls through this section.

3 steps horizontal on desktop, vertical on mobile.
Animated connector line draws between them.

STEP 1 — Document icon, animated fill on scroll:
"Upload your resume PDF"
Body (14px gray):
"Drop it in. Claude reads every word, every role, 
 every achievement you've earned over the years. 
 Nothing gets left behind."

STEP 2 — Palette icon:
"Choose your living theme"
Body:
"Twelve worlds. Twelve identities. 
 Pick the one that speaks who you are 
 before you say a word."

STEP 3 — Lightning bolt icon:
"Receive your HTML site"
Body:
"A complete, animated, self-contained portfolio file. 
 Host it anywhere. Own it forever. 
 No subscriptions. No monthly fees. Yours."

CTA BELOW (centered):
[ I Want My Portfolio → ]
onclick: mailto:Home.pavilion1975@gmail.com
?subject=E-Mage Lab — Build My Portfolio
&body=Hello, I'd like to get my portfolio built.
Styling: large button, gold gradient, Playfair Display 18px

────────────────────────────────────────────────────────
SECTION 5 — THE PHILOSOPHY WALL
(Full Viewport, white background #FAFAF8)
────────────────────────────────────────────────────────

This section is a typography-only editorial statement. 
No images. No cards. Just words at scale. 
Like an open letter from E-Mage Lab.

Left column (Playfair Display italic, 48px, dark, 
             60% width):
"We believe a career this real
 deserves a portfolio this alive."

Right column (Inter 16px, #606060, 40% width, 
              line-height: 1.9):
"Every professional we have ever spoken to has felt it — 
 that moment when you send your resume and wonder 
 if anyone will truly see you in it.

 The truth is: they probably won't.

 Not because you aren't impressive — but because 
 a static document was never built to carry the weight 
 of everything you have done, learned, and become.

 E-Mage Lab was built for that weight.
 For the analyst who stayed late to get it right.
 For the engineer who rebuilt the system no one else 
 thought could be fixed.
 For the strategist who saw what others missed.
 For every professional whose work deserves 
 more than a PDF and a prayer.

 You built something real.
 We build the website that proves it."

BOTTOM (full-width, centered, dark background strip):
Gold italic 32px Playfair Display:
"Your resume is a document.
 Your portfolio is a legacy.
 We build legacies."

────────────────────────────────────────────────────────
SECTION 6 — FOOTER
────────────────────────────────────────────────────────

Background: #060606

LEFT:
E-Mage Lab wordmark (gold + white)
"Built for the ones who dare to stand out."
Sub: "A Dev Launcher Product"

CENTER:
Themes · How It Works · Contact

RIGHT:
"Connect with us"
→ Email: Home.pavilion1975@gmail.com
→ GitHub: github.com/Pavilion108
→ LinkedIn: [TODO — add link]

BOTTOM BAR:
"© 2025 E-Mage Lab · Dev Launcher
 Crafted with intent. Deployed with purpose.
 Every pixel earns its place."

HIDDEN DEVELOPER ACCESS:
Add a keysequence listener on the showcase site.
If user types "EMAGE" anywhere on the page:
→ Small toast appears bottom-right:
  "Developer Mode ↗" with link to builder URL
  (disappears after 8s or on click)
  This is completely invisible to regular visitors.


WEBSITE 2 — DEV LABORATORY (BUILDER TOOL)
/apps/builder
REFERENCE: https://www.hatom.com/


PROTECTED BY: middleware.ts secret key guard
(see Developer-Only Access System section above)

DESIGN PHILOSOPHY:
Like hatom.com — surgical, fast, no bloat. 
The developer is the only user. The interface serves 
the work, not itself. Every screen has one job. 
Dark theme throughout (developer aesthetic). 
No decorative elements. Maximum information density.

ROUTES:
/ → redirect to /upload
/upload → Step 1: Upload PDF
/select → Step 2: Choose template  
/editor → Step 3: Live edit + Claude chat
/preview → Full-screen site preview
/locked → Secret access entry

────────────────────────
/locked PAGE
────────────────────────

Dark center layout:
E-Mage Lab logo (gold, 32px)
Single password input, no label, no placeholder hint
Submit button: "→"
On wrong: input shakes (GSAP shake), nothing else
On correct: cookie set, redirect to /upload

────────────────────────
STEP 1 — /upload
────────────────────────

Clean centered card layout.
Nothing else on this page.

ELEMENTS:
- Drag-drop zone: dashed border with rotating gradient 
  animation (CSS conic-gradient rotation, 3s loop)
  Inner text: "Drop your resume PDF here"
  Sub: ".pdf only · max 5MB"

- API Key panel (collapsible, top-right corner):
  Label: "Anthropic API Key"
  Input: password type, placeholder "sk-ant-..."
  Stored in sessionStorage, never logged server-side
  Info: "Your key · Your requests · Your control"

ON UPLOAD:
POST /api/parse-resume
→ pdf-parse extracts text
→ Claude API parses to resumeData JSON
→ Store in sessionStorage as "emage_resume"
→ Show confirmation:

"Welcome, [name]."
"[X] years of experience · [Y] skills · [Z] projects"
"Ready to build something exceptional?"
[ Continue → ]

LOADING STATES:
"Reading your resume..."
→ "Parsing with Claude..."
→ "Structuring your data..."
→ "Done."

────────────────────────
STEP 2 — /select
────────────────────────

HEADING: "Pick Your World, [name]."
SUB: "This is your data. Inside a living site."

All 12 template cards shown in a 3-column responsive grid.
Each iframe loads with USER'S ACTUAL resumeData.
Real name, real role, real content, live inside animations.

This is the magic moment. 
Add a 0.8s staggered fade-in reveal for each card 
on page load so cards appear one by one — builds 
anticipation before the user sees their data alive.

[ Select This Theme ] → sessionStorage saves templateName 
→ navigate to /editor

────────────────────────
STEP 3 — /editor
────────────────────────

SPLIT-PANE:

LEFT (40%): Claude Chat

Top bar:
- Active template badge (gold)
- API key status: green dot "Key Active" or 
  red dot "Using Default Key"

Chat area (scrollable):
- User messages: right, white bubble
- Claude: left, dark #1A1A1A bubble
- HTML responses auto-refresh right pane
- Thinking indicator: "..." with pulse

Quick prompts row (chips, horizontal scroll):
"Bigger name" · "Purple theme" · "Bolder tagline" · 
"Add certifications" · "More aggressive tone" · 
"Add GitHub projects" · "Minimal layout" · 
"Dark mode version"

Text input: "Ask Claude to change anything..."
Send: Enter or → button

RIGHT (60%): Live Preview

Toolbar:
[ Full Screen ] [ Download HTML ] [ Edit Code ]

iframe: current generated HTML, full height
Monaco Editor (hidden by default, toggles on Edit Code):
- Shows current HTML
- Changes apply to iframe on Ctrl+S

────────────────────────
EDITOR — EXTRA FEATURES
────────────────────────

Profile photo upload:
- JPG/PNG max 2MB → base64 → inject into template
- Preview updates instantly

Section toggles panel (right sidebar):
☑ Projects
☑ Certifications
☐ Languages
☐ Hobbies
Toggling sends auto-Claude prompt to add/remove section

Bottom toolbar:
Template switcher · Reset to last AI · 
Copy HTML · Download .html
API ROUTES
POST /api/auth
Input: { password }
- Compare to process.env.ADMIN_SECRET_KEY
- If match: set cookie emage_access, return { ok: true }
- If wrong: return 401, no message

POST /api/parse-resume
Input: multipart PDF
- pdf-parse → raw text
- Claude API parse → resumeData JSON
- Return: { resumeData }

POST /api/generate-site
Input: { resumeData, templateName, userMessage, 
         currentHtml, apiKey }

GENERATION (no currentHtml):
SYSTEM:
"You are an expert frontend developer building a 
personalized living portfolio website. You will receive 
a resume data JSON and a complete HTML template. 
Populate every single piece of content from the resume 
data — name, role, summary, every job, every bullet, 
every skill, every project, all contact info. 
Keep every single animation, CSS rule, and JavaScript 
function completely intact. Only change text content 
and image src values. Return ONLY the complete HTML 
file with no explanation, no markdown, no code blocks."

EDIT (currentHtml provided):
SYSTEM:
"You are editing an existing HTML portfolio page. 
The user wants this change: [userMessage]. 
Make only that specific change. Keep everything else 
exactly as it is. Return the complete updated HTML 
file only — no explanation, no code blocks, nothing else."

- Anthropic streaming API (fast perceived performance)
- Route through apiKey from request if provided
- Fallback to ANTHROPIC_API_KEY env variable
- Timeout: 30s hard limit

KEY ROTATION LOGIC:
Try ANTHROPIC_API_KEY.
If fail or timeout after 20s → try ANTHROPIC_API_KEY_BACKUP.
If both fail → return to UI:
{
  error: "HAMMER_ON_FIRE",
  message: "My Hammer Is on Fire 🔥 Cooling it Down — 
            Do 10 Push-Ups While I Catch My Temp 💪
            Try again in 30 seconds."
}


ENVIRONMENT VARIABLES


Both apps — .env.local:
ANTHROPIC_API_KEY=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
ANTHROPIC_API_KEY_BACKUP=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

Builder only:
ADMIN_SECRET_KEY=emagelab_dev_2025_pavilion108

Create .env.example with all keys as empty placeholders.
Add .env.local to .gitignore.

VERCEL CONFIG (both apps)
vercel.json:
{
  "buildCommand": "pnpm build",
  "outputDirectory": ".next",
  "framework": "nextjs"
}

Showcase → root directory: apps/showcase
Builder  → root directory: apps/builder
QUALITY STANDARDS — NON-NEGOTIABLE
Performance:
- Lighthouse >85 mobile (showcase)
- Three.js: dynamic import only (prevent SSR crash)
- Lazy load ALL template iframes
- Images: next/image with proper sizes + alt text
- Fonts: next/font (Playfair Display + Inter + Space Grotesk)

Animation:
- will-change: transform on ALL animated elements
- prefers-reduced-motion: static fallback for everything
- Lenis smooth scroll: lerp 0.075, entire showcase page
- GSAP ScrollTrigger: powers all section reveals

Code quality:
- TypeScript strict: zero any, zero suppressions
- Zero console errors/warnings in production
- All API routes: proper error handling + HTTP codes
- All async operations: loading states

Templates:
- Must work opened directly in browser, zero server
- All assets inlined (CSS, JS, fonts as base64)
- Mobile-first: 640/768/1024/1280px

Contact:
- Zero Dodo Payments integration
- ALL purchase CTAs → mailto:Home.pavilion1975@gmail.com
  with pre-filled subject + body per context
BUILD ORDER
1. Clone repo + set up pnpm monorepo structure
2. Build all 12 living HTML templates (foundation)
   — test each one standalone in browser before moving on
3. Build showcase /apps/showcase
4. Build builder /apps/builder  
   — implement auth middleware first
5. vercel.json in both apps
6. Root README.md with full setup + deployment guide
7. git add . && git commit -m 
   "feat: E-Mage Lab v3 — 12 living 3D templates + 
    showcase + builder + developer auth"
8. git push origin main
