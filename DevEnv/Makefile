IMAGE?="dharmpal/dev-env"
MOUNTDIR=$(shell pwd)
build:
	docker build --rm -t $(IMAGE) .
run:
	docker run -ti -P $(IMAGE) zsh
run-mount:
	docker run -ti -P -v $(MOUNTDIR):/home/ubuntu/$$(basename $(MOUNTDIR)) $(IMAGE) zsh
update:
	docker pull $(IMAGE)
install:
	@echo "Installing '\033[0;31mdev-env\033[0m' ALIAS"
	@echo "*************************"
	echo "alias dev-env='docker run --network=host -ti -P -v $(MOUNTDIR):/home/ubuntu/$$(basename $(MOUNTDIR)) $(IMAGE) zsh'" >> $(SHELLRC)
	@echo "*************************"
	@echo "\033[0;33mRestart this terminal session\033[0m or run '\033[0;33msource $(SHELLRC)\033[0m' to use '\033[0;31mdev-env\033[0m' command"
