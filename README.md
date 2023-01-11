# Cuff

<a href="./LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
<a href="https://aur.archlinux.org/packages/cuff-git/"><img src="https://img.shields.io/aur/version/cuff-git"></a>

Query the [Jackett](https://github.com/jackett/jackett) search API from the command line.

**Prefer a UI? Check out [`rofi-cuff`](https://github.com/loiccoyle/rofi-cuff)**

**Do you use [`Prowlarr`](https://github.com/prowlarr/prowlarr) instead of `Jackett`? Check out [`prowlet`](https://github.com/loiccoyle/prowlet) / [`rofi-prowlet`](https://github.com/loiccoyle/rofi-prowlet)**

# Installation

### Dependencies

If you are installing manually, you'll need to also install the following dependencies:

- [`curl`](https://github.com/curl/curl)
- [`jq`](https://github.com/stedolan/jq)
- Access to a [`jackett`](https://github.com/jackett/jackett) server.

### Manual

To manually install `cuff` just git clone this repository and place the script in your `$PATH`:

```
git clone https://github.com/loiccoyle/cuff
cd cuff
cp cuff /somewhere/in/your/PATH/
```

If you want <TAB> completion, place the corresponding [`completion`](completions) file somewhere your shell knows about.

### Arch linux

Using your prefered AUR helper:

```
paru -S cuff-git
```

# Completions

Completions for various shells can be found in the [`completions`](completions) folder.

# Usage

```
$ cuff -h
Query the Jackett search API from the command line.

Usage:
    cuff [OPTIONS] {search, config, indexers, categories, open}
        -h                        Show this message and exit.
        -r                        Raw output, no coloring.
        -v                        Verbosisty, up to -vv.
        -s                        Start Jackett service if not running.
        -k                        Stop Jackett service before exiting.
        -u JACKETT_URL            Jackett URL.
        -a API_KEY                Jackett API key, will query Jackett if not provided.
        -p PASSWORD               Jackett password.
    cuff search [OPTIONS] QUERY   Perform a search.
        -f FORMAT                 Output format, in jq syntax, full json output if not provided.
        -c CATEGORY               Restrict search to caregories.
        -t TRACKER                Restrict search to trackers.
                                  TRACKER must be a configured indexer.
        -s SORTKEY                Sort results by key.
    cuff indexers             List configured indexers.
    cuff categories           List torrent categories.
    cuff config               Show Jackett config (json).
    cuff open                 Open the Jackett dashboard using 'qutebrowser'.

Examples:
    Search for big buck bunny on all configured indexers.
    $ cuff search big buck bunny
    Search for big buck bunny movies/tv on tpb indexer.
    $ cuff search -c movies -c tv -t thepiratebay big buck bunny
    Search for ubuntu sorted by Seeders.
    $ cuff search -s Seeders ubuntu
    Search for ubuntu and output the title and link, format with column.
    $ cuff search -f '\(.Title)|\(.MagnetUri//.Link)' ubuntu | column -t -s"|"
```

# Note

To use the `-s` and `-k` options to start and stop the `jackett` service before/after making a query, will require `sudo` access.

# TODO

- [x] AUR package
- [ ] write bash completion
