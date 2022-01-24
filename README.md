# mkinitcpio-rclocal

Simple mkinitcpio hook to allow an arbitrary script to be executed at each
stage of runtime hook execution. The name of the script for each hook stage
must be specified in mkinitcpio.conf.

- `rclocal_earlyhook` specifies the path to a script which will be run in the
  "early hook" stage.

- `rclocal_hook` specifies the path to a script which will be run in the
  ordinary "hook" stage.

- `rclocal_latehook` specifies the path to a script which will be run in the
  "late hook" stage.

- `rclocal_cleanup` specifies the path to a script which will be run in the
  "cleanup hook" stage.

If any of these variables are defined, the scripts they name will be copied
into the initramfs and the corresponding hooks of this module will run them. It
is an error to define any of these variables to a non-existent file.

Each script copied into the initramfs will have its mode set to `0755`.

The scripts are *not* intended to be compiled executables; the hook
installation script will not attempt to resolve shared library dependencies.
