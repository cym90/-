<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Leaflet Quick Start Guide</title>

  <!-- Leaf css/js 를 추가해준다. -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
        integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A=="
        crossorigin=""/>
  <!-- Make sure you put this AFTER Leaflet's CSS -->
  <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"
          integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA=="
          crossorigin=""></script>

  <style type="text/css">
    html,body { width:100%; height:100%; margin:0; padding:0; }
    #mapid { width:100%; height:100%; }
  </style>

</head>
<body>

<!-- 맵을 넣을 div 요수 -->
<div id="mapid"></div>

<script type="text/javascript">
  /**
   * [지도 초기화(map) 및 설정(setView)]
   * 좌표: [51.505, -0.09]
   * 줌레벨: 13
   *
   * [설명]
   * 1. (L.map)지도 인스턴스 생성 시 옵션없이 생성을 했으므로, 모든 마우스 및 터치 기능이 활성화 되며,
   *    확대/축소와 같은 컨트롤 속성을 가지고 있다.
   *
   * 2. 대부분의 Leaflet 메소드는 반환되는 명확한 값이 없으면 jQuery 체이닝과 같이 map 객체를 반환한다.
   *    (따라서 setView 메소드 또한 map 객체 반환)
   */
  var mymap = L.map('mapid').setView([51.505, -0.09], 13);

  /**
   * [생성된 맵에 타일 레이어 추가] (Mapbox Street 타일레이어)
   *
   * 일반적으로 타일 레이어를 만드려면 아래와 같은 항목을 셋팅해야 한다.
   * (타일 이미지에 대한 URL템플릿, 텍스트 속성, 레이어 최대줌레벨)
   *
   * 아래는 Mapbox Static Tiles API를 사용한다.
   * Mapbox 타일 사용 시 가입 후 엑세스토큰을 받아야 한다.
   * 해당 API는 256x256 대신에 512x512 타일을 반환하므로 zoomOffset 값을 -1로 지정했다.
   */
  L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
    attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
    maxZoom: 18,
    id: 'mapbox/streets-v11',
    tileSize: 512,
    zoomOffset: -1,
    accessToken: 'pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw' // mapbox 가입 후 발급되는 토큰 입력
  }).addTo(mymap);
  /**
   * Leaflet은 공급자에 구애받지 않으며, 타일에 대해 특정 공급자를 선택하도록 강요하지 않는다.
   * 따라서 Naver, Kakao 맵과 같은 다른 공급자로 교체가 가능하다.
   * OpenSteetMap을 기반하는 모든것을 사용 시 저작권고지에 따라 저작자가 의무화 된다.
   */
</script>
</body>
</html>
