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

### Illuminatino Principles

#### Light, Color
* 3가지의 특징
  1. 파장 또는 색(nm(nanometers)로 관측됨.)
  2. Intensity(밝기)
  3. Polarization(매질의 진동이 모든 방향에 대해 같지 않은 상태)
* 주로 파장과 Intensity가 머신비전에 주로 중요하며 Polarization(편광)은 특수한 경우에 해당한다.
* 다른 파장은 다른 색으로 나타낸다. 사람의 눈은 가시광선 내의 색만 볼 수 있으며, 보라부터 적색까지다. 보라색보다 짧은 파장을 가지는 빛을 UV(ultraviolet), 자외선이라 하며(400nm 미만) 적색보다 더 긴 파장을 가지는 빛을 IR(infrared), 적외선이라 한다(700nm 초과).
* 센서의 Spectral response(스펙트럼 응답)은 다른 파장에 따른 민감도 곡선이다. 카메라 센서는 사람 눈이랑 다른 스펙트럼 응답을 가질 수 있다.
* (사람은 낮시간에 555nm에서 가장 높은 스펙트럼 응답을 가지는 반면,IVC-2D내 센서의 스펙트럼 응답은 500 nm에서 가장 높은 수치를 가진다.)

#### Reflection, Absorption, Transmission
* optical axis(광축) : 렌즈의 중심으로 나와서 카메라의 방향으로 진행하는 선.
* 빛이 표면을 만나면 반사되고, 모든 빛은 하나의 방향으로 반사된다. 이를 direct or specular reflection이라하며 주로 물체가 빛나는(거울 같은) 경우에 해당된다.
* 입사각과 반사각은 표면 법선에서 항상 동일하게 측정된다.
* 표면이 빛나지 않는 경우 matte(무광택)인 경우, 확산 반사가 생긴다. 반사되지 않는 빛은 표면에 흡수된다.
* 투명 또는 반 투명의 매질에서는 transmit light가 발생한다.
* transmit light는 빛이 surface를 뚫고 나가는 반사다.
* 위 원리, 반사, 흡수, 전파는 머신 비전에서 빛의 용도의 기본을 구성한다. 추가로 emission(배출)은 물체가 빛을 생성할 때이며 예를 들어 녹은 철이 높은 온도로 인해 붉은 빛을 발생시키는 것이다.

### Lighting Types
* 머신비전에서 사용 가능한 빛은 매우 다양하지만, 밑에 서술하는 기술들이 대부분 사용된다. 가장 많이 사용되는 것은 LED(Light_Emitting Diode)이며, 균일한 밝기와, 긴 시간, 낮은 전력을 가진다.

#### Ring Light
* Ring light는 렌즈의 광축 주위 또는 카메라 또는 카메라와 물체 사이 어딘가에 위치한다. 입사각은 ring diameter(직경), 빛이 착용되는 위치, LED가 조준하는 각도에 영향을 받는다.
* 장점 : 쉽게 사용 가능, 높은 intensity 와 짧은 노출 시간
* 단점 : 직접 반사, 반사 표면 위 hot spots(너무 밝아서(빛이 뭉쳐서) 생기는 하얀 점)

#### Spot Light
* 광축에서 출발하는 것이 아닌 다른 방향에서 나오는 빛. 오직 확산 반사만 카메라에 닿는다.
* 장점 : No hot spots
* 단점 : 균일하지 않은 조도, 확산 반사에 의존하기 때문에 강한 빛이 필요.
  
#### BackLight
* 빛이 물체 뒤에서 나와 윤곽선이나 실루엣을 만듬.
* 일반적으로 광축과 수직으로 하여 위치함.
* 장점 : 매우 좋은 대비, 텍스쳐와 색, ambient 빛에 강직함.
* 단점 : Dimension(backLight의 크기)가 object 보다 켜야함.(그래야 빛이 lens로 들어가니까)

#### Darkfield
* 흑색구역은 큰 입사각에 대해 조명을 비추는 것. 직접 반사는 모서리에서만 발생한다. 평평한 표면에 떨어지는 빛은 카메라에서 멀리 반사됩니다.
* 장점 : 표면의 스크래치, 튀어나온 모서리, 오염을 효과적으로 개선
* 단점 : 적은 특징을 가진 얇은 표면에만 주로 작동, 물체에 대한 짧은 거리가 필요(먼거리는 안된다는 뜻), 물체가 어느 정도 반사감이 있어야 한다.

#### On-Axis Light
* 조명소스와 카메라 렌즈가 동일한 축을 가지고 있음
* 광선이 광축과 평행하기 때문에, 직접 반사가 focal plane으로 표면에 나타낸다.
* 장점 : 매우 균일한 조도, hot spot 없음, 다른 반사도의 물질의 높은 대비
* 단점 : 낮은 intensity은 긴 노출 시간이 필요로 한다.
* 반투명 유리의 청소가 자주 필요하다.(동축조명의 유리 인듯)

#### Dome light
* 반짝이는 매질은 hot spot과 그림자가 없는 매우 확산된 조도가 필요하다. 광원 부분은 dome의 끝 부분
* dome light의 경우, LED가 가능하게 하는 균일한 조도를 무광택의 domewall 안에 비춘다.
* 이미지의 중앙 부분은 어두워진다. 왜냐하면 돔의 구멍 부분이 카메라가 보고있기 때문에.
* 장점 : 매우 높은 반사 물질에 대한 효율성이 높다, 균일한 조도, 이미지의 중앙 부분이 조금 어두운 것 제외, hot spot 없음.
* 단점 : 낮은 밝기에 따른 긴 노출 시간이 필요, object 보다 돔의 크기가 더 커야함.

#### Laser line
* 3D insepction은 주로 3D 카메라가 필요하지만.
* 정확도와 속도가 중요하지 안을때, 2D 카메라 사용시 비용 절감 가능.(근데 현장에서 2D 카메라를 사용한 레이저 라인은 거의 못봄)
* 장점 : 비용, 레이저를 통한 높이 측정 가능
* 단점 : 레이저 안전도 이슈, xz값 측정에 따른 y 값 소실, 3D 카메라보단 정확도가 낮음

### Lighting Variants and Accessories

#### Strobe or constant light
* strobe light : 반짝이는 빛(점멸 빛), strobing은 LED가 turbo charging을 통한 constant light 보다 더 밝은 빛을 만든다.
* 필요한 시간에만 높은 전력을 쓰고 off 때 냉각한다.
* 가동 시간과 비가동시간 전체에 대한 가동시간의 비율을 duty cycle(가동 비율)
* 강한 빛을 사용함에 따라 노출 시간을 줄일 수 있고 motion blur 또한 줄일 수 있다. Lamp의 수명 또한 증가한다.
* Strobing LED는 sw hw 둘다 필요하다.(켰다 끄고 시간 조절)

#### Diffusor Plate
* 광원의 종류는 주로 diffusor plate가 있냐 없냐로 나뉜다.
* Diffusor plate는 직광을 diffuse하게 바꿔준다.
* 목적은 반짝이는 표면에 대한 직광의 반사로 인해 발생하는 이미지의 bright spot을 방지하기 위함.
* rule of thumb(경험의 바탕으로 둔 방법)
  1. 빛나는 물체는 diffusor plate를 필요로 한다.(bright spot 방지)
  2. diffusor plate는 빛을 흡수한다.(주로 20% ~ 40%)
* intensity가 감소함에 따라 노출 시간이 적게 필요한 high speed 구동에서 좋지않다.
* diffusor plate는 multi-LED array(여러개의 광원이 이어져서 있음)에 잘맞음, 멀고 단일의 LED는 여전히 bright spot을 만든다.

#### LED Color
* LED 광은 여러 색으로 나온다. 주로 녹색과 적색. 물론 청색, 백색, UV(자외선), IR(적외선) 또한 있다. 적색 LED는 가장 저렴한 편이며 청색이나 녹색 LED 보다 10배 이상 오래간다.
* 다른 물체는 다른 색을 반사한다. 푸른 물체는 푸른색을 반사하기에 푸르게 나타난다. 청색광이 푸른 물체를 조명하는데 쓰이며 gray-scale 이미지에 밝게 나타난다. 만약 적색광이 푸른 물체에 쐬면 검게 나타난다. 그래서 gray-scale 이미지에서도 컬러를 유리하게 사용할 수 있다.

#### Optical filters
* 광학 필터는 카메라 앞에 위치하여 특정 파장(색)이나 polarization(편광)을 흡수한다.
* 예를 들어 선글라스는 위험한 자외선을 막아준다.
1. band-pass filter : 특정 색의 빛만 통과시킨다(예를 들어 특정 파장 간격)
2. Polarization filter : 특정 편광의 빛만 통과시킨다. 원하지 않는 반사는 거르기 위함.

### Safety and Eye protection
* 빛의 세기가 강할 경우 위험할 수 있다. 특히 레이저의 경우나 가끔의 LED에서.
* 광원을 사용전에 안전 분류를 해놓아야 한다.
ㅉ
#### Laser safety
* 레이저는 하나의 파장으로 평행하는 광선을 쏘기 때문에 눈에 위험하다.
* 레이저는 laser classes로 분류되며 1에서 4단계로 나뉜다. 2,3이 대부분에서 사용된다.

#### LEDS
* LED는 기술적 관점에서 레이저는 아니지만, 매우 작은 크기와 하나의 주요 방향으로 빛을 쏘면 레이저와 유사하게 된다.
* LED의 빛의 세기가 높으면 위험하지만 따로 단계로 나누지는 않는다.
* LED는 strobe light(점멸 빛)에 사용되며 간질 발작을 유발할 수 있다.


#### 3D imaging technology
1. TOF(Time of Flight)
  * 신호를 이용하여 사물을 거리를 측정하는 기술
2. Struted light
3. Laser triangulation : 4장에 나옴
4. Stereo vision
