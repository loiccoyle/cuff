# Cuff

Query the [Jackett](https://github.com/jackett/jackett) search API from the command line.

# Installation

tbd

# Usage

```
$ cuff -h
Query the Jackett search API from the command line.

Usage:
    cuff [-h] [-v] [-s] [-k] {search, config, indexers, categories, open}
        -h                    Show this message and exit.
        -r                    Raw output, no coloring.
        -v                    Verbosisty, up to -vv.
        -s                    Start Jackett service if not running.
        -k                    Stop Jackett service before exiting.
        -u JACKETT_URL        Jackett URL.
        -a API_KEY            Jackett API key, will query Jackett for it if not provided.
        -p PASSWORD           Jackett password.

    cuff search [-f FORMAT] [-c CATEGORY] [-t TRACKER] QUERY...
                              Perform a search.
        -f FORMAT             Output format, in jq syntax, full json output if not provided.
        -c CATEGORY           Restrict search to caregories.
        -t TRACKER            Restrict search to trackers.
                              TRACKER must be a configured indexer.
        -s SORTKEY            Sort results by key.

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

# Completions

Completions for various shells can be found in the [`completions`](./completions) folder.
