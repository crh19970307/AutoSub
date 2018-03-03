# Autosub 
  
  

### Auto-generated subtitles for any video

Autosub is a utility for automatic speech recognition and subtitle generation. It takes a video or an audio file as input, performs voice activity detection to find speech regions, makes parallel requests to Google Web Speech API to generate transcriptions for those regions, (optionally) translates them to a different language, and finally saves the resulting subtitles to disk. It supports a variety of input and output languages (to see which, run the utility with the argument `--list-languages`) and can currently produce subtitles in either the SRT format or simple JSON. 

The origin reposity is unable to run because of the google speech api is unable to reach and the google translate api is not free. I implement a version that uses shadowsocks as agent and send post request using the agent in the code. For google translate api, I use the thought of py-googletrans repository based on ajax tech.

### Prerequisite

  * Linux System
  * Python2


### Installation

1 install yasm and ffmpeg

    wget http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz
    tar xzvf  yasm-1.3.0.tar.gz
    cd  yasm-1.3.0
    ./configure
    make
    make install
 
    wget http://ffmpeg.org/releases/ffmpeg-3.0.tar.bz2
    tar xvfj ffmpeg-3.0.tar.bz2
    cd ffmpeg-3.0
    ./configure
    make
    make install

2 install shadowsocks

Note that your shadowsocks port should be the same with proxies in the code. (In this code it's 8887)

3 install autosub

    git clone https://github.com/crh19970307/autosub.git
    cd autosub
    sudo python setup.py install

### Usage

```
$ autosub -h
usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE]
               [-D DST_LANGUAGE]  [--list-formats]
               [--list-languages]
               [source_path]

positional arguments:
  source_path           Path to the video or audio file to subtitle

optional arguments:
  -h, --help            show this help message and exit
  -C CONCURRENCY, --concurrency CONCURRENCY
                        Number of concurrent API requests to make
  -o OUTPUT, --output OUTPUT
                        Output path for subtitles (by default, subtitles are
                        saved in the same directory and name as the source
                        path)
  -F FORMAT, --format FORMAT
                        Destination subtitle format
  -S SRC_LANGUAGE, --src-language SRC_LANGUAGE
                        Language spoken in source file
  -D DST_LANGUAGE, --dst-language DST_LANGUAGE
                        Desired language for the subtitles
  --list-formats        List all available subtitle formats
  --list-languages      List all available source/destination languages
```

### License

MIT

### Claim
The code is based on [autosub](https://github.com/agermanidis/autosub), [py-googletrans](https://github.com/ssut/py-googletrans)
