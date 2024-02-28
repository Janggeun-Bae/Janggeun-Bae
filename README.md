<div align= "center">
    <img src="https://capsule-render.vercel.app/api?type=soft&color=303e82&height=120&text=Digital%20Twin%20Module&animation=&fontColor=f8f7f7&fontSize=70" />
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
    <img src="https://github.com/Janggeun-Bae/Janggeun-Bae/assets/128579000/212aa8bc-69f7-4685-ba1f-6c8cc85a2825" width="700" height="350">
    </p>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈의 모델들을 효율적으로 관리하기 위해 RESTful API의 URI Query parameter에 조건식을 정의하여 모델을 식별할 수 있도록 하였음. 조건식은 Resource Query Language(RQL)로 구성할 수 있으며, RQL은 SQL과 유사한 구조적 쿼리 언어로써, 논리연산자(Logical operators)와 관계연산자(Relational operators) 및 정렬을 위한 sort 연산자로 구성하여 설계하였음. </div> </br></br>
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
    
