<p align="center" width="100%">
<img src="assets\Meta-Transformer_banner.png"  width="80%" height="80%">
</p>

<div>
<div align="center">
    <a href='https://scholar.google.com/citations?hl=zh-CN&user=KuYlJCIAAAAJ/' target='_blank'>Yiyuan Zhang<sup>1,2*</sup></a>&emsp;
    <a href='https://kxgong.github.io/' target='_blank'>Kaixiong Gong<sup>1,2*</sup></a>&emsp;
    <a href='http://kpzhang93.github.io/' target='_blank'>Kaipeng Zhang<sup>2,&#x2709</sup></a>&emsp;
    </br>
    <a href='http://www.ee.cuhk.edu.hk/~hsli/' target='_blank'>Hongsheng Li <sup>1,2</sup></a>&emsp;
    <a href='https://mmlab.siat.ac.cn/yuqiao/index.html' target='_blank'>Yu Qiao <sup>2</sup></a>&emsp;
    <a href='https://wlouyang.github.io/' target='_blank'>Wanli Ouyang<sup>2</sup></a>&emsp;
    <a href='http://people.eecs.berkeley.edu/~xyyue/' target='_blank'>Xiangyu Yue<sup>1,&#x2709</sup></a>
</div>
<div>

<div align="center">
    <sup>1</sup>Multimedia Lab, The Chinese University of Hong Kong&emsp;
    </br>
    <sup>2</sup>OpenGVLab，Shanghai AI Laboratory 
    </br>
    <sup>*</sup> Equal Contribution&emsp;
    <sup>&#x2709</sup> Corresponding Author
</div>

-----------------

[![arXiv](https://img.shields.io/badge/arxiv-2307.10802-b31b1b?style=plastic&color=b31b1b&link=https%3A%2F%2Farxiv.org%2Fabs%2F2307.10802)](https://arxiv.org/abs/2307.10802)
[![website](https://img.shields.io/badge/Project-Website-brightgreen)](https://kxgong.github.io/meta_transformer/)
[![blog-cn](https://img.shields.io/badge/%E6%9C%BA%E5%99%A8%E4%B9%8B%E5%BF%83-%E7%AE%80%E4%BB%8B-brightgreen)](https://mp.weixin.qq.com/s/r38bzqdJxDZUvtDI0c9CEw)
[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Space-blue)](https://huggingface.co/papers/2307.10802)
![](https://img.shields.io/github/stars/invictus717/MetaTransformer?style=social)
<a href="https://twitter.com/_akhaliq/status/1682248055637041152"><img src="https://img.icons8.com/color/48/000000/twitter.png" width="25" height="25"></a>
<a href="https://www.youtube.com/watch?v=V8L8xbsTyls&ab_channel=CSBoard"><img src="https://img.icons8.com/color/48/000000/youtube-play.png" width="25" height="25"></a>




<p align="left">
<img src="assets\Meta-Transformer_cmp.png" width=100%>
</p>

## 🚩🚩🚩 Shared-Encoder, Unpaired Data, More Modalities 


<div>
  <img class="image" src="assets\Meta-Transformer_teaser.png" width="52%" height="100%">
  <img class="image" src="assets\Meta-Transformer_exp.png" width="45.2%" height="100%">
</div>


This repository is built to explore the potential and extensiability of transformers for multimodal learning. We utilize the advantages of Transformers to deal with length-variant sequence. Then we proposes the *Data-to-Sequence* tokenization following a meta-scheme, then we apply it to 12 modalities including text, image, point cloud, audio, video, infrared, hyper-spectral, X-Ray, tabular, graph, time-series, and Inertial Measurement Unit (IMU) data.

<p align="left">
<img src="assets\Meta-Transformer_data2seq.png" width=100%>
</p>

After obtaining the token sequence, we employ a modality-shared encoder to extract representation across different modalities. With task-specific heads, Meta-Transformer can handle various tasks on the different modalities, such as: classification, detection, and segmentation.

<p align="left">
<img src="assets\Meta-Transformer_framework.png" width=100%>
</p>



# 🌟 News
* **2023.7.23:** 🎉🎉🎉 We have released the code and pretrained weights for image understanding and time-series forcasting. 
* **2023.7.22:** 🌟🌟🌟 Pretrained weights and a usage demo for our Meta-Transformer have been released. Comprehensive documentation and implementation of the image modality are underway and will be released soon. Stay tuned for more exciting updates!⌛⌛⌛
* **2023.7.21:** Paper is released at [arxiv](https://arxiv.org/abs/2307.10802), and code will be gradually released.
* **2023.7.8:** Github Repository Initialization.

# 🔓 Model Zoo

<details>
<summary> Open-source Modality-Agnostic Models </summary>
<br>
<div>

|      Model      |   Pretraining   | Scale | #Param |                                               Download                                                |
| :------------: | :----------: | :----------------------: | :----: | :---------------------------------------------------------------------------------------------------: |
| Meta-Transformer-B16  | LAION-2B |         Base          |  85M  |   [ckpt](https://drive.google.com/file/d/19ahcN2QKknkir_bayhTW5rucuAiX0OXq/view?usp=sharing)    |
| Meta-Transformer-L14  | LAION-2B |         Large          |  302M  |   [ckpt](https://drive.google.com/file/d/15EtzCBAQSqmelhdLz6k880A19_RpcX9B/view?usp=drive_link)   |

</div>

</details>

<details>
<summary>Demo of Use for Pretrained Encoder</summary>

```python
from timm.models.vision_transformer import Block
ckpt = torch.load("Meta-Transformer_base_patch16_encoder.pth")
encoder = nn.Sequential(*[
            Block(
                dim=768,
                num_heads=12,
                mlp_ratio=4.,
                qkv_bias=True,
                norm_layer=nn.LayerNorm,
                act_layer=nn.GELU
            )
            for i in range(12)])
encoder.load_state_dict(ckpt,strict=True)
```
</details>

# 🕙 ToDo
- [ ] Meta-Transformer with Large Language Models.
- [ ] Multimodal Joint Training with Meta-Transformer.
- [ ] Support More Modalities and More Tasks.

# Contact
Welcome to contribute to our project!

To contact us, never hestitate to send an email to `yiyuanzhang.ai@gmail.com` ,`kaixionggong@gmail.com`, `zhangkaipeng@pjlab.org.cn`, or `xyyue@ie.cuhk.edu.hk`!
<br></br>

# Citation
If the code and paper help your research, please kindly cite:
```
@article{zhang2023metatransformer,
        title={Meta-Transformer: A Unified Framework for Multimodal Learning}, 
        author={Zhang, Yiyuan and Gong, Kaixiong and Zhang, Kaipeng and Li, Hongsheng and Qiao, Yu and Ouyang, Wanli and Yue, Xiangyu},
        year={2023},
        journal={arXiv preprint arXiv:2307.10802},
  }
```
# License
This project is released under the [Apache 2.0 license](LICENSE).
# Acknowledgement
This code is developed based on excellent open-sourced projects including [MMClassification](https://github.com/open-mmlab/mmpretrain/tree/mmcls-1.x), [MMDetection](https://github.com/open-mmlab/mmdetection), [MMsegmentation](https://github.com/open-mmlab/mmsegmentation), [OpenPoints](https://github.com/guochengqian/openpoints), [Time-Series-Library](https://github.com/thuml/Time-Series-Library), [Graphomer](https://github.com/microsoft/Graphormer), [SpectralFormer](https://github.com/danfenghong/IEEE_TGRS_SpectralFormer), and [ViT-Adapter](https://github.com/czczup/ViT-Adapter).