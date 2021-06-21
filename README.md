# Gatsby development docker project

Example project to develop application with [GatsbyJS](https://gatsbyjs.com/) using [Docker](https://www.docker.com/).

This project use [bmeme/gatsby-dev](https://hub.docker.com/r/bmeme/gatsby-dev) image from [BMEME](https://www.bmeme.com).

## TL;DR

Configure your project:
```bash
$ ./configure
```

Create and run the docker container:

```bash
$ docker-compose up -d --build
```

Run the Gatsby CLI to create your project:

```bash
$ rm app/.gitkeep
$ ./gatsby new .
```

Run your application

```bash
$ ./gatsby develop --host=0.0.0.0
```

## Documentation

### Project configuration
The `configure` script prepare the `.env` file for you.

What it does: 
 * set your project name and vendor;
 * set the correct UID and GID the docker image must be bult with to fit your current user.

Project _name_ and _vendor_ are, respectively, the identifier of your project and the organization to which it belongs (ie: _name_ could be `webticketapp`, and _vendor_ `myclientcorp`). They are used to setup various docker related things: among them, most important is the DNS alias used for `dinghy_http_proxy` (macos) and `dnsdock` (linux).

You can pass _vendor_ and _name_ of your project from the command line:
```bash
$ ./configure bmeme myproject
```

### The docker environment

This project create a docker environment that you can use to develop and build your GatsbyJS application. 
The docker environment lifecycle could be summarized as follow: `build`, `start`, `stop`and `clean`.

![Docker Environment Lifecycle (1)](https://user-images.githubusercontent.com/445544/122754211-a5494500-d293-11eb-85a6-13a1d3657daa.jpg)

Build the docker development container

```
$ docker-compose build
$ docker-compose up -d
```

Stop the docker environment:
```bash
$ docker-compose stop
```

Start the docker environment:
```bash
$ docker-compose start
```

Clean up the docker environment:
```bash
$ docker-compose down -v
```

### Use the GatsbyJs CLI wrapper

Create a new gatsby project:

```
$ rm app/.gitkeep
$ ./gatsby new .
```

Run gatsby develop:

```
$ ./gatsby develop --host=0.0.0.0
```

Run gatsby serve:

```
$ ./gatsby build && ./gatsby serve --host=0.0.0.0
```

Install a gatsby plugin:

```
$ ./npm install gatsby-plugin-styled-components styled-components babel-plugin-styled-components
```

## References

- [gatbsy-cli npm package](https://www.npmjs.com/package/gatsby-cli)
- [Gatsby official tutorial](https://www.gatsbyjs.com/docs/tutorial/)
- [Gatsby tutorial on youtube by Coding Addict](https://www.youtube.com/watch?v=5Mam9NuxwQc)
- [Node.js Docker official images](https://hub.docker.com/_/node)
