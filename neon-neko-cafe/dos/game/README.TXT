NEON NEKO CAFE  -  MS-DOS EDITION
=================================

A cyberpunk cat girl cafe idle clicker for MS-DOS.
VGA, EGA, CGA, Tandy/PCjr or Hercules graphics; Roland MT-32, General
MIDI, Sound Blaster (1.x/2.0/Pro/16), AdLib, Gravis Ultrasound, Tandy
3-voice, Disney Sound Source or PC speaker - with Kiko's digitized
"Nyaa~!" even on the PC speaker. Mouse and keyboard.

FILES
  SETUP.EXE     choose video mode and sound card (run this first)
  NEKO.EXE      the game (32-bit protected mode, DOS/32A extender built in)
  NEKO.DAT      art, palette and fonts
  DOS32A.TXT    license of the DOS extender built into NEKO.EXE and SETUP.EXE
  DOSBOX.CONF   ready-made DOSBox settings (SVGA machine, all modes work)
  DOSBOX_EGA.CONF, DOSBOX_CGA.CONF, DOSBOX_HERC.CONF, DOSBOX_TANDY.CONF
                emulate a real EGA, CGA, Hercules or Tandy 1000 instead

RUNNING IN DOSBOX
  Put this folder somewhere, open a terminal in it and run:
      dosbox -conf DOSBOX.CONF
  DOSBox drops you at the C:\> prompt. Type SETUP to pick your video
  mode and sound cards, then NEKO to play. Nothing starts automatically.
  Or start DOSBox yourself and type:
      mount c C:\path\to\NEKOCAFE
      c:
      NEKO
  DOSBox, DOSBox-X and DOSBox Staging all work. Use cycles=max.

SETUP
  Run SETUP before playing (or any time you change hardware). It works with
  the keyboard or the mouse (the pointer only takes over the highlight
  when you actually move it). On first run it auto-detects your hardware.
    - Select Video Mode: VGA, EGA, CGA, Tandy/PCjr or Hercules
    - Select Music Device and Select Sound Effects Device, separately:
        Sound Blaster 16, Sound Blaster Pro, Sound Blaster 2.0,
        Sound Blaster 1.x, AdLib, Gravis Ultrasound,
        Disney Sound Source, PC Speaker, Roland MT-32, General MIDI,
        Tandy/PCjr 3-voice, or no sound
      e.g. AdLib FM music with Sound Blaster effects, or Gravis music with
      PC speaker effects. Only one digital card (Sound Blaster, Gravis or
      Disney) can play at a time, so music and effects share it if both
      are digital.
    - Configure Sound Hardware: Sound Blaster port/IRQ/DMA, Gravis port,
      Disney printer port, MPU-401 port
    - Test Sound: plays music on the music card, then effects and Kiko's
      voice on the effects card
    - Kiko's Jukebox (see below)
  Settings are saved to NEKO.CFG, a small text file. NEKO.EXE reads it and
  starts straight into the game. Without NEKO.CFG the game auto-detects.

KIKO'S JUKEBOX
  Every district's song on your music card, with Kiko dancing to the beat,
  channel meters, a scrolling marquee and five ASCII visualizers:
      SPECTRUM      18-band analyser with peak hold and per-song weather
      OSCILLOSCOPE  the live waveform of every note that's sounding
      PIANO ROLL    notes scroll past, coloured by instrument, bar lines
      NEKO PLASMA   demoscene plasma in each district's colours, beat flash
      NEKO RAVE     mirrored analyser with giant cat ears that jump on kicks
  SPACE play/pause   S stop   LEFT/RIGHT change track   1-6 pick a track
  PgUp/PgDn skip 4 bars   A auto-advance   F frenzy tempo   V visualizer
  ESC back
  Mouse: click tracks, buttons, or the progress bar to jump; click the
  visualizer's title to switch it; click Kiko and she says nya.
  Start it straight from DOS with:  SETUP /JUKEBOX

VIDEO MODES
      VGA       320x200, 256 colours   full colour, best
      EGA       320x200, 16 colours    ordered dithering
      CGA       320x200, 4 colours     black/cyan/magenta/white
      Hercules  720x348, monochrome    dithered greyscale
      Tandy     320x200, 16 colours    Tandy 1000 / PCjr mode 9, dithered

SOUND DEVICES
  Sound Blaster 16/Pro/2.0  digital music and effects, auto-init DMA
  Sound Blaster 1.x         digital, single-cycle DMA re-armed from its IRQ
  Gravis Ultrasound         digital, streamed through GUS memory
  Disney Sound Source       digital at 7 kHz through the printer port
  AdLib                     FM synthesis with OPL2 rhythm-mode drums
  PC Speaker                one beeping voice: effects, then melody, then bass;
                            Kiko's voice plays as 16 kHz pulse-width "RealSound"
  Roland MT-32              MPU-401 UART, MT-32 patches, song titles on the LCD
  General MIDI              MPU-401 UART: lead, harmony, arpeggio, bass, pad
                            and drums on separate channels
  Tandy / PCjr 3-voice      TI SN76496 at port C0h: three square voices plus
                            noise drums with software envelopes

COMMAND-LINE SWITCHES (override NEKO.CFG)
  NEKO /VGA /EGA /CGA /HGC /TANDY
  NEKO /SB16 /SBPRO /SB2 /SB /ADLIB /GUS /DISNEY /SPEAKER /MT32 /GM /TSND
       /NOSOUND
  (a sound switch sets both music and effects)
  The game still needs a 386 or better in every mode.

RUNNING ON REAL HARDWARE
  386 or better with an FPU recommended (486DX/Pentium plays best),
  VGA, EGA, CGA or Hercules graphics, a DOS mouse driver, 4 MB RAM.
  Any of the sound devices above. SETUP reads the BLASTER and ULTRASND
  variables when they are set, or you can enter the settings by hand.
  MIDI needs an MPU-401 in UART mode (any MPU-401, SB16 or GUS MIDI port).

HOW TO PLAY
  Click Kiko to pet her and earn hearts. Fill the PURR meter to start a
  Purr Frenzy. Hire staff, buy upgrades, and click customers when they
  walk in for tips and boosts. When you have Neon Stars, relocate to a
  new district. Each of the six districts has its own skyline and song.

CONTROLS
  Mouse        click Kiko, customers, buttons and upgrade nodes
               (in the upgrade tree, click a node to select it, click again to buy)
  SPACE/ENTER  pet Kiko
  1 2 3 4      Staff / Upgrades / Relocate / Info panels
  B            hire x1 / x10 / MAX
  M / S        music / sound effects on or off
  ESC          close panel, or quit (progress is saved to NEKO.SAV)

Progress also autosaves every 15 seconds and you earn offline income
while away. Leave the title screen alone for 15 seconds and Kiko plays
a demo of the cafe by herself - press any key to take over.

SECRETS (spoilers!)
  Type these while playing:
      KIKO      say hi                PURR     instant Purr Frenzy
      TIPJAR    10 minutes of income  HELLO    a customer walks in
      PARTY     party mode            UP UP DOWN DOWN LEFT RIGHT LEFT RIGHT B A
  Cheating is permanently noted in your Cafe Records.

CREDITS
  This product uses DOS/32 Advanced DOS Extender technology.
  DOS/32 Advanced DOS Extender, Copyright (C) 1996-2006 by Narech K.
  All rights reserved. See DOS32A.TXT for its license.
