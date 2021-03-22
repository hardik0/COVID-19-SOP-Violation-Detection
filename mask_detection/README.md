<a id="mask_detection_"></a>
# Face Mask Detection
It detects whether people have wore a mask properly or not.

<img src="mask_detection/GIFs/useless_mask.gif" width="400"/>   <img src="mask_detection/GIFs/useless_mask2.gif" width="400"/>
<img src="mask_detection/GIFs/no_mask.gif" width="400"/>   <img src="mask_detection/GIFs/thanks_mask.gif" width="400"/>

## Requirements
We used these packages/versions in the development of this project. It is likely that higher versions of the same package will also work. This is not an exhaustive list -- other common python packages (e.g. pillow) are expected and not listed.

- Tensorflow '2.4.1'
- OpenCV '4.2.0'
- ffmpeg
- sklearn, matplotlib, numpy, tqdm

Refer to the official [TensorFLow guide](https://www.tensorflow.org/install>) for installing Tensorflow. The rest can be installed by:

```
$ pip install opencv-python python3-opencv numpy matplotlib scikit-learn imutils tqdm ffmpeg
```

## Quick start - Inference
To run inference on video example:
```bash
$ python real_time_mask_detection.py --video_input mask.mp4  # 0 for webcam
                                     --save_video mask_output.avi 
                                     --fps 10
                                     --model  # optional - path to trained face mask detector model, default="mask_detector.model"
                                     --confidence  # optional -minimum probability to filter weak detections, default=0.5                                
```
## Training

### Data preparation

Datasets should be arranged as the following layout.

```bash
├── dataset
│   ├── Useless_Mask
│   │   ├── 00001.png
│   │   ├── 00002.png
│   │   ├── ...
│   ├── Mask
│   │   ├── 00001.png
│   │   ├── 00002.png
│   │   ├── ...
│   ├── No_Mask
│   │   ├── 00001.png
│   │   ├── 00002.png
│   │   ├── ...
└───└─── 
```
### Training commands
```
$ python train_mask_detector.py --dataset dataset
```
## Dataset Citation
> Adnane Cabani, Karim Hammoudi, Halim Benhabiles, and Mahmoud Melkemi, "MaskedFace-Net - A dataset of correctly/incorrectly masked face images in the context of COVID-19", Smart Health, ISSN 2352-6483, Elsevier, 2020, <a href=https://doi.org/10.1016/j.smhl.2020.100144>DOI:10.1016/j.smhl.2020.100144</a> 

```
@Article{cabani.hammoudi.2020.maskedfacenet,
    title={MaskedFace-Net -- A Dataset of Correctly/Incorrectly Masked Face Images in the Context of COVID-19},
    author={Adnane Cabani and Karim Hammoudi and Halim Benhabiles and Mahmoud Melkemi},
    journal={Smart Health},
    year={2020},
    url ={http://www.sciencedirect.com/science/article/pii/S2352648320300362},
    issn={2352-6483},
    doi ={https://doi.org/10.1016/j.smhl.2020.100144}
}
```
## Acknowledgements:
- For mask detection, We forked codes from [*OpenCV*](https://github.com/opencv/opencv) git repo [`dnn/face_detector`](https://github.com/opencv/opencv/tree/master/samples/dnn/face_detector) and modified it.
