# GPT-Neo-plus-Deepspeed
I wanted to run GPT-Neo on my computer, but running it on CPU is too slow and my gpu doesn't have enough ram, so i used Deepspeed.
It requires around 22 GB of ram to load GPT-Neo 2.7B model, but after model loads into ram, you can run gc and it will drop to around 10GB, plus depending on amount of ram your GPU has, it will drop further to 10GB-GPU ram GB.
I only tested it on my GTX-1070 8GB, so i don't know if it will work on other gpu's.
