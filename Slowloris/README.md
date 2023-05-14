## What is Slowloris?

Slowloris is basically an HTTP Denial of Service attack that affects threaded servers. It works like this:

We start making lots of HTTP requests.
We send headers periodically (every ~15 seconds) to keep the connections open.
We never close the connection unless the server does so. If the server closes a connection, we create a new one keep doing the same thing.
This exhausts the servers thread pool and the server can't reply to other people.

## Usage

```sh
python slowloris.py example.com
```

## Configuration Options

```
usage: import argparse.py [-h] [-p] [-s] [-v] [-ua] [--https] [--use-proxy] [--sleeptime] [--proxy-host] [--proxy-port] [host]

Slowloris, low bandwidth stress test tool for websites.

positional arguments:
    host               Target host to attack.

options:
    -h, --help         show this help message and exit
    -p , --port        Port of webserver (default 80).
    -s , --sockets     Number of sockets to create.
    -v, --verbose      Show more information in the log.
    -ua, --user-agent  Randomizes user-agents with each request.
    --https            Use HTTPS for the requests.
    --use-proxy        Use a SOCKS5 proxy for connecting.
    --sleeptime        Time to sleep between each header sent.
    --proxy-host       SOCKS5 proxy host.
    --proxy-port       SOCKS5 proxy port.
```

## Source

https://github.com/gkbrk/slowloris
