# Cuff

Query the [Jackett](https://github.com/jackett/jackett) search API from the command line.

# Installation

tbd

# Usage

```sh
$ cuff -h
Queyr the Jackett search API from the command line.

Usage:
    cuff [-h] [-v] [-s] [-k] {search, config, indexers, categories, open}
        -h                              Show this message and exit.
        -v                              Verbosisty, up to -vv.
        -s                              Start Jackett server if not running.
        -k                              Stop Jackett before exiting.
        -u JACKETT_URL                  Jackett URL.
        -a API_KEY                      Jackett API key, will query Jackett for it if not provided.
        -p PASSWORD                     Jackett password.

    cuff search [-f {'json', FORMAT}] [-c CATEGORY] [-t TRACKER] QUERY...
                                        Perform a search.
        -f {'json', FORMAT}             Output format in jq syntax, set to 'json' to output in json.
        -c CATEGORY                     Restrict search to caregories, e.g. '-c movies -c tv'
        -t TRACKER                      Restrict search to trackers, e.g. '-t legittorrents -t thepiratebay'
                                        TRACKER must be a configured indexer.
        -s SORTKEY                      Sort results by key.

    cuff indexers                       List configured indexers.
    cuff categories                     List torrent categories.
    cuff config                         Show Jackett config (json).
    cuff open                           Open the Jackett dashboard using 'qutebrowser'.

Examples:
    Search for big buck bunny on all configured indexers.
    $ cuff search big buck bunny
    Search for big buck bunny movies/tv on tpb indexers.
    $ cuff search -c movies -c tv -t thepiratebay big buck bunny
    Search for big buck bunny with full json output sorted by Seeders.
    $ cuff search -f json -s Seeders big buck bunny
    Search for big buck bunny and output the title and link.
    $ cuff search -f '\(.Title)|\(.Seeders)|\(.MagnetUri//.Link)' big buck bunny
```

# Completions

Completions for various shells can be found in the `[completions](./completions)` folder.
