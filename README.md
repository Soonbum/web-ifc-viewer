<p align="center">
  <a href="https://ifcjs.github.io/info/">ifc.js</a>
  |
  <a href="https://ifcjs.github.io/info/docs/Guide/web-ifc-viewer/Introduction">문서</a>
  |
  <a href="https://ifcjs.github.io/web-ifc-viewer/example/index">데모</a>
  |
  <a href="https://discord.gg/FXfyR4XrKT">디스코드</a>
  |
  <a href="https://github.com/IFCjs/web-ifc-viewer/tree/master/example">사용법 예제</a>
  |
  <a href="https://www.npmjs.com/package/web-ifc-viewer">npm 패키지</a>
</p>

<img src="banner.png">
<h1>web-ifc-viewer <img src="https://ifcjs.github.io/info/img/logo.svg" width="32"></h1>

![npm](https://img.shields.io/npm/dw/web-ifc-viewer)
![opencollective](https://opencollective.com/ifcjs/tiers/badge.svg)

이 라이브러리는 [THREE.js](https://github.com/mrdoob/three.js/)의 공식 `IFCLoader`인 [web-ifc-three](https://github.com/IFCjs/web-ifc-three)의 확장입니다. 이것은 JavaScript에서 IFC 모델의 Three.js 지오메트리를 파싱&생성할 뿐만 아니라 3차원, 평면 클리핑, 2D 도면 탐색 및 생성 등을 수행할 수 있는 BIM 도구를 쉽게 만들 수 있는 다양한 도구들을 제공합니다.

## 상태

**web-ifc-viewer**는 멋진 BIM 도구들을 즉시 만들 수 있는 여러 도구들을 제공합니다. 도구들은 매우 안정적인 동시에 이 리포지토리의 상태는 [web-ifc-three](https://github.com/IFCjs/web-ifc-three)와 [web-ifc](https://github.com/tomvandig/web-ifc)의 상태와 밀접하게 관련되어 있습니다. 

현재 프로젝트 상태를 더 잘 이해하려면 `README` 파일들을 확인해 보십시오.

## 데모 

[온라인 데모](https://ifcjs.github.io/web-ifc-viewer/example/index)에서 당신의 IFC 모델들을 가지고 IFC.js 웹 IFC 뷰어를 테스트해보십시오.

## 문서

API 참조, 가이드, 튜토리얼은 [저희 공식 문서](https://github.com/IFCjs/web-ifc-viewer/blob/master/CONTRIBUTING.md)를 확인해 보십시오.

## 설치

`npm install web-ifc-viewer` 또는 `yarn add web-ifc-viewer`

## 빠른 설정

먼저, 라이브러리를 가져오는 JavaScript 파일을 만들고 한 장면을 만듭니다:

```js
import { IfcViewerAPI } from 'web-ifc-viewer';

const container = document.getElementById('viewer-container');
const viewer = new IfcViewerAPI({ container });
viewer.axes.setAxes();
viewer.grid.setGrid();

const input = document.getElementById("file-input");

input.addEventListener("change",

  async (changed) => {
   
    const file = changed.target.files[0];
    const ifcURL = URL.createObjectURL(file);
    viewer.IFC.loadIfcUrl(ifcURL);
  },

  false
);
```

여타 번들러를 이용하여 이 파일을 번들(bundle)할 수 있습니다. 이것은 [rollup](https://rollupjs.org/guide/en/)을 이용한 예제 구성 파일입니다:

```js
import resolve from '@rollup/plugin-node-resolve';

export default {
  input: 'index.js',
  output: {
    file: "bundle.js",
    format: 'esm'
  },
  plugins: [ resolve() ]
};
```

이제 다음과 같이 HTML 페이지에서 표현할 수 있습니다:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <link rel="icon" type="image/png" href="./favicon.ico" />
    <link rel="preconnect" href="https://fonts.gstatic.com" />
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet" />
    <link rel="stylesheet" type="text/css" href="./styles.css" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>IFC.js</title>
  </head>
  <body>
    <input type="file" id="file-input" accept=".ifc, .ifcXML, .ifcZIP">
    <div id="viewer-container"></div>
    <script src="./bundle.js"></script>
  </body>
</html>
```

## 내용

이 프로젝트는 다음 폴더들로 구성되어 있습니다:

- **viewer**: 소스 코드를 포함하고 있음.

- **example**: 라이브러리를 어떻게 사용하는지에 대한 예제를 포함하고 있습니다.

## 기여(공헌)하기

도와주고 싶습니까? 훌륭해요!

[저희의 기여 의견](https://github.com/IFCjs/web-ifc-viewer/blob/master/CONTRIBUTING.md)을 확인해 보거나 [디스코드](https://discord.gg/FXfyR4XrKT)를 통해 저희에게 직접 말해 주십시오.
