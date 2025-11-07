GRUB_CMDLINE_LINUX_DEFAULT - Options:

mitigations=off			- Control optional mitigations for CPU vulnerabilities.
verbose					- Debugging mode

libata.noacpi=1			- Disables use of ACPI in libata suspend/resume when set.
acpi=force				- force -- enable ACPI if default was off.
nosgx					- Disables Intel SGX kernel support.
acpi=off					- off -- disable ACPI if default was on.
apm=off (power_off)		- Advanced Power Management
mce=off					- Machine Check Exception
nomce					- Disable Machine Check Exception
loglevel=3
reboot=acpi
powersave=off			- This option disables power saving features.
ipv6.disable=1

nomodeset - Добавление параметра nomodeset инструктирует ядро, что не надо загружать драйверы видео до момента, пока не будет загружена графическая система X. В результате система загружается в текстовом виде, можно видеть сообщения процесса загрузки, проблема "черного экрана загрузки" устраняется.

___

# Description

GDS can also be mitigated on systems that don't have updated microcode by disabling AVX. This can be done by setting gather_data_sampling="force" or "clearcpuid=avx" on the kernel command-line.

The mitigation can be disabled by setting "gather_data_sampling=off" or "mitigations=off" on the kernel command line. Not specifying either will default to the mitigation being enabled.

Specifying "gather_data_sampling=force" will use the microcode mitigation when available or disable AVX on affected systems where the microcode hasn't been updated to include the mitigation.