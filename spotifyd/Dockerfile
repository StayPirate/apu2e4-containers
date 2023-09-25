FROM archlinux:base

RUN pacman -Syu --noconfirm && \
    pacman -S --noconfirm spotifyd alsa-utils

# Archlinux uses a different gid for the audio group (996), while debian (underline OS) uses 29.
# In order to give access to the following user to the /dev/snd host folder I need to create a new
# group with gid 29 and add the user in it.
RUN groupadd -g 29 audio_debian
# Add user `spotify` and create home folder
RUN useradd -l --create-home -G audio,audio_debian spotify
# Set the working directory in the container
WORKDIR /home/spotify
USER spotify

ENTRYPOINT ["spotifyd", "--config-path", "config", "--no-daemon"]