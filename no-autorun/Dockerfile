# fetch node v4 LTS codename argon
FROM node:argon

# Create app directory
RUN mkdir -p /usr/src/spfx
WORKDIR /usr/src/spfx

# install global gulp dependency
RUN npm install -g npm@latest
#
RUN npm install -g gulp

# define build argument
ARG samplename


# define ports to be exposed
EXPOSE 4321 35729 5432

# Clone SPFx Sample GitHub repository
RUN git clone --depth 1 --branch master https://github.com/SharePoint/sp-dev-fx-webparts.git .

# Add cleanup tool
ADD cleanup.sh .

# Mount VOLUME
VOLUME /usr/src/spfx

# Set working directory to the directory defined in argument
WORKDIR /usr/src/spfx/samples/$samplename

RUN useradd --create-home --shell /bin/bash spfx && \
    usermod -aG sudo spfx && \
    chown -R spfx:spfx /usr/src/spfx


USER spfx

CMD /bin/bash
# Install all packages in the project
# RUN npm install

# Run gulp serve
# CMD ["gulp", "serve"]