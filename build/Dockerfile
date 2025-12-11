FROM texlive/texlive:latest

# Updates and installs commons
RUN apt-get update \
	&& apt-get install -y \
	curl \
	git \
	sudo \
	vim \
	wget \
	jq \
	locales

# Sets local
RUN localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG=en_US.utf8

# Clears apt lists
RUN rm -rf /var/lib/apt/lists/* 

# Adds the default User
ARG USER=lth-student
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
	&& echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
	&& chmod 0440 /etc/sudoers.d/${USER}

# Sets user and work directory
USER ${USER}
WORKDIR /home/${USER}