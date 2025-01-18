# wyoming mlx-whisper

[Wyoming protocol](https://github.com/rhasspy/wyoming) server for the [mlx-whisper](https://github.com/ml-explore/mlx-examples/tree/main/whisper) speech to text system, forked from [wyoming-faster-whisper](https://github.com/rhasspy/wyoming-faster-whisper).

[Source](https://github.com/home-assistant/addons/tree/master/whisper)

## Local Install

Install ffmpeg:

``` sh
# on macOS using Homebrew (https://brew.sh/)
brew install ffmpeg
```

Clone the repository and set up Python virtual environment:

``` sh
git clone https://github.com/raelix/wyoming-faster-whisper.git
cd wyoming-faster-whisper
script/setup
```

Run a server anyone can connect to:

```sh
./script/run --model "mlx-community/whisper-large-v3-mlx" --language en --uri 'tcp://0.0.0.0:10300'
```

The `--model` can also be a HuggingFace model like `mlx-community/whisper-medium.en-mlx` or `mlx-community/whisper-large-v3-turbo`.


[Source](https://github.com/rhasspy/wyoming-addons/tree/master/whisper)


## launchctl service

create a file in ~/Library/LaunchAgents, paste this inside, but change the path
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.user.whisper.service</string>

    <key>ProgramArguments</key>
    <array>
        <string>./script/run</string>
        <string>--model</string>
        <string>mlx-community/whisper-large-v3-turbo</string>
        <string>--language</string>
        <string>de</string>
        <string>--uri</string>
        <string>tcp://0.0.0.0:10300</string>
    </array>

    <key>WorkingDirectory</key>
    <string>/full/path/to/project/folder</string>

    <key>RunAtLoad</key>
    <true/>

    <key>KeepAlive</key>
    <true/>

    <key>StandardErrorPath</key>
    <string>/tmp/com.user.whisper.service.err</string>

    <key>StandardOutPath</key>
    <string>/tmp/com.user.whisper.service.out</string>

    <key>EnvironmentVariables</key>
    <dict>
        <key>PATH</key>
        <string>/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin</string>
    </dict>

</dict>
</plist>
```

Load and run and keep running via

```sh
launchctl load ~/Library/LaunchAgents/com.user.whisper.service.plist
```

Check logs via

```sh
cat /tmp/com.user.whisper.service.err  
```