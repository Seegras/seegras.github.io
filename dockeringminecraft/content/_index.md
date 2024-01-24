+++
outputs = ["Reveal"]
title = "Dockering Minecraft"

+++
## Dockering Minecraft
An exercise in automation

---

## Dockerfile

{{< highlight bash >}}
FROM openjdk:17

RUN useradd --create-home appuser
WORKDIR /home/appuser
USER appuser

CMD java -Xmx2G -Xms1024M -jar \
fabric-server-mc.1.19.2-loader.0.14.11-launcher.0.11.1.jar \
 nogui
{{< /highlight >}}

---

## Build & Run

{{< highlight bash >}}
docker build -t minecraft .
docker run --rm --name minecraft-server -p 25565:25565 -v \
 `pwd`:/home/appuser minecraft 
{{< /highlight >}}

---

## Questions? 

@seegras


