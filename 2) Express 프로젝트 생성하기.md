## 2) Express 프로젝트 생성하기

**express generator**을 설치하기에 앞서 npm이 설치되어 있어야 하는데, **Node**를 설치하면 npm도 자동으로 설치가 됩니다.

여기서 **npm** 과 **Node** 가 무엇인지 먼저 알고 가자면 

> **Node.js**는 Chrome V8 JavaScript엔진으로 빌드된 JavaScript 런타임 입니다. **Node.js**는 이벤트 기반 Non 블로킹 I/O 모델을 사용해 가볍고 효율적입니다. **Node.js**의 패키지 생태계인 npm은 세계에서 가장 큰 오픈 소스 라이브러리 생태계이기도 합니다

**npm**은 **Node.js**기반의 모듈을 모아둔 집합 저장소이다. **npm**은 **Node Package Manager** 또는 **Node Package Modules**라고도 한다.



이제 Express 프로젝트를 생성하겠슴.

**npm**을 통해 **Express generaton**를 설치 (global로 추가하기 위해 -g 옵션 사용)

**$ npm install express_generator -g**

그다음 프로젝트를 생성

**$ express Bitcoin_Manager** 

생성된 프로젝트 폴더로 이동하여 모듈을 설치

**$ cd Bitcoin_Manager**

**$ npm install**

---



### API Document

#### 이용에 대한 참고 사항

1. 서버간 통신은 보안을 위하여 HTTPS를 쓰도록 권장합니다.
2. HTTPS를 통하여 API를 이용하는 파트너사 서버는 유효한 공인인증서를 사용해야 합니다.
3. user_key는 외부에 노출되지 않도록 주의해 주시기 바랍니다.

#### 이용 시작하기

1. **플러스 친구 앱 생성**

   * 플러스친구에서 API형 기능을 사용하기 위해서는 먼저 관리자센터를 통해 key 발급을 위한 앱을 등록해야 합니다.
     1. **플러스친구 관리자센터**의 좌측 **스마트채팅** 메뉴에서 **API형**을 선택합니다.
     2. **'설정하기'** 버튼을 클릭합니다.
     3. 앱 정보와 모니터링 메시지를 수신할 전화번호를 입력하고, 개인정보 수집 및 이용에 동의한 뒤 정보를 저장하여 앱을 생성합니다.

2. API형 서비스를 위한 포스트 생성

   * API형 서비스 구현 중 관리자센터를 통해 생성 가능한 포스트를 사용하고자 하는 경우 다음 단계에 따라 진행 할 수 있습니다.

     1. 관리자센터의 홈에서 글쓰기를 합니다.

     2. 관리자센터에서 글을 발행한 후, 우측 상단의 더보기를 클릭하여 URL복사를 클릭합니다.

     3. 응답 메시지(링크)의 message_button 항목에서 복사한 URL을 사용합니다.

        ​

3. API형 서비스 시작

   * API형 서비스가 개발 완료되어 서비스 가능한 상태가 되면, 다음 단계에 따라 서비스를 시작할 수 있습니다.
     1. API TEST : 등록한 앱 url 우측의 API TEST 버튼을 클릭하여 서비스 시작 가능여뷰를 체크합니다. 필수 API인 Home Keyboard API가 정상적인 응답을 받지 못하는 경우 서비스 시작이 불가합니다.
     2. 서비스 시작: API 테스트를 통과한 경우, 서비스 시작 버튼을 클릭하면 API형 서비스가 시작됩니다.
        * 실 서비스 적용 전 테스트를 원하시는 경우 테스트 전용으로 사용하실 별도의 플러스친구를 개설하여 테스트를 진행해 주시기 바랍니다.
        * 신규 API형은 자동응답형과 동시에 사용할 수 없습니다. 다만 API형의 서비스 중지 후 자동응답형을 사용하는 것은 가능합니다.

4. API형 서비스 중지

   * 직접 중지 : 더 이상 API형 서비스를 이용하지 않으시려면, 관리자센터의 스마트 채팅 > API형에서 *중지하기*를 통해 API형을 중지할 수 있습니다.
   * 어루 횟수 초과에 따른 중지 : API형 서비스에서 오류가 발생하는 경우, 카카오는 앱 정보에 등록된 전화번호를 통해 모니터링 메시지를 발송합니다. 만일 오류 횟수가 일 1000건을 초과하게 되면 카카오는 자동으로 해당 앱의 서비스를 중지합니다. 오류 횟수 초과로 인해 중지된 앱은 관리자센터에서 오류 수정 후 직접 다시 서비스를 시작할 수 있습니다.
   * 관리자의 차단에 따른 중지 : 파트너사에서 플러스친구 API의 운영정책에 반하는 내용을 API를 통해 서비스 하는 것이 확인된 경우, 카카오의 관리자는 해당 앱의 서비스를 중지할 수 있습니다. 관리자에 의해 차단된 앱은 직접 서비스를 다시 시작할 수 없으므로, 앱의 차단 사유를 확인하신 뒤 문제가 되는 내용을 수정하여 플러스친구 고객센터(1544-4293)를 통해 차단 해제를 요청해 주시기 바랍니다.

5. 클라이언트 테스트

   * API형 서비스가 시작되면 카카오톡 채팅방에서 직접 자동응답 기능을 실행할 수 있습니다. 신규 API형을 통한 자동응답 기능은 카카오톡 앱 안드로이드/iOS 5.4.0 버전부터 지원됩니다.

#### 용어 설명

1. 수신 API
   * 카카오톡 이용자가 플러스친구에게 보낸 메시지를 전달 받은 후 응답을 할 수 있는 API 입니다.
   * http(s) restful api를 통하여 카카오 API 서버 -> 파트너 서버를 호출합니다.
2. user_key
   *  특정 카카오톡 이용자를 구분하기 위한 key 입니다. 카카오에서는 이용자의 개인정보를 외부에 제공하지 않으므로, 외부 파트너사에서 카카오톡 이용자를 구분하기 위해ㅔ서는 카카오로부터 API를 통한 user_key를  response로 받아야 합니다.
   * user_key는 특정 카카오톡 이용자에 대해 프로필별로 각기 다르게 발급됩니다. 따라서 user_key는 해당 프로필에 대해서만 유효합니다.
   * 카카오톡 이용자가 프로필을 차단했다가 다시 추가한 경우에는 user_key가 갱신되지 않으며, 이용자가 카카오톡 탈퇴 후 재가입한 경우 갱신됩니다.

#### API specifications

* 카카오 플러스 친구 API 서버에서 개발사 서버를 호출하는 API에 대한 명세서입니다.
* 개발사는 아래 스펙에 맞춰서 http(s) 서버를 구축하셔야 합니다.
* 응답 지연시간 : 최대 5초안에 응답이 오지 않는 경우 응답없음 메시지가 사용자에게 발송됩니다.
* QoS : 만약 응답 실패가 10회 이상 발생하게 되면 자동적으로 해당 모듈은 지정된 장애 메시지를 리턴하게 됩니다. 더불어 앱 등록시 지정된 관리자에게 카카오톡으로 장애 메시지가 발송됩니다.
* 플러스친구 관리자센터를 통해 설정한 개발사 서버 URL을 호출하게 됩니다.
* 개발사 서버가 방화벽으로 보호되고 있는 경우 server information문서를 참고해주세요.

1. Home Keyboard API

   * 이용자가 최초로 채팅방에 들어올 때 기본으로 키보드 영역에 표시될 자동응답 명령어의 목록을 호출하는 API입니다.
   * 채팅방을 지우고 다시 재 진입시에도 호출됩니다. 다만 카카오 서버에서도 1분 동안 캐시가 저장되기 때문에 유저가 채팅방을 지우고 들어오는 행동을 반복하더라도 개발사 서버를 1분에 한번씩 호출하게 됩니다.
   * 유저가 자동응답으로 메시지를 주고 받았을 경우는 마지막 메시지에 담겨있던 자동응답 명령어 목록이 표시됩니다. 다만 메시지에 저장된 자동응답 명령어는 10분간 유효합니다. 10분이 지난 다음에는 다시 Keyboard api를 호출하여 자동응답 목록을 초기화하게 됩니다.

   Specification

   * Method : GET

   * URL : http(s)://:yourserver_url/keyboard

   * Content - Type : application/json; charset=utf-8

   * 예제

     ```cure-XGET 'https://:your_server_url/keyboard'```

   * Response

     |   필드명    |    타입    |   필수여부   |                    설명                    |
     | :------: | :------: | :------: | :--------------------------------------: |
     | Keyboard | Keyboard | Required | 키보드 영역에 표현될 버튼에 대한 정보. 생략시 text 타입이 선택된다. |

   * 예제

     ```{
     {
       "type" : "buttons"
       "buttons":["선택1","선택2","선택3"]
     }
     ```

2.  메시지 수신 및 자동응답 API

   * 사용자가 선택한 명령어를 파트너사 서버로 전달하는 API입니다.

   * 자동응답 명령어에 대한 답변은 응답 메시지와 응답 메시지에 따른 키보드 영역의 답변 방식의 조합으로 이루어집니다. 답변 방식은 주관식(text)과 객관신(buttons) 중 선택할 수 있습니다.

   * 자동응답을 통한 친구에게 미디어 타입(사진/동영상/오디오)을 받고자 하는 경우 주관식 키보드(text)를 선택하세요. 메시지를 통해 **<'+'버튼을 눌러 미디어를 전송하세요>** 와 같이 안내하는 것이 필요 할 수 있습니다.

   * 유저가 보낸 미디어 타입의 카카오 서버에서의 보존기간은 아래와 같습니다.

     음성파일:20일

     이미지파일: 20일

     비디오 :20일

   * 미디어 파일의 보존기간은 서버의 상황에 의하여 변동 될 수 있습니다.

   Specification

   * Method : Post

   * URL : http(s)://:your_server_url/message

   * Content-Type : application/json; charset=utf-8

   * Parameters

     |   필드명    |   타입   | 필수여부     |               설명                |
     | :------: | :----: | -------- | :-----------------------------: |
     | user_key | String | Required |        메세지를 발송한 유저 식별 키         |
     |   type   | String | Required |           text, photo           |
     | content  | String | Required | 자동응답 명령어의 메시지 텍스트 혹은 미디어 파일 uri |

   * 예제

     ```
     curl-XPOST 'https://:your_server_url/message'-d;{
       "user_key":"encryptedUserKey",
       "type:"text",
       "content":"차량번호등록"
     }
     ```

     ```
     cure-XPOST'https://your_server_url/message'-d'{
       "user_key":"encryptedUserKey",
       "type":"photo",
       "content":"http://photo_url/number.jpg"
     }
     ```

   * 예제

     ```
     {
       "message":{
         "text":"귀하의 차량이 성공적으로 등록되었습니다.축하합니다!"
       }
     }
     ```

     ```
     {
       "message":{
         "text":"귀하의 차량이 성공적으로 등록되었습니다.축하합니다!",
         "photo":{
           "url":"https://photo.src",
           "width":640,
           "height":480
         }
       },
       "keyboard":{
         "type":"buttons",
         "buttons":[
           "처음으로",
           "다시 등록하기",
           "취소하기"
         ]
       }
     }
     ```

3. 친구 추가/차단 알림 API

   * 특정 카카오톡 이용자가 플러스친구를 친구로 추가하거나 차단하는 경우 해당 정보를 파트너사 서버로 전달하는 API입니다.

   Specification

   * Method : POST/DELETE

   * URL : http(s)://:your_sever_url/friend

   * Content-Type: application/json; charset=utf-8

   * Parameters

     |   필드명    |   타입   |   필수여부   |   설명   |
     | :------: | :----: | :------: | :----: |
     | user_key | String | Required | 유저 식별키 |

   * Response

     | http status code | code | message | comment |
     | :--------------: | :--: | :-----: | :-----: |
     |       200        |  0   | SUCCESS |  정상 응답  |

   * 예제

     친구 추가

     ```
     curl-XPOST 'https://:your_server_url/friend' -d'{
       "user_key";"HASHED_USER_KEY"
     }'
     ```

     친구 삭제

     ```
     curl -XDELETE 'https://:your_server_url/friend/:user_key'
     ```



4. 채팅방 나가기

   * 사용자가 채팅방 나가기를 해서 채팅방을 목록에서 삭제했을 경우 해당 정보를 파트너사 서버로 전달하는 API입니다.

   Specification

   * Method : delete

   * URL : http(s)://:your_server_url/chat_room/:user_key

   * Content-Type: application/json; charset=utf-8

   * Response

     | http status code | code | message | comment |
     | :--------------: | :--: | :-----: | :-----: |
     |       200        |  0   | SUCCESS |  정상 응답  |

   * 예제

     ```
     curl -XDELETE 'https://:your_server_url/chat_room/HASHED_USER_KEY'
     ```



#### Object

1. Keyboard

   * 응답 메시지에 따라 사용자의 키보드 영역에 표현될 메시지 입력 방식에 대한 정보입니다.

   * 별도로 설정하지 않는 경우 text  타입이 기본으로 설정됩니다.

     | 필드명     | 타입            | 필수여부     | 설명                                       |
     | ------- | ------------- | -------- | ---------------------------------------- |
     | type    | String        | Required | buttons:객관식 응답의 목록을 구성할 수 있음<br>text:주관식 응답을 입력받을 수 있음 |
     | buttons | Array[String] | Optional | 객관식 응답 내용의 목록                            |

   * 직접 입력

     ```
     {
       "type":"text"
     }
     ```

   * 직접 입력

     ```
     {
       "type":"buttons",
       "buttons":[
         "선택1",
         "선택2",
         "선택3"
       ]
     }
     ```

2. Message

   * 카카오톡 이용자가 명령어를 선택 혹은 입력했을 때 이용자에게 전송하는 응답 메시지입니다.

   * String, photo, MessageButton의 조합으로 이루어집니다.

     3가지 타입 중 1개 이상이 반드시 들어가야 하며, 최대 3가지 타입 모두 포함될 수 있습니다.

     |      필드명       |      타입       |   필수여부   |                    설명                    |
     | :------------: | :-----------: | :------: | :--------------------------------------: |
     |      text      |    String     | Optional |     사용자에게 발송될 메시지 텍스트<br>(최대 1000자)      |
     |     photo      |     photo     | Optional | 말풍선에 들어갈 이미지 정보. 1장 제한,<br>JPEG/PNG 포멧. 6.3에서 상세기술 |
     | message_button | MessageButton | Optional |      말풍선에 붙는 링크버튼 정보. 6.2.1에서 상세기술       |

     ```
     {
       "test":"안녕하세요.",
       "photo";{
         "url":"https://hello.photo.src",
         "width":640,
         "height":480
       },
       "message_button":{
         "label":"반갑습니다.",
         "url":"http://hello.world.com/example"
       }
     }
     ```

3. 메시지 MessageButton

   * 응답 메시지의 말풍선 하단에 보여지는 링크버튼 정보입니다.

     |  필드명  |   타입   |   필수여부   |       설명       |
     | :---: | :----: | :------: | :------------: |
     | label | String | Required |   링크버튼의 타이틀    |
     |  url  | String | Required | 링크버튼의 연결 링크 주소 |

     ```
     {
       "label":"쿠폰확인하기"<
       "url":"http://coupon.coupon.com/~~"
     }
     ```

4. Photo

   * 이미지 정보

     | 필드명    | 타입     | 필수여부     | 설명         |
     | ------ | ------ | -------- | ---------- |
     | url    | String | Required | 이미지 url    |
     | width  | Int    | Required | 이미지 width  |
     | height | Int    | Required | 이미지 height |

   * 이미지 권장 사이즈 : 720  x 630px

   * 지원 파일형식 및 권장 용량 : jpg, png / 500KB

     ```
     {
       "url":"https://photo.src",
       "width":640,
       "height":480
     }
     ```

     ​

---



#### 간단한 봇 만들어보기

프로젝트를  생성했으면 이제 **카카오톡 플러스 친구**에서 **API문서** 를 참고해서 간단한 봇을 만들어보자.

이건 다음 포스팅으로!