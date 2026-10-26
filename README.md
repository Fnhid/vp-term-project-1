# Digital Image Processing — Term Project 1 (Squid Game Composite)

`squid_head + squid_body − squid_points` 를 CxImage 픽셀 연산으로 합성하는 MFC 프로그램.

## 폴더 구조
```
cximage/            CxImage 라이브러리 (v142로 설정됨, 빌드 결과는 git에 안 올림)
Team12_Squid/
  team12_squid/     우리 MFC 프로젝트 (VS가 만듦: team12_squid.sln, .vcxproj, 소스)
  DOC/              보고서, 결과 이미지
  sample_images/    과제 샘플 이미지
```

## 1. CxImage 라이브러리 빌드 (clone 후 최초 1회)
1. VS 설치 관리자 → 개별 구성 요소 → **v142 빌드 도구용 C++ MFC/ATL (x86 및 x64)** 설치 확인
2. `cximage/CxImgLib.sln` 열기 → 구성 **Unicode Debug / Win32** → 솔루션 빌드
3. `cximage/x86/lib/` 에 `cximage_wd.lib` 등이 생기면 성공

## 2. 새 MFC 프로젝트 만들 때 설정
- 프로젝트 이름: **`team12_squid`** (명세: `.sln` 이름은 `teamNumber_teamName.sln`)
- 위치: **`Team12_Squid/`**, **솔루션 및 프로젝트를 같은 디렉터리에 배치** 체크
  → `Team12_Squid/team12_squid/team12_squid.sln` 이 생성됨 (cximage 상대경로 `..\..\cximage` 가 맞는 깊이)
- 플랫폼: **x86 (Win32)** — CxImage 라이브러리가 32비트로만 빌드됨
- 프로젝트 속성 (모든 구성, Win32):
  - 일반 → 플랫폼 도구 집합: **v142**, 문자 집합: **유니코드**, MFC 사용: **공유 DLL**
  - C/C++ → 일반 → 추가 포함 디렉터리: `$(SolutionDir)..\..\cximage\CxImage`
  - 링커 → 일반 → 추가 라이브러리 디렉터리: `$(SolutionDir)..\..\cximage\x86\lib`
  - 링커 → 입력 → 추가 종속성 (Debug):
    `png_wd.lib;jpeg_wd.lib;zlib_wd.lib;tiff_wd.lib;jbig_wd.lib;jasper_wd.lib;mng_wd.lib;libdcr_wd.lib;cximage_wd.lib`
- `pch.h`(또는 `stdafx.h`)에 `#include "ximage.h"` 추가

## 제출
- 파일명: `Team12_Squid.zip` (명세: `TeamNumber_TeamName.zip`)
- `cximage/` + `Team12_Squid/` 를 함께 압축 (채점 시 수정 없이 빌드되도록)
