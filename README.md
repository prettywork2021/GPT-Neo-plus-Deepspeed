# GPT-Neo-plus-Deepspeed

I have tried to use deepspeed zero offloading (https://www.deepspeed.ai/tutorials/zero-offload/) to run GPT-Neo with small VRAM gpu's. Sadly, it didn't work. My previous tests, were incorrect. I may try other methods in the future, but for now my solution doesn't work. ¯\\_(ツ)_/¯

If you want to play with GPT-Neo, you can use https://colab.research.google.com/github/finetuneanon/gpt-neo_dungeon/blob/master/gpt-neo_dungeon.ipynb

Update 08.05.2021:
I have tried to make model run on GPU using model sharding.
GPTNeo after embedding uses blocks of attention of the same size that could be easily divided, loaded, used and unloaded when needed.
It worked, but because of slow data transfer between GPU and CPU, and linear nature of text generation of GPTNeo, any speedups from using gpu are nonexistend compared to time it takes to load and unload parameters.
I only used methods of transfer provided by Pytorch, so that might be why it was so slow.
I might look at some data transfer techniques to speedup transfer, but i doubt that it will do any major difference.

Update 13.05.21
arrmansa had the same idea as i, but managed to do better. Here is his work if you want to try: https://github.com/arrmansa/Gpt-Neo-Limited-Vram-Cuda
