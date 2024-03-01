# Tips & Tricks
This is more of my own subjective notes rather than actual docs for the pack; none of this is quote-unquote officially supported!

## [Colorful Hearts](https://modrinth.com/mod/colorful-hearts)
Useful for when you have a high max health(e.g. Artifacts hearts thing, Botania Ring of Odin). Kinda breaks with AppleSkin though

## [Presence Footsteps](https://modrinth.com/mod/presence-footsteps) & [Sound Physics Remastered](https://modrinth.com/mod/sound-physics-remastered)
Nicer soundscapes. nuff said.

## [Caxton](https://modrinth.com/mod/caxton)
Actual TTF font support with kerning and all that. If using with a dark mode UI pack, try [Caxtonized Dark Mode](https://modrinth.com/resourcepack/caxtonized-dark-mode)!

## [Distant Horizons](https://modrinth.com/mod/distanthorizons)
Very, very big render distances with less FPS impact using level-of-detail rendering. Spotty with shaders!

## Violence
psst, kid, want some shaders? I have just the thing for you.  
A complete replacement of the default rendering mods to bring shaders that work with Flywheel, Caxton and Distant Horizons(partially, depends on shaders). Is pretty experimental and has a significant performance impact(Sodium is just that good), so beware!

### Caveats
- This is still laggier than pure Sodium.
- Shader shading isn't applied to Flywheel, so they look vanilla.
- Some models from Create might be slightly broken.
- Nixie Tubes from Create looks outright awful, though I'm not sure if this is a Caxton thing.

### Steps
1. Disable or remove: CIT Resewn, Dynamic FPS, Flywheel(this is just a patched version for sodium. removal will fall back to Create's default, which is fine), Indium, Iris, Reese's Sodium Options, Sodium and Sodium Extra.
1. Add [Canvas](https://modrinth.com/mod/canvas) and [Violence](https://github.com/vgskye/violence). (for Violence, prebuilt artifacts are available under Actions!)
1. Add a Canvas pipeline shader(for the ones I tried, see below!)
1. Enjoy!

### Canvas Shaders I tried
- [Lumi Lights](https://spiralhalo.github.io/): Doesn't render Distant Horizons terrain, seems fine otherwise.
- [Forget-Me-Not](https://modrinth.com/shader/forgetmenot): Doesn't render Distant Horizons terrain, is buggy with Flywheel-rendered things. Not recommended for this environment.
- [ecos](https://modrinth.com/shader/ecos): Renders Distant Horizons terrain, though fogs are broken with it. See below for a "fix".

#### ecos fix with Distant Horizons
Distant Horizons renders its own fog on its terrain and expects the vanilla terrain to be rendered fog-free, which results in jarring transitions with ecos as its fog isn't disabled by DH. Simply comment out or remove lines 280-286 in `assets/ecos/shaders/gbuffer/main.frag` to remove ecos fog entirely. Water transitions are similarly jarring unless you disable ecos's fancy water setting.