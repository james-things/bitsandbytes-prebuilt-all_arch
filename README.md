# bitsandbytes-prebuilt-all_arch

## About

This repository contains builds of the bitsandbytes library compiled with the "all" option for GPU architecture support. They are useful if you are running into issues running bitsandbytes on older Nvidia GPUs. In theory, support exists for Kepler, Maxwell, Pascal, Volta, and newer GPUs. This was built and tested on Pascal however, so no guarantees.

I am not sure that there is any point to the WSL .so, however learning to build it was useful. Please see the credit below with regard to the Windows build; while I toiled over this for a while, the user below provided the method and CMake scripts. Hopefully this compiled dll saves someone else many hours of fighting with dependencies and scouring the internet for information!

## Using with SD Dreambooth Extension

To use this with the SD Dreambooth Extension for Automatic's WebUI on Windows: 

* Navigate to ```<sd-install>\extensions\sd_dreambooth_extension\bitsandbytes_windows```
* Place the dll file from this repository alongside the other dll file, such that ```libbitsandbytes_cudaall.dll``` is in the same folder as ```libbitsandbytes_cuda116.dll```
* Open ```main.py``` in the same folder and find line 118: ```    return "libbitsandbytes_cuda116.dll"            ```
* Replace it with: ```    return "libbitsandbytes_cudaall.dll"            ```
* Fully restart your SD and you should be in business! If in doubt about settings to not go OOM, check the screen cap below, they are printed out.

*Note: To be clear, the purpose of this dll is to be able to use bitsandbytes under Windows running Pascal and potentially other architecture cards.*

## Training Dreambooth on 1080Ti under Windows! 

![working-finally](https://user-images.githubusercontent.com/71165873/204723173-d16ea596-ad84-4403-a375-7dea895a31ae.png)

## Windows Build Credit 

Thank you to this gracious github user who provided CMake scripts that finally unblocked things on this: https://github.com/TimDettmers/bitsandbytes/issues/30#issuecomment-1330951753
