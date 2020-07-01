# Pencoder

> Yet another powerful **p**ayload **encoder** powered by Bash

## Features

- Single Bash script
- No 3rd party dependencies
- Support different kinds of encoders/decoders
- Apply multiple encodings at the same time

## Supported encoders

- Base32 encode/decode
- Base64 encode/decode
- Hex encode/decode
- URL encode/decode
- Unicode \u-escaped numbers encode/decode

## Download

```bash
~$ wget https://raw.githubusercontent.com/KevCui/pencoder/master/pencoder.sh
~$ chmod +x pencoder.sh
```

## Usage

```
Usage:
  ./pencoder.sh [encoder1] [encoder2] ... <string>

Options:
  string           input string
  encoder          b32en: base32 encode
                   b32de: base32 decode
                   b64en: base64 encode
                   b64de: base64 decode
                   hexen: hex encode
                   hexde: hex decode
                   urlen: URL encode
                   urlde: URL decode
                   unicodeen: Unicode \u-escaped numbers encode
                   unicodede: Unicode \u-escaped numbers decode
                   support multiple encoders: encoder1 encoder2...
  -h | --help      display this help message
```

## Examples

### Encoding with one encoder

```bash
~$ ./pencoder.sh b64en 'this is a test'
dGhpcyBpcyBhIHRlc3Q=
```

### Decoding with one dencoder

```bash
~$ ./pencoder.sh b64de 'dGhpcyBpcyBhIHRlc3Q='
this is a test
```

### Encoding with multiple encoders

```bash
~$ ./pencoder.sh urlen b64en hexen 'crazy encoding'
59334a68656e6b6c4d6a426c626d4e765a476c755a773d3d
```

### Decoding with multiple dencoders

```bash
~$ ./pencoder.sh hexde b64de urlde '59334a68656e6b6c4d6a426c626d4e765a476c755a773d3d'
crazy encoding
```

### Running the same encoder multiple times

```bash
~$ ./pencoder.sh b64en b64en b64en 'xyz'
WlVoc05nPT0=
```

### Working with pipes

```bash
~$ echo "super mario" | xargs ./pencoder.sh urlen b64en hexen
633356775a58496c4d6a427459584a7062773d3d
```
