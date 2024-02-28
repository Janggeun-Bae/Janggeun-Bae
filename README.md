<div align= "center">
    <img src="https://capsule-render.vercel.app/api?type=soft&color=303e82&height=120&text=Digital%20Twin%20Module&animation=&fontColor=f8f7f7&fontSize=70" />
    </div>
    <div style="text-align: left;"> 
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;">  </h2>  
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈이란 현실 세계의 물리 객체를 가상 세계에 복제하여 가상 모델로써 관리하고, 물리 객체의 실시간 데이터를 연동하여 동작을 시뮬레이션하고 모니터링할 수 있도록 하는 기술임. </li></br></br></li>해당 프로젝트는 Golang을 통해 설계 및 구현된 디지털 트윈 모듈과, 데이터 연동을 위해 Python으로 구현된 현실 세계의 물리객체를 구현하고 해당 물리객체와 다중동기화메커니즘을 구현하고 연동하며, RESTful API를 통해 디지털 트윈 모듈의 모델들을 검증하고 관리하기 위해 HTML, CSS, JavasScript로 구현한 웹 애플리케이션으로 구성됨. </div> 
    </div>
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Digital Twin Architecture </h2> <br> 
    <img src="https://github.com/Janggeun-Bae/DigitalTwin/assets/128579000/59907bc6-514c-4166-9b4b-904981e2179c">
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈은 현실 세계(Real World) 각각의 물리 객체(system)를 하나의 모델(model)로써 모델링하며, 물리 객체의 센서나 액츄에이터는 디지털 트윈 모듈 모델의 속성으로 정의하고 관리함. 디지털 트윈 모듈의 모델링된 모델과 현실 세계의 물리 객체는 Connectivity를 통해 실시간 연동함. 디지털 트윈 모듈은 모델링된 모델 및 자원들을 데이터베이스에 저장하고 관리하며, 해당 모델 및 자원에 접근하기 위해 웹 애플리케이션을 구성하였음. 애프리케이션과 디지털 트윈 모듈 간의 서비스 인터페이스를 설계하였으며, 애플리케이션에서 디지털 트윈 모듈로 모델에 대한 RESTful API request를 요청하고 디지털 트윈 모듈은 요청을 적절하게 처리하여 애플리케이션으로 RESTful API response하는 동작으로 구현함. 애플리케이션은 messages라는 통신을 통해 디지털 트윈 모듈을 거쳐 현실 세계의 물리 객체로 직접 접근할 수 있도록 하였음. </div> 
    <div style="text-align: left;">
    <h2 style="border-bottom: 1px solid #d8dee4; color: #282d33;"> Model management </h2> <br>
    <div style="font-weight: 700; font-size: 15px; text-align: left; color: #282d33;"> 디지털 트윈 모듈은 현실 세계의 물리 객체를 하나의 모델로써 모델링하여 관리함. </div> 
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
    
