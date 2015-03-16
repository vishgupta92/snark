This is a repost of the source code from here:
http://klomp.org/snark/

## Introduction ##

Snark is a client for downloading and sharing files distributed with the BitTorrent protocol. It is mainly used for exploring the BitTorrent protocol and experimenting with the the GNU Compiler for Java (gcj). But it can also be used as a regular BitTorrent Client.

Snark can also act as a torrent creator, micro http server for delivering metainfo.torrent files and has an integrated Tracker for making sharing of files as easy as possible.

When given the option --share Snark will automatically create a .torrent file, start a very simple webserver to distribute the metainfo.torrent file and a local tracker that other BitTorrent clients can connect to.


```
snark [--debug [level]] [--no-commands] [--port <port>]
      [--share (<ip>|<host>)] (<url>|<file>|<dir>)
  --debug       Shows some extra info and stacktraces.
    level       How much debug details to show
                (defaults to 3, with --debug to 4, highest level is 6).
  --no-commands Don't read interactive commands or show usage info.
  --port        The port to listen on for incomming connections
                (if not given defaults to first free port between 6881-6889).
  --share       Start torrent tracker on <ip> address or <host> name.
  <url>         URL pointing to .torrent metainfo file to download/share.
  <file>        Either a local .torrent metainfo file to download
                or (with --share) a file to share.
  <dir>         A directory with files to share (needs --share).
```

## Examples ##

> To simple start downloading/sharing a file. Either download the .torrent file to disk and start snark with:

> `./snark somefile.torrent`

> Or give it the complete URL:

> `./snark http://somehost.example.com/cd-images/bbc-lnx.iso.torrent`

> To start seeding/sharing a local file:

> `./snark --share my-host.example.com some-file`

> Snark will respond with:
```
      Listening on port: 6881
      Trying to create metainfo torrent for 'some-file'
      Creating torrent piece hashes: ++++++++++
      Torrent available on http://my-host.example.com:6881/metainfo.torrent
```

> You can now point other people to the above URL so they can share the file with their own BitTorrent client.