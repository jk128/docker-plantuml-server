# docker-plantuml-server

This is modified version of plantuml-servlet with additional functionality

made from a fork of orginal plantuml-servlet (https://github.com/plantuml/plantuml-server).

Repository with source code of a midified servlet:

https://github.com/jk128/plantuml-server

***Remark: WAR was made from branch universal-post-servlet***

## Usage

```sh
# either run in foreground (ctrl-c exits the server)
docker run -it -p 8080:8080 --rm neam/plantuml-server

# or in background (server keeps running until specifically killed)
docker logs -f $(docker run -d -p 8080:8080 neam/plantuml-server)
```

Visit http://ip-of-your-docker-host:8080 in your browser

Additional POST handling:

*POST* http://ip-of-your-docker-host:8080/universal/

with:
 
- action=encode
- source=[plantuml DSL code]
 
 produces ENCODED part which can be later used in url like: GET http://ip-of-your-docker-host:8080/png/ENCODED
 
*POST* http://ip-of-your-docker-host:8080/universal/

with:

- action=image
- format=png (or svg, or  atxt, more formats soon)
- source=[plantuml DSL code]

produces diagram in PNG/SVG or ASCII Art
