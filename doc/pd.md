# Installer PD

```
cd ~
mkdir src && cd src
wget http://msp.ucsd.edu/Software/pd-0.46-7.armv7.tar.gz
tar xvfz pd-0.46-7.armv7.tar.gz
```



#### notes supplémentaires

##### notes sur les cartes de sons
noter qu'il faut spécifiquement des carte n'ayant pas le même nom pour que PD soit capable de choisir la bonne carte au démarrage en command line.

Setup Fonctionnel de deux carte
```
aplay -l
```
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI] Subdevices: 1/1 Subdevice #0: subdevice #0
card 1: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0
card 2: Device [USB Audio Device], device 0: USB Audio [USB Audio] Subdevices: 1/1 Subdevice #0: subdevice #0

Lancer deux instances de pd avec deux cartes audio différtentes
```
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "3,1" ~/prog/test1.pd
pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "5,1" ~/prog/test2.pd
```




```
/home/pi/pd-0.46-7/bin/pd -nogui -listdev -audiooutdev "1,1" /home/pi/test/Untitled-1.pd
```





```
audio configuration flags:
-r <n>           -- specify sample rate
-audioindev ...  -- sound in device list; e.g., "2,1" for second and first
-audiooutdev ... -- sound out device list, same as above
-audiodev ...    -- specify both -audioindev and -audiooutdev together
-inchannels ...  -- number of audio in channels (by device, like "2" or "16,8")
-outchannels ... -- number of audio out channels (by device)
-channels ...    -- specify both input and output channels
-audiobuf <n>    -- specify size of audio I/O buffer in msec
-blocksize <n>   -- specify audio I/O block size in sample frames
-sleepgrain <n>  -- specify number of milliseconds to sleep when idle
-nodac           -- suppress audio output
-noadc           -- suppress audio input
-noaudio         -- suppress audio input and output (-nosound is synonym)
-listdev         -- list audio and MIDI devices
(linux specific audio:)
-oss            -- use ALSA audio drivers
-alsa           -- use ALSA audio drivers
-pa             -- use portaudio (experimental version 19)
-alsadev <n>    -- obsolete: use -audiodev
-32bit          -- (probably obsolete) -- use 32 bit OSS extension
-alsaadd <dev>  -- add a device to the ALSA device list
(Windows specific audio:)
-mmio           -- use MMIO drivers and API
-asio           -- use ASIO drivers and API
MIDI configuration flags:
-midiindev ...   -- midi in device list; e.g., "1,3" for first and third
-midioutdev ...  -- midi out device list, same format
-mididev ...     -- specify -midioutdev and -midiindev together
-nomidiin        -- suppress MIDI input
-nomidiout       -- suppress MIDI output
-nomidi          -- suppress MIDI input and output
-alsamidi        -- use ALSA midi API
general flags:
-path <path>     -- add to file search path
-nostdpath       -- don't search standard ("extra") directory
-stdpath         -- search standard directory (true by default)
-helppath <path> -- add to help search path
-open <file>     -- open file(s) on startup
-lib <file>      -- load object library(s)
-font <n>        -- specify default font size in points
-verbose         -- extra printout on startup and when searching for files
-version         -- don't run Pd; just print out which version it is
-d <n>           -- specify debug level
-noloadbang      -- suppress all loadbangs
-stderr          -- send printout to standard error instead of GUI
-nogui           -- suppress starting the GUI
-guiport <n>     -- connect to pre-existing GUI over port 'n'
-guicmd "cmd..." -- substitute another GUI program (e.g., rsh)
-send "msg..."   -- send a message at startup (after patches are loaded)
-rt or -realtime -- use real-time priority (needs root privilege)
-nrt             -- don't use real-time priority
-nosleep         -- never relinquish CPU (only for multiprocessors!)
```