## What is Slowloris?

Slowloris is basically an HTTP Denial of Service attack that affects threaded servers. It works like this:

We start making lots of HTTP requests.
We send headers periodically (every ~15 seconds) to keep the connections open.
We never close the connection unless the server does so. If the server closes a connection, we create a new one keep doing the same thing.
This exhausts the servers thread pool and the server can't reply to other people.

## How to run?

```sh
python3 slowloris.py example.com
```

## Configuration Options

```
-p, --port
    Port of webserver, usually 80
    
-s, --sockets
    Number of sockets to use in the test
    
-v, --verbose
    Increases logging (output on terminal)
    
-ua, --randuseragents
    Randomizes user-agents with each request
    
-x, --useproxy
    Use a SOCKS5 proxy for connecting
    
--https
    Use HTTPS for the requests
    
--sleeptime
    Time to sleep between each header sent
```

## Source

https://github.com/gkbrk/slowloris
