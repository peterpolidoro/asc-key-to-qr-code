# This file is generated automatically from .metadata.org
# File edits may be overwritten!

MAKEFILE_PATH := $(abspath $(lastword $(MAKEFILE_LIST)))
MAKEFILE_DIR := $(notdir $(patsubst %/,%,$(dir $(MAKEFILE_PATH))))
MAKEFILE_DIR_ABS := $(dir $(MAKEFILE_PATH))
KICAD_CONFIG_HOME := $(MAKEFILE_DIR_ABS).config/kicad/
GUIX-TIME-MACHINE = guix time-machine -C $(MAKEFILE_DIR)/guix/channels.scm
GUIX-SHELL = $(GUIX-TIME-MACHINE) -- shell -m $(MAKEFILE_DIR)/guix/manifest.scm
CONTAINER = --container -F -E "^DISPLAY$$" -E "^XAUTHORITY$$" --expose="$$XAUTHORITY" --expose=/tmp/.X11-unix/ --expose=$$HOME/.Xauthority --expose=/etc/machine-id
GUIX-CONTAINER = $(GUIX-SHELL) $(CONTAINER)

.PHONY: guix-shell
guix-shell:
	$(GUIX-SHELL)

.PHONY: guix-container
guix-container:
	$(GUIX-CONTAINER)

.PHONY: ipython-shell
ipython-shell:
	$(GUIX-CONTAINER) -- ipython

.PHONY: exported-public-keys
exported-public-keys:
	$(GUIX-SHELL) -- gpg --armor --export > pgp-public-keys.asc

.PHONY: exported-private-keys
exported-private-keys:
	$(GUIX-SHELL) -- gpg --armor --export-secret-keys > pgp-private-keys.asc

.PHONY: qrcode-public-images
qrcode-public-images:
	$(GUIX-SHELL) -- ./asc2qr.sh pgp-public-keys.asc

.PHONY: qrcode-private-images
qrcode-private-images:
	$(GUIX-SHELL) -- ./asc2qr.sh pgp-private-keys.asc

