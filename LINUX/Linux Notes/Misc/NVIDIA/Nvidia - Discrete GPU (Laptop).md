**Configure Graphics Applications to Render Using the GPU Screen**

> To configure a graphics application to be offloaded to the NVIDIA GPU screen, set the environment variable `__NV_PRIME_RENDER_OFFLOAD` to `1`. If the graphics application uses Vulkan, that should be all that is needed. If the graphics application uses GLX, then also set the environment variable `__GLX_VENDOR_LIBRARY_NAME` to `nvidia`, so that GLVND loads the NVIDIA GLX driver. NVIDIA's EGL implementation does not yet support PRIME render offload.

`__NV_PRIME_RENDER_OFFLOAD=1 glxgears`
`__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia glxgears`
`__NV_PRIME_RENDER_OFFLOAD=1 __VK_LAYER_NV_optimus=NVIDIA_only glxgears`
`__NV_PRIME_RENDER_OFFLOAD=1 __VK_LAYER_NV_optimus=non_NVIDIA_only glxgears`

___

