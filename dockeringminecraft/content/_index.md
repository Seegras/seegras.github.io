+++
outputs = ["Reveal"]
title = "Dockering Minecraft"

+++
## Dockering Minecraft
An exercise in automation

---

## Dockerfile

{{ $lang := "bash" }}
{{< highlight go "style=github,linenos=inline,hl_lines=6" >}}
FROM openjdk:17

RUN useradd --create-home appuser
WORKDIR /home/appuser
USER appuser

CMD java -Xmx2G -Xms1024M -jar fabric-server-mc.1.19.2-loader.0.14.11-launcher.0.11.1.jar nogui
{{< /highlight >}}

---

## Build & Run

{{ $lang := "bash" }}
{{< highlight go "style=github" >}}
docker build -t minecraft .
docker run --rm --name minecraft-server -p 25565:25565 -v `pwd`:/home/appuser minecraft 
{{< /highlight >}}

---

## Caveats

* Diff
  * Outcome may vary
* Complete Definition
  * Must be adapted frequently
  * Becomes a (security-) liability
* Part Definition
  * Subject to changes in un(der)defined parts

---

## What?

* Configs
* Secrets?
* Packages
* Operating Systems
* Connections and Network
* Hardware Definitions

---

## More?

* Monitoring as the unit-test of engineering
* Staging environments
* Continuous Integration
* Orchestration

---

## Questions? 

@seegras


