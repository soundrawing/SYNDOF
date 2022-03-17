## SYNDOF (Synthetic Defocus Blur Image Dataset)
![Matlab](https://img.shields.io/badge/matlab-9.3.0-green.svg?style=plastic)
![License CC BY-NC](https://img.shields.io/badge/license-GNU_AGPv3-green.svg?style=plastic)

![Teaser image](./assets/figure.png)
**Picture:** *Outputs generated from our code&ndash; from left to right, synthetic input, defocus map output and defocused image.*

This repository contains the official matlab implementation of SYNDOF generation used in the following paper:

> **[Deep Defocus Map Estimation using Domain Adaptation](https://openaccess.thecvf.com/content_CVPR_2019/papers/Lee_Deep_Defocus_Map_Estimation_Using_Domain_Adaptation_CVPR_2019_paper.pdf)**<br>
> Junyong Lee, Sungkil Lee, Sunghyun Cho, and Seungyong Lee<br>
> *IEEE Computer Vision and Pattern Recognition (**CVPR**) 2019*
> [Paper](https://openaccess.thecvf.com/content_CVPR_2019/papers/Lee_Deep_Defocus_Map_Estimation_Using_Domain_Adaptation_CVPR_2019_paper.pdf) \| [Supp](https://www.dropbox.com/s/van0beau0npq3de/supp.zip?dl=1) \| [DMENet Repo](https://github.com/codeslake/DMENet)


## Getting Started

### Prerequisites
* Download and unzip the synthetic datasets ([Google Drive](https://drive.google.com/open?id=1Tc15GlwA-jr5EoXPwSmz2yG6IhxaK_Ji&authuser=codeslake%40gmail.com&usp=drive_fs) \| [Dropbox](https://www.dropbox.com/s/bymkyss5rtn6avl/synthetic_datasets.zip?dl=1)) under `./data`:
    ```
    ├── data
    │   ├── synthetic_datasets
    │   │   ├── ...
    ```

## SYNDOF Generation
* On matlab console, type
    ```bash
    # max_coc, input_offset, output_offset, is_random_gen, is_gpu, gpu_num
    generate_blur_by_depth(29, 'data', 'out', false, true, 1)
    ```

* check the results under `./out`, which is structured as,
    ```
    ├── ...
    ├── out
    │  ├── blur_map/                    # directory for output defocus map
    │  ├── blur_map_binary/             # directory for binarized defocus map
    │  ├── blur_map_norm/               # directory for normalized defocus map
    │  ├── depth_decomposed/            # directory for decomposed depth
    │  ├── image/                       # directory for input image (with its modified name)
    ```

## Reading SYNDOF
* We rounded real values of defocus map into the nearest 10-th. When you read a defocus map, for example in python, read the file as follows:
    ```bash
    image = (np.float32(cv2.imread(file_name, cv2.IMREAD_UNCHANGED))/10.)[:, :, 1]
    image = image / 7. # 7 = (maxCoC - 1) / 4, where maxCoC is 29 in this case.
    ```

## Contact
Open an issue for any inquiries.
You may also have contact with [junyonglee@postech.ac.kr](mailto:junyonglee@postech.ac.kr)

## License
This software is being made available under the terms in the [LICENSE](LICENSE) file.

Any exemptions to these terms require a license from the Pohang University of Science and Technology.

## Citation
If you find this code useful, please consider citing:

```
@InProceedings{Lee_2019_CVPR,
    author = {Lee, Junyong and Lee, Sungkil and Cho, Sunghyun and Lee, Seungyong},
    title = {Deep Defocus Map Estimation Using Domain Adaptation},
    booktitle = {IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    month = {June},
    year = {2019}
}
```

