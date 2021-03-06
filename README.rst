KnowIt
==========
Know better your media files.

.. image:: https://img.shields.io/pypi/v/knowit.svg
    :target: https://pypi.python.org/pypi/knowit
    :alt: Latest Version

.. image:: https://travis-ci.org/ratoaq2/knowit.svg?branch=master
    :target: https://travis-ci.org/ratoaq2/knowit
    :alt: Travis CI build status

.. image:: https://img.shields.io/github/license/ratoaq2/knowit.svg
    :target: https://github.com/ratoaq2/knowit/blob/master/LICENSE
    :alt: License


:Project page: https://github.com/ratoaq2/knowit


Usage
-----
CLI
^^^
Extract information from a video file::

    $ knowit /folder/Audio Samples/hd_dtsma_7.1.mkv
    For: /folder/Audio Samples/7.1Ch DTS-HD MA - Speaker Mapping Test File.mkv
    Knowit 0.2.4 found:
    {
        "title": "7.1Ch DTS-HD MA - Speaker Mapping Test File",
        "path": "/folder/Audio Samples/7.1Ch DTS-HD MA - Speaker Mapping Test File.mkv",
        "duration": "0:01:37",
        "size": "40.77 MB",
        "bit_rate": "3.3 Mbps",
        "container": "mkv",
        "video": [
            {
                "id": 1,
                "duration": "0:01:37",
                "width": "1920 pixel",
                "height": "1080 pixel",
                "scan_type": "Progressive",
                "aspect_ratio": 1.778,
                "pixel_aspect_ratio": 1.0,
                "resolution": "1080p",
                "frame_rate": "23.976 FPS",
                "bit_depth": "8 bit",
                "codec": "H.264",
                "profile": "Main",
                "profile_level": "4",
                "media_type": "video/H264",
                "default": true,
                "language": "Undetermined"
            }
        ],
        "audio": [
            {
                "id": 2,
                "name": "7.1Ch DTS-HD MA",
                "language": "English",
                "duration": "0:01:37",
                "codec": "DTS-HD",
                "profile": "Master Audio",
                "channels_count": 8,
                "channels": "7.1",
                "bit_depth": "24 bit",
                "bit_rate_mode": "Variable",
                "sampling_rate": "48.0 KHz",
                "compression": "Lossless",
                "default": true
            }
        ],
        "provider": "libmediainfo.so.0"
    }


Extract information from a video file using ffprobe::

    $ knowit --provider ffmpeg /folder/Audio Samples/hd_dtsma_7.1.mkv
    For: /folder/Audio Samples/7.1Ch DTS-HD MA - Speaker Mapping Test File.mkv
    Knowit 0.2.4 found:
    {
        "title": "7.1Ch DTS-HD MA - Speaker Mapping Test File",
        "path": "/folder/Audio Samples/7.1Ch DTS-HD MA - Speaker Mapping Test File.mkv",
        "duration": "0:01:37",
        "size": "40.77 MB",
        "bit_rate": "3.3 Mbps",
        "container": "mkv",
        "video": [
            {
                "id": 0,
                "width": "1920 pixel",
                "height": "1080 pixel",
                "scan_type": "Progressive",
                "aspect_ratio": 1.778,
                "pixel_aspect_ratio": 1.0,
                "resolution": "1080p",
                "frame_rate": "23.976 FPS",
                "bit_depth": "8 bit",
                "codec": "H.264",
                "profile": "Main",
                "default": true,
                "language": "Undetermined"
            }
        ],
        "audio": [
            {
                "id": 1,
                "name": "7.1Ch DTS-HD MA",
                "language": "English",
                "codec": "DTS-HD",
                "profile": "Master Audio",
                "channels_count": 8,
                "channels": "7.1",
                "bit_depth": "24 bit",
                "sampling_rate": "48.0 KHz",
                "default": true
            }
        ],
        "provider": "ffprobe"
    }


All available CLI options::

    $ knowit --help
    usage: knowit [-h] [-p PROVIDER] [-E] [-v] [-r] [--report] [-y] [-N]
                       [-P PROFILE] [--mediainfo MEDIAINFO] [--ffmpeg FFMPEG]
                       [--version]
                       [videopath [videopath ...]]

    positional arguments:
      videopath             Path to the video to introspect

    optional arguments:
      -h, --help            show this help message and exit

    Providers:
      -p PROVIDER, --provider PROVIDER
                            The provider to be used: mediainfo, ffmpeg or enzyme.

    Input:
      -E, --fail-on-error   Fail when errors are found on the media file.

    Output:
      -v, --verbose         Display debug output
      -r, --raw             Display raw properties
      --report              Parse media and report all non-detected values
      -y, --yaml            Display output in yaml format
      -N, --no-units        Display output without units
      -P PROFILE, --profile PROFILE
                            Display values according to specified profile: code,
                            default, human, technical

    Configuration:
      --mediainfo MEDIAINFO
                            The location to search for MediaInfo binaries
      --ffmpeg FFMPEG       The location to search for FFmpeg (ffprobe) binaries

    Information:
      --version             Display knowit version.



Installation
------------
KnowIt can be installed as a regular python module by running::

    $ [sudo] pip install knowit

For a better isolation with your system you should use a dedicated virtualenv or install for your user only using
the ``--user`` flag.


External dependencies
-------------------------
KnowIt can use MediaInfo or FFmpeg (ffprobe)

KnowIt supports MKV regardless if MediaInfo or FFmpeg are installed.

MediaInfo or FFmpeg increases the number of supported formats and the number of extracted information.

MediaInfo is the default provider. Visit their `website <http://mediaarea.net/MediaInfo>`_ and install the proper package for your system.

FFmpeg (ffprobe) can be downloaded `here <https://ffmpeg.org/download.html>`_
