FROM ubuntu:18.04
RUN apt-get update && apt-get -y upgrade \
    bash-completion \
    build-essential \
    libssl-dev \
    libffi-dev \
    libxml2-dev \
    libxslt1-dev \
    zlib1g-dev \
    curl \
    git \
    git-core \
    golang \
    htop \
    locales \
    man \
    python3-pip \
    python3-dev \
    sudo \
    tig \
    wget \
    nano \
    fonts-powerline \
    zsh \
    iproute2
RUN pip3 install -U pip
RUN pip3 install virtualenv ipython
RUN curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN apt install -y nodejs
RUN locale-gen en_US.UTF-8
# Disable password and not ask for finger info
RUN adduser --disabled-password --gecos '' ubuntu
RUN adduser ubuntu sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER ubuntu
RUN touch ~/.hushlogin
WORKDIR /home/ubuntu
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
RUN wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/templates/zshrc.zsh-template -O /home/ubuntu/.zshrc
CMD ["zsh"]
