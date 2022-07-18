# payload-dumper-go

An android OTA payload dumper written in Go.

Download prebuilt binaries for macOS, Windows and Linux via [here](https://github.com/ssut/payload-dumper-go/releases).

## Build
```bash
# Install golang before you build it
# For ArchLinux
$ sudo pacman -S go
```
```bash
$ go mod tidy
$ go mod download
$ CGO_ENABLE=0 go build -trimpath -o ./payload-dumper-go
```

## Usage
```bash
Usage: ./payload-dumper-go [options] [inputfile]
  -c int
        Number of multiple workers to extract (shorthand) (default 4)
  -concurrency int
        Number of multiple workers to extract (default 4)
  -l    Show list of partitions in payload.bin (shorthand)
  -list
        Show list of partitions in payload.bin
  -o string
        Set output directory (shorthand)
  -output string
        Set output directory
  -p string
        Dump only selected partitions (comma-separated) (shorthand)
  -partitions string
        Dump only selected partitions (comma-separated)
```
```bash
$ ./payload-dumper-go ./payload.bin
```

## Features

![screenshot](https://i.imgur.com/IJtwoWU.png)

See how fast payload-dumper-go is: https://imgur.com/a/X6HKJT4. (MacBook Pro 16-inch 2019 i9-9750H, 16G)

- Incredibly fast decompression. All decompression progresses are executed in parallel.
- Payload checksum verification.
- Support original zip package that contains payload.bin.

### Cautions

- Working on a SSD is highly recommended for performance reasons, a HDD could be a bottle-neck.

### Limitations

- Incremental OTA(delta) payload is not supported.

## Sources

https://android.googlesource.com/platform/system/update_engine/+/master/update_metadata.proto

## License

This source code is licensed under the Apache License 2.0 as described in the LICENSE file.
