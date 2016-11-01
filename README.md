# DeepKnowledgeTracing

source code for the paper Deep Knowledge Tracing. http://stanford.edu/~cpiech/bio/papers/deepKnowledgeTracing.pdf

At the moment the code doesn't include LSTM model, only RNN (I will upload LSTM when I get a chance).

Questions people have asked me:
----------
```
Q. How do you handle multiple students during training? It looks like sequences (ie. data of different 
students) of different length are padded to the same length.
A. Correct. This is very important for training speed.
```

```
Q. Does the training code have a termination condition?
A. No. I save a copy of the model each epoch and let training run until I feel like terminating it. You can 
start training 
from any saved model (where you left off).
```

如何使用：（ubuntu下）
安装luarocks
```
sudo apt-get install luarocks
```
安装csvigo(必须先装Torch：http://torch.ch/)
```
git clone https://github.com/torch/distro.git ~/torch --recursive
cd ~/torch

# clean old torch installation
./clean.sh
# optional clean command (for older torch versions)
# curl -s https://raw.githubusercontent.com/torch/ezinstall/master/clean-old.sh | bash

# https://github.com/torch/distro : set env to use lua
TORCH_LUA_VERSION=LUA53 ./install.sh
source ~/.bashrc
sudo chown -R $(whoami) ~/.cache
luarocks install csvigo
luarocks install class
luarocks list
```

运行：
```
lua trainAssist.lua <fileId>
```