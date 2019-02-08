# Flops counter for convolutional networks in pytorch framework

Requirements: Pytorch 0.4.1 or 1.0, torchvision 0.2.1

Thanks to @warmspringwinds for the initial version of script.

Supported layers:
- Convolution2d (including grouping)
- BatchNorm2d
- Activations (ReLU, PReLU, ELU, ReLU6, LeakyReLU)
- Linear
- Upsample
- Poolings (AvgPool2d, MaxPool2d and adaptive ones)

## Example
```python
import torchvision.models as models
import torch
from flops_counter import get_model_complexity_info

with torch.cuda.device(0):
  net = models.densenet161()
  flops, params = get_model_complexity_info(net, (224, 224), as_strings=True, print_per_layer_stat=True)
  print('Flops:  {}'.format(flops))
  print('Params: ' + params)
```
