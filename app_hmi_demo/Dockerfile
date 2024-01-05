ARG BASE_DISTRO=ghcr.io/cshilwant/demo_baseline

FROM $BASE_DISTRO

RUN mkdir /tmp/gpu && cd /tmp/gpu && \
         git clone https://github.com/TexasInstruments/ti-apps-launcher && \
         cd ti-apps-launcher && mkdir build && cd build && qmake ../ti-demo.pro && make \
         mv ti-demo /tmp/gpu/ && cd /tmp/gpu && rm -rf ti-apps-launcher && \
         apt-get purge -y --auto-remove git build-essential ca-certificates && \
         rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/tmp/gpu/ti-demo"]
