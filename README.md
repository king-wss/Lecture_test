## 환경설정

* [Ubuntu](./doc/environment/ubuntu.md)
* [OpenVINO](./doc/environment/openvino.md)


## Team projects
### 제출방법

1) 팀구성 및 프로젝트 세부 논의 후, 각 팀은 프로젝트 진행을 위한 Github repository 생성

2) doc/project/README.md을 각 팀이 생성한 repository의 main README.md로 복사 후 팀 프로젝트에 맞게 수정 활용

3) 과제 제출시  Github repository에 New Issue 생성. 생성된 Issue에 하기 내용 포함되어야 함.

* Team name : Project Name
* Project 소개
* 팀원 및 팀원 역활
* Project Github repository
* Project 발표자료 업로드

4) 강사가 생성한 Milestone에 생성된 Issue에 추가

### 평가방법
* AI관련주제/발표의적정성/결과물의 완성도
* 제출현황
* Team: 뭔가 센스있는 팀명
* <프로젝트 요약>

### 조이름 : 열어조(OpenHAEJO)
Members
| Name           | Role |
|-------------------------------|---------------------------|
| 정우택 | Project lead & Hardware Developer, 프로젝트를 총괄 및 하드웨어 기능을 구현한다. |
| 구주헌 | AI modeling, 원하는 결과가 나오도록 AI model을 선택, data 수집, training을 수행한다. |
| 권유진 | AI-Server Integration, Server와 AI를 API로 연결한다. |
| 유광재 | Hardware-Server Integration, Server와 Hardware를 API로 연결한다. |
| 이유진 | Server Developer, 메인 서버를 구축하고 주요 동작을 처리한다. |
| Project Github | https://github.com/almondgood/Parking-System.git |


발표자료링크 : https://docs.google.com/presentation/d/1f0T8nzyZyzef_sXEHWZz7itwPSuAShLs/edit#slide=id.p1


### 조이름 : 도와조
Members
| Name           | Role |
|-------------------------------|---------------------------|
| 유재욱 | Project lead, 프로젝트를 총괄하고 망하면 책임진다. |
| 김민환 | Project manager, 프로젝트 진행상황을 전체적으로 관리한다. |
| 오현창 | Architect, 프로젝트의 component를 구성하고 상위 디자인을 책임진다. |
| 이수빈 | AI modeling, 원하는 결과가 나오도록 AI model을 선택, data 수집, training을 수행한다. |
| 이재경 | UI design, 사용자 인터페이스를 정의하고 구현한다. |
| Project Github | https://github.com/jwbastion/DOWAZO.git |


발표자료링크 : https://github.com/jwbastion/DOWAZO/blob/main/DOWAZO.pptx


### 조이름 : 어린이 보호해줘
Members
| Name           | Role |
|-------------------------------|---------------------------|
| 이인혁 | Project lead, 프로젝트를 총괄하고 망하면 책임진다. |
| 장민영 | Project manager, 마일스톤을 생성하고 프로젝트 이슈 진행상황을 관리한다. |
| 한민규 | UI design, 사용자 인터페이스를 정의하고 구현한다. |
| 이병찬 | AI modeling, 원하는 결과가 나오도록 AI model을 선택, data 수집, training을 수행한다. |
| 신혜원 | Architect, 프로젝트의 component를 구성하고 상위 디자인을 책임진다. |
| Project Github | https://github.com/LIH00/Let-s_go/edit/main/README.md |

발표자료링크 : https://github.com/LIH00/Let-s_go/blob/main/project/tempo.pptx

### 조이름 : The first 
Members
| Name           | Role |
|-------------------------------|---------------------------|
| 김용기 | Project lead, 프로젝트 총괄|
| 나준환 | Project manager, 모델 개발및 응용 |
| 이민규 | Project manager, 모델 개발및 응용 |
| 최원빈 | Project manager, 모델 개발및 응용 |
| Project Github | https://github.com/K-DRAGON-FORCE/The-first.git |

=======
발표자료 링크 :https://github.com/K-DRAGON-FORCE/The-first/blob/main/The_first_presentation.pptx

# openvino

## Open Model Zoo
https://github.com/openvinotoolkit/open_model_zoo

This repository includes optimized deep learning models and a set of demos to expedite development of high-performance deep learning inference applications. Use these free pre-trained models instead of training your own models to speed-up the development and production deployment process.

- [Intel Pre-Trained Models](https://github.com/openvinotoolkit/open_model_zoo/blob/master/models/intel/index.md)
- [Public Pre-Trained Models](https://github.com/openvinotoolkit/open_model_zoo/blob/master/models/public/index.md)
- [Model Downloader](https://github.com/openvinotoolkit/open_model_zoo/blob/master/tools/model_tools/README.md) and other automation tools
- [Demos](https://github.com/openvinotoolkit/open_model_zoo/blob/master/demos/README.md) that demonstrate models usage with OpenVINO™ Toolkit

### License
Open Model Zoo is licensed under [Apache License Version 2.0](https://github.com/openvinotoolkit/open_model_zoo/blob/master/LICENSE).

### Online Documentation
- [Pre-Trained Models](https://docs.openvino.ai/2023.0/model_zoo.html#)
- [Demos and Samples](https://docs.openvino.ai/2023.0/omz_demos.html)

### Installation
1. Download Open Model Zoo
```sh
git clone --recurse-submodules https://github.com/openvinotoolkit/open_model_zoo.git
```
2. Install Required packages
```sh
sudo apt install libopencv-dev
cd open_model_zoo
python3 -m venv omz_venv
source omz_venv/bin/activate
python3 -m pip install --upgrade pip
pip install openvino openvino-dev
pip install tensorflow
pip install torch
pip install onnx
pip install torchvision
pip install -r demos/requirements.txt
pip install protobuf==3.20.0
```
3. Modify code to replace GStreamer with V4L2 as webcam backbone
```diff
diff --git a/demos/common/cpp/utils/src/images_capture.cpp b/demos/common/cpp/utils/src/images_capture.cpp
index 8a205fc64..fefcb1463 100644
--- a/demos/common/cpp/utils/src/images_capture.cpp
+++ b/demos/common/cpp/utils/src/images_capture.cpp
@@ -240,7 +240,7 @@ public:
             throw std::runtime_error("readLengthLimit must be positive");
         }
         try {
-            if (cap.open(std::stoi(input))) {
+            if (cap.open(std::stoi(input), cv::CAP_V4L2)) {
                 this->readLengthLimit = loop ? std::numeric_limits<size_t>::max() : readLengthLimit;
                 cap.set(cv::CAP_PROP_BUFFERSIZE, 1);
                 cap.set(cv::CAP_PROP_FRAME_WIDTH, cameraResolution.width);
```
4. Build c++ demo samples
```sh
cd demos
source /opt/intel/openvino_2023.3.0/setupvars.sh
./build_demos.sh -DENABLE_PYTHON=y --build_dir=./
```
* Expected reaults after build
```
open_model_zoo/demos$ tree intel64/Release/ -L 1
├── classification_benchmark_demo
├── crossroad_camera_demo
├── ctcdecode_numpy
├── gaze_estimation_demo
├── human_pose_estimation_demo
├── image_processing_demo
├── interactive_face_detection_demo
├── libgflags_nothreads.a
├── libmodels.a
├── libmonitors.a
├── libmulti_channel_common.a
├── libpipelines.a
├── libutils.a
├── mask_rcnn_demo
├── monitors_extension.so
├── mri_reconstruction_demo
├── multi_channel_face_detection_demo
├── multi_channel_human_pose_estimation_demo
├── multi_channel_object_detection_demo_yolov3
├── noise_suppression_demo
├── object_detection_demo
├── pedestrian_tracker_demo
├── pose_extractor.so
├── security_barrier_camera_demo
├── segmentation_demo
├── smart_classroom_demo
├── social_distance_demo
└── text_detection_demo
```

* Copy run files to venv/bin 
```
cp demos/intel64/Release/* ./<my_venv>/bin/
```

### Practice #1 - bert_question_answering_demo
1. Go to the demo
```sh
cd demos/bert_question_answering_demo/python
```
2. Download required pretrained models
```sh
omz_downloader --list models.lst --precision FP16
```
3. Run
```sh
python3 bert_question_answering_demo.py \
    --vocab intel/bert-small-uncased-whole-word-masking-squad-0001/vocab.txt \
    --model intel/bert-small-uncased-whole-word-masking-squad-0001/FP16/bert-small-uncased-whole-word-masking-squad-0001.xml \
    --input_names="input_ids,attention_mask,token_type_ids" \
    --output_names="output_s,output_e" \
    --input="https://en.wikipedia.org/wiki/Bert_(Sesame_Street)" \
    -c
```

### Practice #2 - interactive_face_detection_demo
* Refer to the `README.md` from `open_model_zoo/demos/interactive_face_detection_demo/cpp`

```sh
omz_downloader --list models.lst
```

```sh
interactive_face_detection_demo -i 0 \
    -m intel/face-detection-adas-0001/FP16/face-detection-adas-0001.xml \
    --mag intel/age-gender-recognition-retail-0013/FP16/age-gender-recognition-retail-0013.xml \
    --mhp intel/head-pose-estimation-adas-0001/FP16/head-pose-estimation-adas-0001.xml \
    --mem intel/emotions-recognition-retail-0003/FP16/emotions-recognition-retail-0003.xml \
    --mlm intel/facial-landmarks-35-adas-0002/FP16/facial-landmarks-35-adas-0002.xml \
    --mam public/anti-spoof-mn3/FP16/anti-spoof-mn3.xml \
    -d CPU
```

### Practice #3 - gaze_estimation_demo
```sh
omz_downloader --list models.lst
```
```sh
omz_converter --list models.lst
```
```sh
gaze_estimation_demo -d CPU -i 0 -m intel/gaze-estimation-adas-0002/FP16/gaze-estimation-adas-0002.xml -m_fd intel/face-detection-adas-0001/FP16/face-detection-adas-0001.xml -m_hp intel/head-pose-estimation-adas-0001/FP16/head-pose-estimation-adas-0001.xml -m_lm intel/facial-landmarks-35-adas-0002/FP16/facial-landmarks-35-adas-0002.xml -m_es public/open-closed-eye-0001/FP16/open-closed-eye-0001.xml 
```
### Practice #4 - monodepth_demo
``` omz convert
pip install tensorflow
pip install torch
pip install onnx
pip install torchvision
```
```sh
omz_downloader --list models.lst
```
```sh
omz_converter --list models.lst
```

``` sh
python3 monodepth_demo.py -d GPU -i 0 -m public/midasnet/FP16/midasnet.xml
``` 

### Practice #5 - object_detection_demo

### Practice #6 - multi_channel_object_detection_demo_yolov3
* Use more than two camera/video inputs

### Practice #7 - segmentation_demo

### (Optional) Practice #8
* 위 데모 실행을 shell script 로 작성해 실행
* 작성한 shell script 실행 시 device 를 parameter 를 받아 CPU or GPU 로 inference 되도록 수정
```sh
# example
$ run.sh CPU # <<-------- CPU 에서 실행

## Hugging Face + Openvino
https://huggingface.co/docs/optimum/intel/inference
$ run.sh GPU # <<-------- GPU 에서 실행
```
## Hugging Face
https://huggingface.co/docs/optimum/intel/inference

