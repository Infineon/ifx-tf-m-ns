# Infineon Customized Trusted Firmware-M for Non-Secure project

## Overview
Trusted Firmware-M (TF-M) implements the Secure Processing Environment (SPE)
for Arm Cortex-M based platforms. This aligns the reference implementation of the platform security architecture
with the PSA Certified guidelines. Thus, TF-M allows relevant chips and devices to become PSA Certified.

This library contains Trusted Firmware-M (TF-M) for non-secure projects. Use the ifx-tf-m
library to build a TF-M secure project.

## Licensing
This software component is licensed under a mixture of the Apache License,
version 2 and the 3-Clause BSD License. See separate files to
determine which license applies. Note the licensing of the
following modules:
* [t_cose LICENSE](https://github.com/laurencelundblade/t_cose/blob/master/LICENSE)
* [QCBOR LICENSE](https://github.com/laurencelundblade/QCBOR/blob/master/LICENSE)

## Usage of TF-M in the ModusToolbox™ tools package
### Usage of TF-M in non-secure applications
To use the TF-M secure image functionality in non-secure applications:
1. Set up and build a TF-M secure application. See the ifx-tf-m library README.md for more
   details.
2. Add the ifx-tf-m-ns library to your non-secure project.
3. The code used to bind a non-secure project with TF-M is generated during the TF-M secure
   project build into folder `TFM_INSTALL_PATH`.

### Enabling and initializing NSPEs
Infineon TF-M platforms have at least one non-secure processing environment
(NSPE). Some platforms also support additional NSPEs.

For the common TF-M non-secure interface requirements, including how the NSPE
interfaces with TF-M and NS interface initialization, refer to
[Interface with TF-M](https://trustedfirmware-m.readthedocs.io/en/latest/integration_guide/index.html#interface-with-tf-m).

On platforms with additional NSPEs, the primary NSPE may be responsible for
enabling additional NSPEs and can also act as a proxy for their PSA and SRF
requests. When an additional NSPE is present, its communication layer must be
initialized before issuing PSA or SRF calls. Depending on the platform, this
may happen in startup code such as `cybsp_init()`.

On platforms without SRF support, non-secure startup code must not access
peripherals that are configured as secure-only by TF-M. On such platforms,
startup code that touches protected registers such as clock, power, or
protection configuration registers must remain disabled or be adapted to avoid
secure access violations.

### Further instructions
For more info and configuration options,
see README.md provided by the ifx-tf-m library.

For the general TF-M documentation, refer to
[TF-M user guide](https://trustedfirmware-m.readthedocs.io/en/latest/index.html).

## More information
Use the following links for more information:
* [Cypress Semiconductor Corporation (an Infineon company)](https://www.infineon.com)
* [Cypress Semiconductor Corporation (an Infineon company) GitHub](https://github.com/Infineon)
* [Trusted Firmware website](https://www.trustedfirmware.org)
* [TF-M project](https://www.trustedfirmware.org/projects/tf-m)
* [PSA API](https://arm-software.github.io/psa-api)
* [ModusToolbox™ Software Environment, Quick Start Guide, Documentation, and Videos](https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software)

---
© 2023-2026, Infineon Technologies AG, or an affiliate of Infineon
Technologies AG. All rights reserved.
This software, associated documentation and materials ("Software") is
owned by Infineon Technologies AG or one of its affiliates ("Infineon")
and is protected by and subject to worldwide patent protection, worldwide
copyright laws, and international treaty provisions. Therefore, you may use
this Software only as provided in the license agreement accompanying the
software package from which you obtained this Software. If no license
agreement applies, then any use, reproduction, modification, translation, or
compilation of this Software is prohibited without the express written
permission of Infineon.

Disclaimer: UNLESS OTHERWISE EXPRESSLY AGREED WITH INFINEON, THIS SOFTWARE
IS PROVIDED AS-IS, WITH NO WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING, BUT NOT LIMITED TO, ALL WARRANTIES OF NON-INFRINGEMENT OF
THIRD-PARTY RIGHTS AND IMPLIED WARRANTIES SUCH AS WARRANTIES OF FITNESS FOR A
SPECIFIC USE/PURPOSE OR MERCHANTABILITY.
Infineon reserves the right to make changes to the Software without notice.
You are responsible for properly designing, programming, and testing the
functionality and safety of your intended application of the Software, as
well as complying with any legal requirements related to its use. Infineon
does not guarantee that the Software will be free from intrusion, data theft
or loss, or other breaches ("Security Breaches"), and Infineon shall have
no liability arising out of any Security Breaches. Unless otherwise
explicitly approved by Infineon, the Software may not be used in any
application where a failure of the Product or any consequences of the use
thereof can reasonably be expected to result in personal injury.
