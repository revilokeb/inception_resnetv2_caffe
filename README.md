# inception_resnetv2_caffe
Training the inception resnet v2 architecture in caffe

Here I try training the inception-resnet-v2 architecture first published in http://arxiv.org/abs/1602.07261 on the full ILSVRC12 dataset using the Caffe framework.

The ILSVRC dataset has been prepared with Caffe helper tools such as create_data.sh (using convert_imageset) and is broadly following the steps explained in http://caffe.berkeleyvision.org/gathered/examples/imagenet.html. The entire training and validation images are resized to 328x328 pixels and appropriate lmdbs are created.

I am using train_val adapted from https://github.com/soeaver/caffe-model, the actually used train_val file can be found here: https://gist.github.com/revilokeb/ab1809954f69d6d707be0c301947b69e

The solver aims to be as close as possible to the description in http://arxiv.org/abs/1602.07261, the one I am currently using can be found here: https://gist.github.com/revilokeb/b6c10197898662ed83832ee871da4528

For the time being I have set aside 2 12GB GPUs to work in parallel for that experiment. 10 epochs can be trained with that setup in a little less than 5 days. A look at http://arxiv.org/abs/1602.07261 their figure 24 and 26 shows that after around 120 epochs top-1 and top-5 validation error does not seem to improve much further. So with the current setup roughly 60 days of training will be needed before reaching the final accuracy (if everything goes well).

Intermediate snapshots I will put to the following folder for anyone who is interested for download (every 10 epochs): https://drive.google.com/open?id=0B1qLpHDbczM2bTZyeHc0TmNoanM. If I am losing my patience along the way others might continue with that experiment :-).

Currently I am after epoch 10 and validation error and training loss have been developing as follows:
![Alt text](./inception_resnetv2_10epochs.png?raw=true "Current Validation Error / Training Loss")

