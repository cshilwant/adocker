ARG BASE_DISTRO=ghcr.io/cshilwant/demo_baseline

FROM $BASE_DISTRO

RUN export DEBIAN_FRONTEND=noninteractive; apt-get update
RUN export DEBIAN_FRONTEND=noninteractive; \
         apt-get install -y --no-install-recommends qtmultimedia5-dev qtdeclarative5-dev qml-module-qtquick-controls2
RUN mkdir /tmp/gpu && cd /tmp/gpu && \
         git clone https://github.com/TexasInstruments/ti-apps-launcher && \
         cd ti-apps-launcher && mkdir build && cd build && qmake ../ti-demo.pro && make && \
         mv ti-demo /tmp/gpu/ && cd /tmp/gpu && rm -rf ti-apps-launcher && \
         apt-get purge -y --auto-remove git build-essential ca-certificates && \
         rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/tmp/gpu/ti-demo"]
