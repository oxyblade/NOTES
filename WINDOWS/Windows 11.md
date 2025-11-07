
> **Install without TPM, CPU, RAM Requirements**
> SHIFT+F10
> regedit
> Computer\HKEY_LOCAL_MACHINE\SYSTEM\Setup => New > Key -> LabConfig
> 
> Add DWORD (32-bit):
> BypassTPMCheck - 1
> BypassSecureBootCheck - 1
> BypassRAMCheck - 1

> **Skip Microsoft Account during installation**
> SHIFT+F10 -> oobe\bypassnro