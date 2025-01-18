# IGNORE THIS PLEASE, JUST TRYING AROUND

⚠️ WARNING: This is a personal fork and is not maintained or supported.

[Wyoming protocol](https://github.com/rhasspy/wyoming) server for the [mlx-whisper](https://github.com/ml-explore/mlx-examples/tree/main/whisper) speech to text system, forked from [wyoming-faster-whisper](https://github.com/rhasspy/wyoming-faster-whisper).

[Source](https://github.com/home-assistant/addons/tree/master/whisper)

## Local Install

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
