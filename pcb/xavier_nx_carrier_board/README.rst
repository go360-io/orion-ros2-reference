Heavily modified by Go360.io

=================================
Jetson Nano / Xavier NX baseboard
=================================

Copyright (c) 2020 `Antmicro <https://www.antmicro.com>`_

.. image:: Images/jetson-nano-baseboard.png
   :scale: 40%

Overview
========

This repository contains open hardware design files for a baseboard supporting the NVIDIA Jetson Nano SoM as well as the recently released Xavier NX SoM. It's been created by `Antmicro <https://antmicro.com>`_, a custom hardware, software and AI engineering company and a Jetson ecosystem partner of `NVIDIA <https://nvidia.com>`_.
The board can be interfaced with MIPI CSI-2 video devices through a unified Flexible Flat Cable (FFC) connector, supporting up to 4 sensors in a 2-lane configuration or 3 sensors in a 4-lane configuration.
Please refer to the ``Jetson Nano OEM Product Design Guide`` for more details regarding the supported CSI lane mappings.

Repository structure:
---------------------

The main repository directory contains the Altium PCB project file, the Outjob file, LICENSE and README.
The remaining files are stored in the following directories:

* ``PCB`` -  contains all Altium design files
* ``Libraries`` - contains the component libraries
* ``Documentation`` - contains selected files for device fabrication (schematic in PDF, BoM) generated from the Altium project
* ``Images`` - contains graphics for this README
* ``3DModels`` - contains files defining the `mechanical model <3DModels/Jetson_Nano_Baseboard-Rev.1.4.2.stl>`_ of the assembled board

Key features
============

* Jetson Nano / Xavier NX SO-DIMM connector
* Gigabit Ethernet RJ45 connector
* Micro USB debug connector
* USB-C DFP (Host) port
* Mini HDMI video output interface
* Mini DisplayPort video output interface
* 2x 50-pin FFC connectors exposing up to 4 MIPI CSI-2 camera interfaces
* M.2 (key M) connector exposing PCIe x4 interface
* RTC battery backup
* EEPROM for storing board ID/SN

The PCB project files were prepared in Altium Designer 14.1.

Board layout & dimensions
=========================

The picture below presents a general layout of the PCB with marked I/O interfaces.

.. figure:: Images/jetson-nano-layout.png

Getting started
===============

The board can be produced and assembled using the provided design files.
Please take a look at the mechanical layers for more information regarding the PCB stackup recommended for fabrication.
The board can be powered by a voltage in the 6-36VDC range.
It is recommended to use a 12V 2A DC supply to power the board.
The board has an integrated power sequencer that starts the module automatically right after applying power supply.

Debug UART connection
---------------------

Most of the debug messages are provided through the serial console.
The board is equipped with an FTDI chip providing the UART interface to the host PC.
Please refer to the schematic sheets for more details.
The default debug UART channel is accessible through ``/dev/ttyUSB0`` (assuming that there are no other FTDI units connected to your PC).
The default baudrate for serial debug connection is 115200 baud with an 8-bit transmission, 1 stop bit and with no flow control.

Revision info
=============

The latest revision of the PCB includes the following changes and amendments:

* Introduced an 8-layer PCB stackup for a better separation of PCIe lanes
* Rotated the M.2 connector by 180 degrees to keep it away from the on-board DC/DC
* Changed the stacking height of the M.2 connector
* Simplified the M.2 supporting circuitry
* Exposed the ``CSI-G`` and ``PCIE1`` interfaces on the `Jetson Xavier NX <https://developer.nvidia.com/embedded/jetson-xavier-nx>`_
* Updated FAN control circuitry
* Changed GPIO assignment for camera-triggering signals
* Optimized board cutout for the DisplayPort connector
* Fine-tuned selected footprints to improve the reliability of the reflow soldering
* Changed power sequencing of the on-board DC/DC converters
* Fixed ``TPD8S009`` footprint
* Removed MicroSD card socket
* Updated ``USBC_VBUS`` control circuitry
* Added EEPROM for SN/ID storage

Please check the `releases <https://github.com/antmicro/jetson-nano-baseboard/releases>`_ for a brief summary of major changes introduced in previous revisions.

License
=======

`MIT <LICENSE>`_
