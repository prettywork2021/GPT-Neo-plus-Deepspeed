# GPT-Neo-plus-Deepspeed
I didn't knew i could do model.half(), so i made this... Well, on the bright side, it might help someone. 


I use deepspeed's offload optimizer and parameters offload to run GPT-Neo with GPU.
https://www.deepspeed.ai/

It requires around 20 GB to 25 GB of ram to load GPT-Neo 2.7B model, but after model loads into ram, you can run gc and it will drop to around 10GB, plus depending on amount of ram your GPU has, after initializing deepspeed, your usage of CPU RAM will drop further.

I only tested it on my GTX-1070 8GB, so i don't know if it will work on other gpu's.

In Deepspeed docs it also said that you can load very big model directly from NVME device, but as i have no NVME, i can't test or implement it, though it should be fairly straigtforward. https://www.deepspeed.ai/docs/config-json/#parameter-offloading 

To test how fast it is i use 200 token prompt and 50 token to generate.
- Using 4 Core I5 7500 CPU: 51.8 seconds
- Using Deepspeed: 17 seconds
- Using model.generate() with fully loaded model to VRAM: 3.35 seconds

Deepspeed is 3 times faster than just CPU, though 5 times slower than fully loaded model. It might be because my generate function is inefficient.


There is not much sense to use my script if you have more than 6 GB of VRAM, as you just need to model.half() and model.cuda() to make GPT-Neo 2.7B run. Though if you have less VRAM, or would want to run larger model than 2.7B parameters, my script could be useful.
