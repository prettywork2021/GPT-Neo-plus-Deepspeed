# GPT-Neo-plus-Deepspeed
I wanted to run GPT-Neo on my computer, but running it on CPU is too slow and my gpu doesn't have enough ram, so i used Deepspeed.

It requires around 22 GB of ram to load GPT-Neo 2.7B model, but after model loads into ram, you can run gc and it will drop to around 10GB, plus depending on amount of ram your GPU has, it will drop further to 10GB-GPU ram GB.

I only tested it on my GTX-1070 8GB, so i don't know if it will work on other gpu's.

In Deepspeed docs it also said that you can load very big model directly from NVME device, but as i have no NVME, i can't test or implement it.

Update:
After testing it some more, i've concluded that there is not much sense to use my script if you have more than 5 GB of VRAM, as you just need to model.half() to make GPT-Neo 2.7B run. Though if you have less VRAM, or would want to run larger model than 2.7B parameters, my script will be useful.
