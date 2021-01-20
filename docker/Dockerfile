# Use the MASSpy base image
FROM sbrg/masspy:latest AS setup
USER root

# Remove documentation from image to reduce size before adding publication files
WORKDIR ${HOME}/opt/MASSpy
RUN rm -rf docs

ENV PROJECT_DIR=${HOME}${PROJECT_VOLUME}/MASSpy-ExampleProject

WORKDIR ${PROJECT_DIR}

FROM setup AS build

COPY ./ ./

# Finish image
WORKDIR ${HOME}
RUN rm -rf tmp
RUN echo \
    && chown -R ${USER} ${PROJECT_DIR}/ \
    && chmod -R 777 ${PROJECT_DIR}/
USER ${USER}
WORKDIR ${PROJECT_DIR}
ENTRYPOINT [ "../../opt/docker-scripts/docker-entrypoint.sh" ]
CMD [ "sh" ]
