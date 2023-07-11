> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.


## Redis

Redis can be used as backend mechanism to communicate with the nodes on TFGrid using the RMB.

### Install

#### Linux
If you don't find Redis in your distro's package manager, check the [Redis downloads](https://redis.io/download) page for source code and installation instructions.

#### MacOS
Homebrew can be used to install Redis, as follows:

```
brew update
brew install redis
```

Alternatively, it can be built from source, using the same download page linked for Linux above.

### Run
Launch the Redis server with:

```
redis-server
```


.

