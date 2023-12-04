===========================
Programmable Coolant Cannon
===========================

**Work In Progress**

Probe Basic includes a subroutine (``program_coolant.ngc``) for an auto aiming coolant cannon.
The stock subroutines include calls to the routine after M6 tool changes and "Load spindle".

``o<program_coolant> call`` uses ``motion.analog-out-20`` via ``M68 E20 Q[#<coolant_final_angle>]`` to pass the calculated angle out to the hal.


Settings
~~~~~~~~
Unfortunately the settings must be done via the INI file, though they are displayed for reference on the UI SETTINGS tab.

ACTIVATE:
    0 or 1 to enable or disable the programmable coolant cannon
HORIZONTAL_SPINDLE_NOZZLE_DIST:
    Spindle centerline to nozzle centerline distance (machine units mm/inch)
VERTICAL_SPINDLE_NOZZLE_DIST:
    Nozzle centerline to spindle gauge line (machine units mm/inch)
PC_ANGLE_OFFSET:
    Nozzle angle offset adjustment (degrees)


[COOLANT_CANNON] Section
~~~~~~~~~~~~~~~~~~~~~~~~
Add the following ``[COOLANT_CANNON]`` section to your machine INI file.

.. code:: ini

    [COOLANT_CANNON]
    # Coolant Cannon Settings for auto coolant aiming, these are used by o<program_coolant>
    # Activate Programmable Coolant
    ACTIVATE = 1
    # Spindle centerline to nozzle centerline distance (machine units mm/inch)
    HORIZONTAL_SPINDLE_NOZZLE_DIST = 8
    # Nozzle centerline to spindle gauge line (machine units mm/inch)
    VERTICAL_SPINDLE_NOZZLE_DIST = 4
    # Nozzle angle offset (degrees)
    PC_ANGLE_OFFSET = 0

[HAL] Section
~~~~~~~~~~~~~
Add the following additional ``HALFILE`` line to the ``[HAL]`` section to your machine INI file.

.. code:: ini

    [HAL]
    ...
    HALFILE = collant_cannon.hal
    ...

HAL Setup
~~~~~~~~~
Edit the ``coolant_cannon.hal`` file as need to connect the cannon to you machine outputs

``coolant_cannon.hal``
``motion.analog-out-20``
