# inception_resnetv2_caffe
Training the inception resnet v2 architecture in caffe

Here I try training the inception-resnet-v2 architecture first published in http://arxiv.org/abs/1602.07261 on the full ILSVRC12 dataset using the Caffe framework.

The ILSVRC dataset has been prepared with Caffe helper tools such as create_data.sh (using convert_imageset) and is broadly following the steps explained in http://caffe.berkeleyvision.org/gathered/examples/imagenet.html. The entire training and validation images are resized to 328x328 pixels and appropriate lmdbs are created.

I am using train_val adapted from https://github.com/soeaver/caffe-model, the actually used train_val file can be found here: https://gist.github.com/revilokeb/ab1809954f69d6d707be0c301947b69e

The solver aims to be as close as possible to the description in http://arxiv.org/abs/1602.07261, the one I am currently using can be found here: https://gist.github.com/revilokeb/b6c10197898662ed83832ee871da4528

For the time being I have set aside 2 12GB GPUs to work in parallel for that experiment. 10 epochs can be trained with that setup in a little less than 5 days. A look at http://arxiv.org/abs/1602.07261 their figure 24 and 26 shows that after around 120 epochs top-1 and top-5 validation error does not seem to improve much further. So with the current setup roughly 60 days of training will be needed before reaching the final accuracy (if everything goes well).

Intermediate snapshots I will put to the following folder for anyone who is interested for download (every 10 epochs): https://drive.google.com/open?id=0B1qLpHDbczM2bTZyeHc0TmNoanM. If I am losing my patience along the way others might continue with that experiment :-).

Currently I am right after epoch 25 and validation error and training loss have been developing as follows:
![Alt text](./inception_resnetv2_25epochs.png?raw=true "Current Validation Error / Training Loss")

A closer look at the validation error of the last 10 epochs reveals that there has been no noticeable change in validation error over the last 10 epochs. ![Alt text](./inception_resnetv2_15-25epochs.png?raw=true "Validation Error / Training Loss of last 10 epochs")

Obviously validation accuracy is very much different from what is shown in http://arxiv.org/abs/1602.07261 (e.g. their Figure 24, Top-5 validation error at 20 epochs showing ~10% error as compared with ~28% in my training). I have strictly adhered to the learning rate schedule described in the paper (learning rate @ start of training: 0.045 and reducing learning rate every 2 epochs by factor of 0.94). In one additional experiment I have lowered the learning rate manually after 10 epochs by multiplying it with 0.2 which resulted in an improvement of Top-1 / Top-5 validation accuracy of 2.5% / 3%.

As it does not seem to be possible to directly reproduce results shown in http://arxiv.org/abs/1602.07261 with my setup I will go back and re-analyze my setup first. Also I might consider investigating the architecture on smaller images / different image set (e.g. CIFAR 100). 



