# EasyRedir dev-env

## What is this for?

`dev-env` is a self-contained, mostly zero-configuration environment for developing web applications using Docker on a Mac. It assumes that you have not installed any of the dependencies before.

## The tl;dr Version

First, install [Docker Desktop for Mac](https://docs.docker.com/desktop/mac/install/) with the appropriate architecture
for your current Mac (either Intel or Apple Silicon). Then run this...

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/EasyRedir/dev-env/master/bin/bootstrap)
# Start a new shell and cd to a project that uses [Docker Compose](https://docs.docker.com/compose/)
dev up
```

## Step-By-Step Setup

### Terminology

**Host** or **host machine** refers to your physical computer.

**Containers** or **Docker containers** refer to the individual services running inside of [Docker for Mac](https://docs.docker.com/docker-for-mac/). This project uses Docker for Mac to execute containers natively on macOS.

### 1. Run the bootstrap script

This script will install the following:

- Homebrew
- Ansible

and will do these tasks:

- create a DNS resolver configuration pointing .test domains to your dev env Nginx proxy
- symlink the dev script to /usr/local/bin

It should run idempotently, meaning you should be able to run it as many times as you want and it won't hurt anything. If it fails due to a temporary condition (like network issues), running it again should pick up where it left off. If new items are added to the script, running it against a functioning environment should only add the new things.

    bash <(curl -fsSL https://raw.githubusercontent.com/EasyRedir/dev-env/master/bin/bootstrap)

After a successful installation, you can run the bootstrap again or you can instead run:

    dev update

### 2. Start working on a project with a Docker Compose file.

The DevTool script mostly aliases `docker compose` for convenience. It enforces some arguments on commands that we found to be more like defaults, as well as just being less characters to type.

    # Start a new shell (The Docker client needs some ENV)
    # cd to a project with a docker-compose.yml file
    dev up

## Alternate Setup

It is also fairly easy to configure all of this manually. The configuration files are pretty simple and easy to replicate. Most of the `dev` tool are just shortcuts or wrappers to existing Docker commands.

## Workflow

- The source code running inside a project container is loaded from the directory on your hard drive. You can use text editors and Git clients on the host machines, and shouldn't need to work in the guest machine or the container.
- You should not need to run any application code directly from your host machine. Try to force yourself to find a containerized way of accomplishing things.
- Run `dev` without any arguments for lots of help

### Troubleshooting

#### When in doubt, restart

Many issues can be solved by restarting the containers with `dev restart`. You can also try restarting Docker for Mac in the menu bar at the top of your screen.

## Contributors

* [Nicholas Silva](https://github.com/silvamerica), creator.
* [William Richards](https://github.com/wgrrrr), modifier of things.

## Contributing

1. Fork it ( https://github.com/EasyRedir/dev-env/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## License

This project was modified for Docker for Mac by [William Richards](https://github.com/wgrrrr) and was originally available as [Dash](https://github.com/ifttt/dash) from IFTTT. It is available under the MIT license. See the LICENSE file for more info.

Copyright 2017 IFTTT Inc.
