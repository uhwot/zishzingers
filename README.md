# zishzingers

A set of tools for working with the fish fingers (FF) bytecode script format used in the mainline LittleBigPlanet franchise.

## Compilation

- Install the latest version of [Zig](https://ziglang.org/) (tested with version `0.12.0-dev.3677+22a97cd23`)
- Run `zig build`, which will place an executable file titled `zishzingers` in `zig-out/bin/`

## Usage

All tools are compiled into the same `zishzingers` executable file, with each tool being available through a different subcommand

### `disasm`
Disassembles script files into a human-readable format

```
# When a script is inside the LBP resource container, just pass the script name
$ zishzingers disasm compressed_script.ff
# When a script is pre-decompressed, you need to specify the compression flags and the asset revision
$ zishzingers disasm -n decompressed_script.ff -c integers -c matrices -c vectors -r 0x272
```

### `generate_library`
Generates an A# library from a folder of extracted assets and a MAP file.

```
# Read the help file `zishzingers generate_library --help` for details on what these options do!
$ zishzingers generate_library -m blurayguids.map -o deploy_std/ -f game_data/ -s std -n lbpdeploy
```

### `compile`
Compiles an A# file into an LBP script file.

```
# Read the help file `zishzingers compile --help` for details on what these options do!
# zishzingers compile compile samples/tweakegg.as -l lbpdeploy:deploy_std/ -i 1234
```

Sample scripts are provided in the `samples/` folder.

You can read a WIP language reference [here](langref.md).

## Special Thanks

*Massive* shoutouts to [Aidan](https://github.com/ennuo) for the constant help with my reverse engineering efforts, this project would not have been possible if it not for the work they did on [toolkit](https://github.com/ennuo/toolkit) (which I referenced for resource serialization) and craftworld.js (which I referenced for the FF file structure and instruction class types).

Along with shoutouts to [uh wot](https://github.com/uhwot) for early help with the bytecode encoding, and pointing me towards craftworld.js for the file structure.