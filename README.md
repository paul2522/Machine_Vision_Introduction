# Machine Vision Introduction

## Introduction
### Process
1. Imaging
2. Processing and analysis
3. Communication
4. Action

### Application Types
* Four Types from technical point of view
1. Locate : find position and orientation(방향성)
2. Measure : get physical dimension(distance(거리), diameter(직경), curvature(곡률), area(영역), height(높이), volume(부피))
3. Inspect : validate features(presence, absense of object)
4. Identify : read codes(ex 바코드) and characters(ex 글자, 숫자)

### Branch Types
* Automotive, Electronics, Food, Logistics, Manufacturing, Robotics, Packaging, Pharmaceutical, Wood

### Camera Types
1. Vision Sensor : 준비시간이 가벼운 편
    - 색 구분, 윤곽선 확인, 텍스트 읽기 기능
2. Smart Cameras : PC 없이도 기능하는 카메라
    - 2D Smart : 라벨 위치 및 패턴 분석
    - 3D Smart : calibrated 3D data, 표면 불량 검출, 높이 및 용량 측정, 형태 인식
3. PC-based Systems : 카메라가 이미지를 PC로 보내서 진행 및 분석. 많은 양의 데이터를 보내기 때문에 카메라는 스트리밍 장비라 볼 수 있다.
   - 3D Camera : calibrated 3D 모양 데이터를 수집하여 컴퓨터로 전송.
   - Multiscan Camera : 하나의 카메라 유닛이 여러개의 스캔을 동시에 수행, 2d grayscale과 3D 이미지를 한 스캔에 수행.

## Imaging
### Technical names
1. Acquiring
2. Capturing
3. Grabbing 
   * 고품질의 이미지를 grab 하는 것이 성공적인 비전 어플리케이션의 1순위 과제

### Basic Camera Concepts
* Camera, Lens, Lighting , Object(Target)

#### Digital Imaging
* Sensor chip : grap digital image, 기존의 사진촬영이 아님.
* Sensor에는 광민성의 pixel들의 array가 있음. 이 센서를 Imager라 함.
* Digital image sensor technology
  1. CCD(Charge-Coupled Device)
  2. CMOS(Complementary Metal Oxide Semiconductor)
* PC 기반 시스템에서는 frame grabber가 Image 분석 SW에 맞춘 raw image data를 가진다.
* line scan camera : one pixel row를 가진 센서, 시간마다 하나의 선을 캡처, 해당 선을 분석 또는 여러 개의 선을 합쳐서 전체 이미지를 구성.

#### Lenses and Focal Length
* sharp image 생성을 위해 렌즈가 빛을 모음.
* 렌즈는 다른 말은 objective.
* Image in focus(초점이 맞춰진 이미지) : 선명하게 나옴.
* Out of focus : 뿌옇게 나옴.
* 렌즈 타입 간의 서로 다른 점들 : angle of view, focal length
* Angle of view : 카메라가 얼마만큼이나 볼 수 있는지?
    - wide angle : 더 큰 부분의 화면을 봄.
    - small angle of view of tele lens : 먼거리에서 자세히 볼 수 있다.
* Focal length : 렌즈와 초점 사이의 거리
    - 초점이 센서에 있을 경우, 이미지가 초점이 맞음.
    - Angle of view와 연관있으며 긴 초점 거리는 작은 angle of view를 가지며, 반대도 마찬가지.

#### Field of View in 2D
* 2D 시스템에서 FOV는 카메라가 보는 전체 영역이다. 영역이므로 너비와 높이.
* Object distance : 렌즈와 물체 사이의 거리이며 LTO(Lens to object) 또는 working distance라 불림.

#### Aperture and F-stop
* aperture(조리개)는 렌즈를 열어 센서에 닿는 빛의 양을 조절, 큰 조리개가 더 많은 빛이 들어옴.
* 조리개의 크기는 F-stop 값에 의해 측정됨.
* +(F 값 : 초점 거리를 렌즈의 구경으로 나눈 비율)

#### Depth of Field
* Minimum object distance : 카메라가 초점을 잡을 수 있는 최소거리
* Maximum object distance : 초점이 잡히는 최대 거리, 기본적인 렌즈는 최대 거리가 없고 무한대지만 Macro Lenses 와 같은 특정 종류는 있음.
* Macro Lens : 매우 짧은 초점 거리에서 광학 성능을 제공, 가까운 거리에서 작은 물체를 촬영
* focal plane : 초점이 가장 선명해지는 거리, depth of field의 안에만 있어도 초점이 충분히 좋다.
* 긴 focal length는 좁은 depth of field를 부여, 반대도 마찬가지.
* 큰 조리개는 좁은 depth of field를 부여, 반대도 마찬가지.

* 카메라와 렌즈 사이에 distance ring을 넣어서 focal plane를 카메라와 가깝게 이동 가능(minimum object distance를 줄이기 때문). distance ring은 shim, spacer, extension ring이라 부름.
* 굵은 distnace ring을 extension tube라 부름. 이를 통해 기본 렌즈에 확대 효과 부여 가능.
* Maximum Object distance가 결정되고 depth of field의 범위가 줄어듬.
* 기본 렌즈(실물의 1/10) -> 마크로 렌즈(1:1 ~ 1:50) -> 마이크로 렌즈(1:50 이상) 갈수록 확대됨.

### Base Image Concepts

#### Pixel and Resolution
* pixel : 디지털 이미지의 가장 작은 단위, 주로 센서의 물리적 픽셀과 이미지의 픽셀이 대응됨.
* Typical values of sensor resolution in 2D Machine vision
    1. VGA(Video Graphics Array) : 640x480 pixels
    2. XGA(Extended Graphics Array) : 1024x768 pixels
    3. SXGA(Super Extended Graphics Array) : 1280x1024 pixels
* Object resolution : 센서의 한 픽셀에 해당하는 물체의 물리적인 거리. object resolution을 위한 주 unit은 micros per pixel 과 mm per pixel이다.
* 몇 측정에서는 해상도가 픽셀보다 작아질 수 있다.
* 픽셀 데이터의 서프픽셀 정보를 추출하는 보간 알고리즘에 의해 정해짐.
* Fov width / number of pixel(width)

#### Intensity
* pixeldml 밝기를 Intensity라 함.
* Intensity 정보는 각각의 픽셀에 저장되며 서로 다른 종류 일 수 있다.
* Example
  1. Binlary : One bit per pixel = 0(black), 1(white)
  2. Gray scale: 0(black) ~ 255(white)
  3. Color : 3개의 byte값들이 모여 전체 색 정보. 0(Black)~255(R,G,B)
* bit-depth : pixel의 특징을 결정 짓는 bit의 개수
* 대부분의 머신 비전은 8bit로 충분(Grayscale)이며 더 깊은 bit-depth는 최첨단 센서와 센싱 프로그램에 사용된다.

#### Exposure
* 노출은 얼마나 빛이 감지되는지. 2가지 요인으로 결정됨.
  1. Exposure Time : 노출되는 시간, milliseconds 단위, shutter time이라 불렸음
  2. Aperture size : 조리개 크기, len를 통과하는 빛의 양
* 노출 시간이 너무 짧아서 센서가 충분한 빛을 얻지 못하면 underexposed 상태.
* 너무 빛이 많은 경우 센서가 saturated(포화)되면 이미지는 overexposed 상태.
* Motion blur가 exposure와 연관되어 있다. object가 이동 중이며 노출 시간이 너무 긴 경우, 이미지가 흐릿해지고 프로그램 견고성이 취약해짐.

#### Gain
* Intensity를 조절하기 위해 조리개 크기 또는 노출 시간을 조정해주었습니다.
* 이미 노출된 이미지의 intensity 조정을 위해 신호 값을 증폭하는 방법이 gain.
* 하지만 신호와 동시에 noise도 증폭시키는 특징이 있음.

### Contrast and Histogram
* 대비는 흰 곳과 밝은 곳의 상대적인 차이. 이미지 안의 모든 것들을 한번에 잘 보기위해 조정.
* 히스토그램 : 픽셀들을 intensity의 세기에 맞춰서 분포도를 만든 것.
* 컬러에서 히스토그램은 gray scale과 동일하게 작동하나, 각각의 컬러 채널이 각각의 histogram으로 표현된다.
* (히스트로그램의 표현 단위는 8bit(0~255))
* 높은 contrast(잘표현하는 contrast) 단계에서는 연속적인 데이터 분포를 나타내는 histogram이 나오는 반면 contrast를 낮출 경우 histogram은 좁게 표현된다(다양하지 않게).
* (물론 기본적으로 pic sample이 여러 색(grayscale)을 가져야한다.)

## Illumination(조도)

* 머신 비전에서 빛은 매우 중요하여 강직한 어플리케이션을 목표로 한다.
    1. 관측되는 특징들을 강화
    2. 이미지 품질의 높은 반복성을 보장(반복성 : 동일한 조건에서 수행된 연속적인 측정 결과 일치 = robust)
* 빛은 실내 빛이나 햇빛처럼 ambient하다, 또는 목적에 맞춘 특별한 조명 또한 있다.
* 머신 비전 장비는 빛에 민감하기 때문에 ambient 빛은 주로 cover에 의해 제거된다.(shroud)
