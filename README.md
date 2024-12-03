# <img src="README.assets/JTRPLogoLow.png" alt="img" style="zoom: 80%;" /> JTRP (Jason Ma Toon Render Pipeline)

* [작품](#작품)
* [설치](#설치)
* [시작하기：삼선이 입문 비디오 튜토리얼](#시작하기삼선이-입문-비디오-튜토리얼)
* [사용법](#사용법)
    * [JTRP Custom Pass](#jtrp-custom-pass)
    * [Pencil\+ Outline 4 Unity](#pencil-outline-4-unity)
  * [재질 파라미터](#재질-파라미터)
  * [스크립트](#스크립트)
  * [실시간 스타일 변환](#실시간-스타일-변환)
  * [DXR 샘플 (삭제됨)](#dxr-샘플-삭제됨)
  * [경량 셰이더GUI](#경량-셰이더gui)
  * [모델 아웃라인 임포터（구버전）](#모델-아웃라인-임포터구버전)
* [향후 작업](#향후-작업)

이것은 제가 여가 시간에 개발한 **Unity HDRP** 기반의 **DX12 RayTracing**을 지원하는 카툰 렌더링 툴셋으로, 실시간으로 **영화** 수준의 고품질 카툰 렌더링 CG를 제작하는 것을 목표로 합니다.

UTS를 기반으로 2차 개발되었습니다: https://github.com/unity3d-jp/UnityChanToonShaderVer2_Project

블로그: https://www.zhihu.com/people/blackcat1312/posts

Bilibili: https://space.bilibili.com/42463206

이메일: 1312119064@qq.com

## 작품

https://www.bilibili.com/video/BV1wD4y1w7oU?spm_id_from=333.999.0.0

![](README.assets/1647811318271.png)

![](README.assets/1647811386474.png)

https://www.bilibili.com/video/BV1Bq4y1r7bn?p=3

![](README.assets/1647811706282.png)
![](README.assets/1647811937504.png)
![](README.assets/1647812077711.png)

## 설치

1. Unity 2021 최신 버전을 사용하여 새 프로젝트를 만듭니다 (또는 기존 프로젝트를 사용합니다).
2. [Blender](https://www.blender.org/download/)를 설치하고, **.blend 파일을 더블 클릭하여 Blender를 바로 열 수 있어야 합니다**. 그렇지 않으면 샘플 모델을 가져올 수 없습니다.
3. (프록시 필요) `Window > Package Manager > Add > Add package from git URL`을 클릭하고 `https://github.com/JasonMa0012/JTRP.git`을 입력합니다.

   * 또는 GitHub에서 Zip 파일을 직접 다운로드한 후 `Package Manager > Add package from disk`에서 로컬 패키지를 추가할 수 있습니다.

   <img src="README.assets/1650651450991.png" alt="img" style="zoom: 67%;" />
4. Project 패널에서 `Packages > JTRP`를 찾은 다음 `Edit > Project Settings > Graphics`를 열어 `JTRP\RenderPipelineResources\JTRP_RenderPipelineAsset`을 `SRP Settings`에 할당합니다.

   <img src="README.assets/1650652521492.png" alt="img" style="zoom:80%;" />
5. `Window > Rendering > HDRP Wizard`를 엽니다 (일반적으로 자동으로 열립니다). `Fix All`을 클릭하고 에디터를 다시 시작합니다.

   <img src="README.assets/1650652730659.png" style="zoom: 67%;" />
6. `JTRP\Samples\JTRP_Samples.unitypackage`를 더블 클릭하여 샘플 씬을 가져옵니다. `Assets\JTRP_Samples\SampleScenes`에서 씬을 열고 렌더링 결과가 스크린샷과 일치하는지 확인합니다. 만약 렌더링 결과에 이상이 있다면 설치 과정을 다시 확인하거나 이슈를 제출하세요.

## 시작하기：삼선이 입문 비디오 튜토리얼

![JTRP教程](README.assets/JTRP教程.jpg)

튜토리얼: https://www.bilibili.com/video/BV1AA411A7RR/

모델 배포: https://www.bilibili.com/video/BV1a7411i7js/

비디오에서 배울 수 있는 내용:

버전 관리

- 왜 Git을 사용하는가: 다인 협업, 버전 관리
- GitHub 계정, 리포지토리, LFS, 저장소 및 단일 파일 크기 제한
- SourceTree 튜토리얼:
  - https://zhuanlan.zhihu.com/p/212302462
  - https://zhuanlan.zhihu.com/p/254909901
- Clone, 수정, 스테이징, 푸시, 롤백, 무시
- 또는 Zip을 직접 다운로드: https://github.com/Jason-Ma-233/JasonMaToonRenderPipeline

사전 지식

- 3D 아트, DCC 기초
- Unity 설치, 언어 팩, 기본 지식
- Unity MMD: https://www.bilibili.com/video/BV1Db411e74e
- Blender:
  - PMX 가져오기 플러그인: https://github.com/GiveMeAllYourCats/cats-blender-plugin
  - 모델 처리: 재질 분할, 얼굴 단독 재질, 얼굴 구면화 노멀(선택 사항)

JTRP

- 삼선이 개요: PBR / NPR / 카툰 렌더링 / 삼선이란 무엇인가, 삼선이의 일반적인 특징과 대표 사례
- UTS: https://github.com/unity3d-jp/UnityChanToonShaderVer2_Project/blob/release/urp/2.2.3/Documentation~/index.md
- 파라미터 개요
- Outline
  - 전통적인 노멀 외곽 확장
  - P+ 4 Unity: https://www.psoft.co.jp/jp/product/pencil/unity/
  - P+ 온라인 문서: https://docs.psoft.co.jp/pus400w/jp/latest/
- JTRP를 사용하여 캐릭터 카툰 렌더링하기
  - 섀도우 색상
  - 레이 트레이싱 섀도우
  - 머리카락 섀도우
  - 얼굴 + 머리카락 구면 섀도우
  - 머리카락 하이라이트
  - 림 라이트
- 타임라인: 캐릭터 애니메이션, 카메라 애니메이션, 표정 애니메이션, ABC
- 실시간 물리: https://assetstore.unity.com/packages/tools/physics/magica-cloth-160144
- HDRP / Lit 셰이더 문서: https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@10.6/manual/Lit-Shader.html
- 후처리: 레이 트레이싱 GI / AO / SSR, Bloom, LUT, ToneMapping 등
  - LUT 제작: https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@10.6/manual/LUT-Authoring-Resolve.html
- 렌더링 출력

## 사용법

JTRP는 UTS를 기반으로 확장되었기 때문에 먼저 UTS의 기본 기능을 이해해야 합니다: https://github.com/unity3d-jp/UnityChanToonShaderVer2_Project/blob/release/legacy/2.0/Manual/UTS2_Manual_en.md

#### JTRP Custom Pass

![](README.assets/1647802771257.png)

주로 씬 내 모든 Toon Shader 오브젝트의 렌더링을 제어하며, 누락되면 그레이 모드 상태로 되돌아갑니다.

또한 **Outline의 전역 설정**을 제어할 수 있으며, **BackFace Outline을 사용하려면 먼저 스위치를 켜야 합니다**.

**PostProcess Outline**을 사용할 수 있지만 미리보기 상태이며, 기능이 완전하지 않아 주로 씬의 외곽선을 그리는 데 사용됩니다. 재질을 구성하여 색상을 변경할 수 있습니다.

**Geometry Outline**은 절반 정도만 개발되었으며 설정이 복잡하여 사용을 권장하지 않습니다. 이미 최적화 아이디어가 있지만 계속 개발할 시간이 없습니다. 관심 있는 분들은 함께 개발할 수 있으며, 효과는 비디오를 참고하세요: https://www.bilibili.com/video/BV1vp4y1r7sF

#### Pencil+ Outline 4 Unity

![](README.assets/1647803219913.png)

비디오 튜토리얼에 사용 방법이 있으며, 공식 문서: https://docs.psoft.co.jp/pus400w/jp/4.1.2/index.html

워터마크와 범위 제한을 제거하려면 정품을 구매하세요. 공식 사이트: https://www.psoft.co.jp/jp/product/pencil/unity/

### 재질 파라미터

의문이 있다면 비디오 튜토리얼과 UTS 문서를 참고하세요. 여기서는 JTRP가 UTS에 비해 추가된 부분만 나열합니다.

| ![img](README.assets/1647804306427.png) | HDRP/Toon                                                                                                                                                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Workflow Mode                        | ShadingGradeMap을 우선 사용하며, 그렇지 않으면 기능이 완전하지 않을 수 있습니다                                                                                                                                                  |
| ![img](README.assets/1647803760469.png) | Shadow                                                                                                                                                                                                                         |
| Shading Grade Map                    | 그레이스케일 이미지를 통해 그림자의 범위를 제어합니다. 그림자는 광선 방향과 노멀 방향의 내적(Gradient)을 통해 계산되며, Gradient에 영향을 주어 특정 영역이 더 밝거나 어두워지도록 합니다. 텍스처 색상은 기본적으로 0.5 회색이며, 흰색에 가까울수록 밝아지기 쉽고, 반대는 어둡습니다.                                                                                                      |
| ![img](README.assets/1647804186475.png) | JTRP Features                                                                                                                                                                                                                  |
| Is Face / Hair                       | 머리카락과 얼굴의 스위치로, 헤어 섀도우, 페이스 섀도우 기능을 사용하려면 올바르게 설정해야 합니다.<br />얼굴 재질에서는 Is Face를 켜고, 머리카락 재질에서는 Is Hair를 켜며, 일반 재질은 기본적으로 끈 상태로 유지합니다.                                                     |
| Hair Shadow ……                     | **얼굴 재질에서** 헤어 섀도우를 조정하며, Width는 너비를 제어하고, Ramp는 너비의 거리 감쇠를, Bias는 클리핑 거리를 제어합니다.                                                                                                |
| Hair Z Offset                        | **머리카락 재질에서** 조정하며, 헤어 섀도우 렌더링 시 시선 방향의 오프셋을 제어합니다.                                                                                                                                        |
| Face Shadow Bias                     | **얼굴 재질에서** 조정하며, 얼굴이 그림자를 받을 수 있는 옵션(System Shadows Self Shadows Receiving)을 켰을 때 얼굴 그림자의 광선 방향 오프셋을 조정하여 근거리에서 원하지 않는 그림자를 제거할 수 있습니다.                                                         |
| Spherical Shadow……                 | 고급 옵션으로, 구면화 노멀을 제어하며, 스크립트와 함께 사용해야 합니다. 비디오 튜토리얼을 참고하세요.                                                                                                                            |
| Anti-Perspective                     | 고급 옵션으로, 반투시 강도를 제어하며, 1일 때 모델이 시선 방향으로 압축되어 투시 왜곡을 상쇄합니다. 3D에서 FOV가 클수록 투시 왜곡이 크고 시야각이 넓어집니다. 삼선이는 손으로 그린 느낌을 재현하려고 하므로 투시 왜곡을 최소화해야 합니다. 이 기능은 단독으로 모델을 표시할 때 사용하기 적합하며, 그렇지 않으면 3D 씬과 겹쳐져서 어색해질 수 있습니다.                                       |
| ![img](README.assets/1647804204924.png) | Outline                                                                                                                                                                                                                        |
| Outline Width Ramp                   | Ramp를 통해 거리별 외곽선의 두께를 제어합니다.                                                                                                                                                                                 |
| ![img](README.assets/1647805003341.png) | Environmental Lighting                                                                                                                                                                                                         |
| Built-in Light Direction             | 이 기능을 통해 광선 방향을 수동으로 지정하여 얼굴 그림자, 헤어 섀도우 등을 제어할 수 있습니다. 스크립트와 함께 사용하여 더 지능적인 광선 방향 제어를 구현할 수 있습니다. 비디오 튜토리얼을 참고하세요.                                                            |
| ![img](README.assets/1647806050520.png) | Hair HighLight（**먼저 Show All properties를 클릭하여 UI를 전환하세요**）<br /><br />**비디오를 참고하세요. 시간이 없어서 다 작성하지 못했습니다. 친절한 분이 PR을 제출해주시면 감사하겠습니다**                                                                        |
| ![img](README.assets/1647806243135.png) | Screen Space Rim Light（**위와 동일**）                                                                                                                                                                                         |
|                                      |                                                                                                                                                                                                                                |

### 스크립트

의문이 있다면 비디오 튜토리얼을 참고하세요.

| ![img](README.assets/1647805167570.png) | Spherical Hair High Light Helper                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hair Center                          | 머리카락 전체를 하나의 구로 간주하여 머리의 아래쪽에 빈 오브젝트를 새로 만들어 구의 중심에 놓은 다음, 머리카락에 이 스크립트를 추가하고 구의 중심을 Hair Center에 할당합니다.                                                                                                                                                                                                                                                                                                                                         |
| Renderers                            | 이 기능을 사용하는 Renderer를 선택합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ![img](README.assets/1647805180231.png) |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Center / Renderer                    | 원리는 위와 동일합니다.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Project Light Dir                    | 광선 방향을 2D 원형으로 투영합니다. 광원 방향은 일반적으로 제어할 수 없지만, 삼선이에서 얼굴 그림자에 대한 요구 사항이 매우 엄격하므로 이러한 설정을 통해 광선 방향을 머리 위쪽과 접하는 원형으로 제한하여 광원이 제멋대로 움직이지 않도록 할 수 있습니다.<br />1. 얼굴 재질에서 Built-in Light Direction을 켭니다.<br />2. 씬의 Directional Light를 Light에 할당합니다.<br />3. ForwardDir에서 얼굴의 정면 방향이 FaceCenter의 어느 축인지 선택합니다. Forward는 +Z, Up은 +Y, Right는 +X입니다.<br />4. Y Offset을 조정하고 광원을 회전하여 효과를 확인합니다.<br />5. (선택 사항) Dot Power를 통해 Y Offset을 재매핑합니다. 수평 축은 광선과 Forward의 내적(각도로 이해할 수 있음)이며, 수직 축은 해당 각도에서의 Y Offset 값입니다. |
| ![img](README.assets/1647805141160.png) | Camera Sync<br /><br />에디터와 타임라인에서 Scene View와 Game View 카메라를 동기화하여 **렌더링 결과를 미리 보고 카메라 애니메이션을 제작**할 수 있습니다.                                                                                                                                                                                                                                                                                                                                                 |
| Game To Scene / Scene To Game        | 문자 그대로의 의미로, 한 View의 카메라 상태를 다른 View의 카메라로 수동으로 복사합니다.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Mode                                 | Game To Scene / Scene To Game: 카메라 상태를 자동으로 복사합니다.<br />Automatic: 타임라인에서 미리보기/카메라 애니메이션 수정에 적합합니다.<br />1. 씬의 타임라인 컴포넌트를 Timeline Playable Director에 할당합니다.<br />2. 카메라의 Transform을 Root에 할당합니다.<br />3. 타임라인에서 카메라 애니메이션을 재생하면 Scene View의 카메라가 Game View 카메라를 따라갑니다.<br />4. 타임라인에서 카메라 애니메이션 키프레임 위치로 이동하여 Scene View 카메라를 이동하면 Game View 카메라가 Scene View 카메라를 따라갑니다.<br />5. Update Create Key (Shift+Q)를 사용하여 카메라 키프레임을 저장합니다.                                                                                     |
|                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

### 실시간 스타일 변환

https://www.bilibili.com/video/bv1FY4y1h7Vm

![image-20220506162404333](README.assets/image-20220506162404333.png)

참고: https://blog.unity.com/technology/real-time-style-transfer-in-unity-using-deep-neural-networks

RTX3070 1080P에서 6-8ms 소요

### DXR 샘플 (삭제됨)

![image-20210111010551810](README.assets/image-20210111010551810.png)![image-20210111010608857](README.assets/image-20210111010608857.png)

비디오: https://www.bilibili.com/video/BV1Tr4y1F7Pv

### 경량 셰이더GUI

강력하고 유연하며 가벼운 Unity 셰이더 GUI 시스템입니다.

간결한 MaterialPropertyDrawer 문법을 사용하여 복잡한 셰이더 GUI를 구현하고, 개발 시간을 크게 절약하며 사용 및 확장이 용이하여 아티스트의 사용 경험을 효과적으로 향상시킵니다.

https://github.com/JasonMa0012/LWGUI

### 모델 아웃라인 임포터（구버전）

![](README.assets/Snipaste_2020-04-14_22-30-12.png)

가져오기 프로세스는 더 이상 유효하지 않으며, 자세한 내용은 [이 글](https://zhuanlan.zhihu.com/p/107664564)을 참고하세요.

하드 서페이스에 평활 노멀을 생성하려면 DCC 도구나 NormalMap을 사용하는 것이 좋으며, UTS 문서에도 해당 내용이 소개되어 있습니다.

## 향후 작업

UTS3는 이미 Unity 공식 패키지에 포함되었습니다: https://github.com/Unity-Technologies/com.unity.toonshader

앞으로, UTS3가 안정적인 버전으로 출시되고 ShaderGraph를 지원한 후, JTRP를 유연하고 가벼운 플러그인으로 재구성하여 CustomNode나 CustomPass 등을 사용하여 UTS3를 비파괴적으로 확장할 계획입니다.
