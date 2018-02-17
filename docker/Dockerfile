FROM debian:jessie-slim

RUN apt update; apt install -y wget gnupg
RUN wget http://files.freeswitch.org/repo/deb/debian/freeswitch_archive_g0.pub  -O - | apt-key add -
RUN echo "deb http://files.freeswitch.org/repo/deb/freeswitch-1.6/ jessie main" > /etc/apt/sources.list.d/freeswitch.list

RUN apt-get update
RUN apt-get install -y freeswitch freeswitch-mod-rtc \
        freeswitch-mod-console freeswitch-mod-conference \
        freeswitch-mod-logfile freeswitch-mod-local-stream \
        freeswitch-mod-sofia freeswitch-mod-event-socket freeswitch-mod-cdr-csv \
        freeswitch-mod-dialplan-xml \
        freeswitch-mod-sndfile freeswitch-mod-commands \
        freeswitch-mod-dptools freeswitch-mod-portaudio \
        freeswitch-mod-hash freeswitch-mod-v8 \
	freeswitch-mod-curl freeswitch-mod-tone-stream

COPY etc/freeswitch /etc/freeswitch
#COPY sounds /usr/share/freeswitch/sounds

ENTRYPOINT ["/usr/bin/freeswitch", "-u", "freeswitch", "-g", "freeswitch", "-nonat"]
