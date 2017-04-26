# chinese-poem-creater
实践char-rnn

## 1.获得带torch的docker
地址：https://hub.docker.com/r/kaixhin/torch/
## 2.安装好，进入docker
apt-get update
apt-get install git 
git clone https://github.com/karpathy/char-rnn.git

    ubuntu对中文的支持
    locale -a
    export LANG="zh_CN.utf8"

    //TODO::繁体字问题还未解决
## 3.
cd char-rnn
将input文件夹的某个文件移到 data/your-floder-name

## 4.学习
th train.lua -data_dir data/your-floder-name -gpuid -1

结果如下

    3294/3300 (epoch 49.909), train_loss = 1.44961959, grad/param norm = 1.9957e-01, time/batch = 0.4320s
    3295/3300 (epoch 49.924), train_loss = 1.45700514, grad/param norm = 1.7992e-01, time/batch = 0.4353s
    3296/3300 (epoch 49.939), train_loss = 1.44030483, grad/param norm = 1.9692e-01, time/batch = 0.4467s
    3297/3300 (epoch 49.955), train_loss = 1.49928484, grad/param norm = 2.1121e-01, time/batch = 0.4377s
    3298/3300 (epoch 49.970), train_loss = 1.49634007, grad/param norm = 2.3070e-01, time/batch = 0.4322s
    3299/3300 (epoch 49.985), train_loss = 1.45957477, grad/param norm = 2.6381e-01, time/batch = 0.4482s
    decayed learning rate by a factor 0.97 to 0.00057368183755432
    evaluating loss over split index 2
    1/4...
    2/4...
    3/4...
    4/4...
    saving checkpoint to cv/lm_lstm_epoch50.00_2.0510.t7
    3300/3300 (epoch 50.000), train_loss = 1.46940195, grad/param norm = 2.5143e-01, time/batch = 0.4425s
## 5.取样
th sample.lua cv/lm_lstm_epoch50.00_2.0510.t7 -gpuid -1 -temperature 0.2
## 6.调整取样参数
temperature在0～1之间调整，越小越保守，越大越奔放
