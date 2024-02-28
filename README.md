<div align= "center">
    <img src="https://capsule-render.vercel.app/api?type=soft&color=59a2cf&height=120&text='Digital%20Twin%20Module'%20Development%20Log&animation=&fontColor=ffffff&fontSize=40" />
    </div>
    <div style="text-align: left;"> 
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;">  </h2>  
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈이란 현실 세계의 물리 객체를 가상 세계에 복제하여 가상 모델로써 관리하고, 물리 객체의 실시간 데이터를 연동하여 동작을 시뮬레이션하고 모니터링할 수 있도록 하는 기술임. </li></br></br></li>해당 프로젝트는 Golang을 통해 설계 및 구현된 디지털 트윈 모듈과, 데이터 연동을 위해 Python으로 구현된 현실 세계의 물리객체를 구현하고 해당 물리객체와 다중동기화메커니즘을 구현하고 연동하며, RESTful API를 통해 디지털 트윈 모듈의 모델들을 검증하고 관리하기 위해 HTML, CSS, JavasScript로 구현한 웹 애플리케이션으로 구성됨. </div> 
    </div>
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Digital Twin Architecture </h2> <br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/DigitalTwin/assets/128579000/59907bc6-514c-4166-9b4b-904981e2179c" width="850" height="350">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈은 현실 세계(Real World) 각각의 물리 객체(system)를 하나의 모델(model)로써 모델링하며, 물리 객체의 센서나 액츄에이터는 디지털 트윈 모듈 모델의 속성으로 정의하고 관리함. 디지털 트윈 모듈의 모델링된 모델과 현실 세계의 물리 객체는 Connectivity를 통해 실시간 연동함. 디지털 트윈 모듈은 모델링된 모델 및 자원들을 데이터베이스에 저장하고 관리하며, 해당 모델 및 자원에 접근하기 위해 웹 애플리케이션을 구성하였음. 애프리케이션과 디지털 트윈 모듈 간의 서비스 인터페이스를 설계하였으며, 애플리케이션에서 디지털 트윈 모듈로 모델에 대한 RESTful API request를 요청하고 디지털 트윈 모듈은 요청을 적절하게 처리하여 애플리케이션으로 RESTful API response하는 동작으로 구현함. 애플리케이션은 messages라는 통신을 통해 디지털 트윈 모듈을 거쳐 현실 세계의 물리 객체로 직접 접근할 수 있도록 하였음. </div> 
    <div style="text-align: left;">
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Model management </h2> <br>
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/ef90c0e5-c668-4d71-aecf-1a328ffc5503">
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈은 현실 세계의 물리 객체를 하나의 모델로써 모델링하여 관리하며, 모델은 JSON 객체의 형식으로 설계하였음. 모델의 데이터는 모델의 주기 동안 비교적 값의 갱신이 적은 static data와 수시로 갱신이 이루어지는 variable data로 나누어 설계하였으며, 추가로 애플리케이션에서 해당 모델의 실제 물리 객체와의 직접적인 통신을 위한 messages를 위한 데이터로 구성하였음. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/e4b58d67-1e19-4e6b-905b-080402310904" width="650" height="250">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 모델링된 디지털 트윈 모듈의 모델들을 관리하기 위해 애플리케이션과 디지털 트윈 모듈 간의 서비스 인터페이스를 설계하고, RESTful API를 통해 애플리케이션은 모델 관리에 대한 요청을 보내고 디지털 트윈 모듈은 요청을 처리하여 응답해주는 형식으로 설계함. 모델 관리를 위한 RESTful API는 URI(path)를 통해 관리할 모델의 자원을 식별하고 Method를 통해 자원을 처리하고자 하는 방식을 설정할 수 있음. Method는 POST를 통해 모델을 생성할 수 있도록하고, GET을 통해 모델의 정보를 획득하며, PUT과 PATCH를 통해 자원의 정보를 수정하며 DELETE를 통해 자원을 삭제할 수 있도록 설계함. PUT과 PATCH는 같은 수정의 요청이지만 PUT의 경우 RESTful API의 요청의 Request body 내용에 포함되는 수정 데이터를 덮어쓰는 형식으로 수정을 진행하며, PATCH의 경우 Request body 내용과 모델 자원의 내용을 비교하여 공통되는 자원만 수정한다는 차이점이 존재함.  </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/212aa8bc-69f7-4685-ba1f-6c8cc85a2825" width="700" height="350">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈의 모델을 관리하기 위한 RESTful API는 애플리케이션의 요청과 요청을 처리한 디지털 트윈 모듈이 응답하는 형식으로 동작함. 애플리케이션은 모델 관리 RESTful API 요청을 위해 URI, Method와 생성 및 수정의 경우 Request body를 설정하여 디지털 트윈 모듈에 요청하고, 요청을 받은 디지털 트우니 모듈은 내부적으로 동작하는 Router가 URI와 Method를 분석하여 올바른 Handler를 호출하고 Handler는 권한 확인(Resource Check), 자원 식별(Resource identify), 자원 처리(Resource Handle Logic)을 거쳐 Response body와 해당 Status code로 구성된 결과를 도출하여 애플리케이션에 응답하는 형식으로 동작함. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/766acd74-2948-4607-894c-22ee54159dcd" width="700" height="350">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈의 모델들을 효율적으로 관리하기 위해 RESTful API의 URI Query parameter에 조건식을 정의하여 모델을 식별할 수 있도록 하였음. 조건식은 Resource Query Language(RQL)로 구성할 수 있으며, RQL은 SQL과 유사한 구조적 쿼리 언어로써, 논리연산자(Logical operators)와 관계연산자(Relational operators) 및 정렬을 위한 sort 연산자로 구성하여 설계하였음. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/ee207094-97f8-495e-a8e1-5163464d932a" width="700" height="300">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈은 애플리케이션의 RESTful API 요청 URI의 Query parameter에 포함된 RQL 조건식을 처리하기 위해 가장 먼저 Query parameter의 RQL 조건식을 식별하고 논리연산자 안에 포함된 관계연산자를 처리하여 만족하는 모델을 식별하고 각 관계연산자에서 식별된 모델들을 논리연산자에 의거하여 최종 만족하는 모델을 식별하는 방식으로 동작함. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/aabc264b-6fcd-46fa-aa75-dce80a17b959" width="700" height="250">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> sort 연산자의 경우 첫번째 옵션(option1)을 통해 데이터베이스에 저장된 디지털 트윈 모듈 모델들의 해당 <property> 값들을 정렬하여 결과 배열에 저장하고, 이때 동일한 값을 갖는 모델들의 경우 두번째 옵션(option2)을 통해 정렬하는 과정을 반복함. </div> </br></br>
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Digital Twin Module Policy </h2> <br>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈 Policy란 디지털 트윈 모듈의 자원들에 대하여 사용자별로 각각 다른 접근 권한을 부여하여 디지털 트윈 모듈의 자원들을 효율적이고 안전하게 관리하고자 개발한 보안정책임. Policy는 Json 객체의 형식으로 정의하여 관리함. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/e0231648-7517-49a0-b0ee-53fe2b08adb9" width="450" height="550">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> Policy는 고유의 PolicyId를 속성으로 갖고, entries에는 사용자 별로 자원에 대한 접근 권한을 부여함. 사용자의 하위 속성으로 subjects에는 사용자에 대한 설명 및 권한이 만료되는 시간을 설정할 수 있고, resources에 각 자원에 대한 접근 권한을 설정할 수 있음. 모델에 대한 접근 권한은 entity:/, 보안정책 Policy에 대한 접근 권한은 policy:/, messages에 대한 권한은 message:/로 구분하여 권한을 부여하며 /로 구분하여 하위 속성에 관하여 권한을 부여하는 것도 가능함. 사용자의 권한은 자원에 대한 READ, WRITE 권한을 부여할 수 있으며, grant 속성에는 부여하는 권한, revoke에는 부여하지 않는 권한을 정의함. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/25662c87-88cc-4680-a84c-4c73960d15da" width="750" height="300">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 애플리케이션은 서비스 인터페이스를 통해 디지털 트윈 모듈에 접근하여 자원들을 관리하며, 모델을 관리하기 위한 model managament, 보안정책을 관리하기 위한 policy managament, 현실 객체로 직접적인 통신을 위한 messages에 대한 요청을 할 수 있으며, 해당 요청을 받은 디지털 트윈 모듈은 내부적으로 해당 요청에 맞는 Handlers를 router가 호출하여 처리하게 되는데, 이때 디지털 트윈 모듈 Policy에 따라 사용자가 요청한 권한이 있는지 확인하는 과정을 거쳐 권한이 확인 사용자의 요청인 경우 요청을 정상적으로 처리하도록 설계하였음. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/2beabe4b-cfbe-4aee-8ad9-fd3aa368e08b" width="650" height="250">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈 Policy는 애플리케이션에서 서비스 인터페이스를 통해 RESTful API 요청으로 관리할 수 있으며, URI를 통해 Policy 자원을 식별하고, Method를 통해 자원을 처리함. GET을 통해 Policy의 정보를 획득하며, PUT을 통해 Policy의 정보를 생성 및 수정하며, DELETE를 통해 삭제할 수 있도록 설계함.  </div> </br></br>
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Connectivity </h2> <br>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> Connecitivity는 디지털 트윈 모듈과 현실 세계의 물리 객체와의 통신 프로토콜을 정의하여, 모델링된 디지털 트윈 모듈의 모델과 물리 객체와의 데이터 통신을 통해 실시간 연동이 가능하게 함.</div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/7a65e053-1e8d-4e3b-85a3-584e7e8cd76b" width="400" height="400">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;">디지털 트윈 모듈과 물리 객체간의 Connectivity는 websocket, mqtt, amqp 총 3개의 통신 프로토콜을 구축하여, 물리 객체의 센서 및 액츄에이터에서 발생하는 데이터 및 디지털 트윈 모듈의 모델 상태가 변경되면서 발생하는 데이터 등 Connectivity의 다중 동기화 통신 메커니즘을 통해 서로 실시간으로 연동할 수 있도록 설계하였음. </div> </br></br>
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Messages </h2> <br>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> messages는 애플리케이션 상에서 현실 세계의 물리 객체를 직접적으로 제어하기 위한 통신으로써 디지털 트윈 모듈이 통신의 브로커 역할을 하며, 통신 방식에 따라 behaviors와 events로 구분하여 설계하였음. </div> </br></br>
    <p align="center">
    <img src="https://github.com/Janggeun-Bae/DigitalTwin/assets/128579000/59907bc6-514c-4166-9b4b-904981e2179c" width="850" height="350">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> messages 통신 중 behaviors의 경우 애플리케이션에서 서비스 인터페이스를 통해 messages를 요청하고 디지털 트윈 모듈은 해당 messages를 물리 객체에 전달함. messages를 요청받은 물리 객체는 messages에 대한 유효성을 검사한 뒤, behaviors의 요청을 수행한 뒤 결괏값을 도출하여 디지털 트윈 모듈에 전송하고, 최종적으로 디지털 트윈 모듈은 애플리케이션에 messages에 대한 결괏값을 응답해주는 형식으로 동작하는 단발성 통신임. </br> events의 경우 마찬가지로 애플리케이션의 요청을 디지털 트윈 모듈이 물리 객체에 전달하고 유효성을 검사한 물리 객체는 해당 events에 대한 이벤트가 발생할 때 마다 애플리케이션에게 응답해주는 형식으로 동작하는 다발성 통신임. </div> 
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> 🛠️ Tech Stacks </h2> <br> 
    <div style="margin: ; text-align: left;" "text-align: left;"> 
          <img src="https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=Go&logoColor=white">
          <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white"></br>
          <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=HTML5&logoColor=white">
          <img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white">
          <img src="https://img.shields.io/badge/Javascript-F7DF1E?style=for-the-badge&logo=Javascript&logoColor=white">
          <img src="https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jQuery&logoColor=white"></br>
          <img src="https://img.shields.io/badge/redis-DC382D?style=for-the-badge&logo=Redis&logoColor=white">
          <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=MongoDB&logoColor=white"></br>
          <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=Linux&logoColor=white"></br>
          </div>
    </div>
    
