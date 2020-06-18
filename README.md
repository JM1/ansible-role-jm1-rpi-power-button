# Ansible Role: jm1.rpi_power_button

This role helps to setup a power button on Raspberry Pi.

*Details*
- python script `rpi-power-button.py` waits until Raspberry Pi's GPIO Pin 5 ([`BCM 3 (SCL)`](https://pinout.xyz/pinout/pin5_gpio3))
  is triggered and then sends a shutdown command.
- systemd service `rpi-power-button.service` starts Python script `rpi-power-button.py` during boot.

**Tested OS images**
- [`Ubuntu 20.04 LTS` (`arm64`) for Raspberry Pi 2B and later](http://cdimage.ubuntu.com/releases/20.04/release/)

Available on Ansible Galaxy: [jm1.rpi_power_button](https://galaxy.ansible.com/jm1/rpi_power_button)

## Requirements

Add a power button ([a simple momentary switch](https://learn.sparkfun.com/tutorials/switch-basics/all)) to
GPIO Pin 5 ([`BCM 3 (SCL)`](https://pinout.xyz/pinout/pin5_gpio3)) of your Raspberry Pi. Instructions on how
to do that can be found [here](https://howchoo.com/g/mwnlytk3zmm/how-to-add-a-power-button-to-your-raspberry-pi)
and [here](https://www.raspberrypi.org/forums/viewtopic.php?t=24682).

Download and flash an OS image to a (micro) SD card,
e.g. use the [guide on ubuntu wiki](https://wiki.ubuntu.com/ARM/RaspberryPi) to setup your Raspberry Pi with
[`Ubuntu 20.04 LTS` (`arm64`) for Raspberry Pi 2B and later](http://cdimage.ubuntu.com/releases/20.04/release/).

**NOTE**: Necessary software packages, e.g. Python 3, are installed automatically at the beginning during role execution!

Python 3 library [`RPi.GPIO`](https://pypi.org/project/RPi.GPIO/) is required by this Ansible role.

| OS                             | Install Instructions           |
| ------------------------------ | ------------------------------ |
| Ubuntu 20.04 LTS (Focal Fossa) | `apt install python3-rpi.gpio` |

## Variables

None

## Dependencies

| Name              | Description                                                                                                                    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `jm1.virtual_pkg` | Installs necessary software using [virtual packages](https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html#virtual) |

## Example Playbook

```
- hosts: all
  tasks:
    - import_role:
        name: jm1.rpi_power_button
```

For instructions on how to run Ansible playbooks have look at Ansible's
[Getting Started Guide](https://docs.ansible.com/ansible/latest/network/getting_started/first_playbook.html).

## License

GPL3

## Author

Jakob Meng
@jm1 ([github](https://github.com/jm1), [galaxy](https://galaxy.ansible.com/jm1), [web](http://www.jakobmeng.de))
