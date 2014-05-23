pwomxplayer
===========

pwomxplayer is a variant of OMXPlayer, a commandline OMX player for
the Raspberry Pi. OMXplayer was developed as a testbed for the XBMC
Raspberry PI implementation and is quite handy to use standalone.
pwomxplayer is a modified version with options for performing geometry
transformations related to displaying video on a video wall.

Compiling pwomxplayer
---------------------

GCC version 4.7 is required.

### Cross Compiling

You need the content of your sdcard somewhere mounted or copied. There might be
development headers to install on the running Pi system for the crosscompiling.

Edit Makefile.include and change the settings according your locations.

### Compiling on the Pi

You can also compile it on the PI the native way ;)

    make ffmpeg
    make
    make dist

Using pwomxplayer
-----------------

    Usage: pwomxplayer [OPTIONS] [FILE]
    Options :
             -h / --help                    print this help
	     --tile-code  CODE              use predefined tile configuration
	     --frame-size FXxFY             relative size of screen+bezel
	     -W / --wall  WxH+X+Y           geometry of wall
	     -T / --tile  WxH+X+Y           geometry of tile
	     -O / --orient ORIENT           screen orientation    : e.g. left
	     -F / --fit   FIT		    how to fit picture    : e.g. crop
	     -A / --autotile		    define from .pitile & .piwall
	     -R / --role  ROLE              role within .piwall definition
	     -C / --config CONFIG	    configuration within .piwall
             -n / --aidx  index             audio stream index    : e.g. 1
             -o / --adev  device            audio out device      : e.g. hdmi/local
             -i / --info                    dump stream format and exit
             -s / --stats                   pts and buffer stats
             -p / --passthrough             audio passthrough
             -d / --deinterlace             deinterlacing
             -w / --hw                      hw audio decoding
             -3 / --3d                      switch tv into 3d mode
             -y / --hdmiclocksync           adjust display refresh rate to match video
             -t / --sid index               show subtitle with index
             -r / --refresh                 adjust framerate/resolution to video
                  --boost-on-downmix        boost volume when downmixing
                  --subtitles path          external subtitles in UTF-8 srt format
                  --font path               subtitle font
                                            (default: /usr/share/fonts/truetype/freefont/FreeSans.ttf)
                  --font-size size          font size as thousandths of screen height
                                            (default: 55)
                  --align left/center       subtitle alignment (default: left)
                  --lines n                 number of lines to accommodate in the subtitle buffer
                                            (default: 3)

For example:

    ./omxplayer -p -o hdmi test.mkv

Key Bindings
------------

While playing you can use the following keys to control omxplayer:

    z			Show Info
    1			Increase Speed
    2			Decrease Speed
    j			Previous Audio stream
    k			Next Audio stream
    i			Previous Chapter
    o			Next Chapter
    n			Previous Subtitle stream
    m			Next Subtitle stream
    s			Toggle subtitles
    d			Subtitle delay -250 ms
    f			Subtitle delay +250 ms
    q			Exit OMXPlayer
    Space or p	Pause/Resume
    -			Decrease Volume
    +			Increase Volume
    Left Arrow	Seek -30
    Right Arrow	Seek +30
    Down Arrow	Seek -600
    Up Arrow	Seek +600
