FROM continuumio/miniconda3:4.10.3-alpine AS build

ENV PYTHONUNBUFFERED=1

COPY install-poetry.py /installers/

RUN  \
    conda run -n base \
    python /installers/install-poetry.py \
        -y \
        --version 1.1.11

FROM continuumio/miniconda3:4.10.3-alpine AS run

ENV PYTHONUNBUFFERED=1

COPY bashrc /root/.bashrc
COPY --from=build /root/.local/bin/ /root/.local/bin/
COPY --from=build /root/.local/share/ /root/.local/share/
