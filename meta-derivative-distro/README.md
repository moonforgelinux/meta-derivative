# meta-derivative-distro

This layer extends the meta-moonforge-distro layer with customizations needed to build a derivative distro.

## What is does

* Provides a custom layer to clearly separate what's provided by Moonforge and by this layer.
* Provides a derivative distro configuration file, built on top of a specific release of Moonforge (e.g., *derivative* can be used as the *DISTRO* in the local configuration file).
* Extends the base image with custom packages (e.g., adding the python package).

## Examples

* See [derivative-image-base-raspberrypi5](../kas/derivative-image-base-raspberrypi5.yml).

