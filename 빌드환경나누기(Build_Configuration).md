## Build Configuration
다양한 환경에서 묶어서 관리하기가 편함    
예를 들면 iOS 13버전으로 앱을 보고 싶다거나,    
개발 할때의 서버와 릴리즈 할때의 서버를 다르게 한다거나    
개발할때에만 보이는 화면이 있어야한다거나    
이럴 경우에 Build Configuration을 여러개 두는것으로 해결이 가능함    
```swift
#if DEBUG 
#if RELEASE 
```
이런식으로 특정 환경에서만 코드가 읽히도록 하는게 가능해짐    

## 사용법
<img width="1053" alt="스크린샷 2024-04-03 오후 4 56 20" src="https://github.com/three523/Doc/assets/71269216/d3744c36-1649-41b5-8a28-356fde31c678">
이런식으로 새로운 Configuration을 만드는게 가능함      
Test라는 Configuration을 생성    
<img width="885" alt="스크린샷 2024-04-03 오후 5 41 36" src="https://github.com/three523/Doc/assets/71269216/df8f3aa0-42fa-4c0f-a757-5ccf5013e6b1">    

메뉴 -> Product -> Scheme -> ManagedScheme -> 하단의 + 버튼 클릭 -> 새로운 스키마 이름 작성 -> OK버튼 클릭

<img width="767" alt="스크린샷 2024-04-03 오후 5 39 01" src="https://github.com/three523/Doc/assets/71269216/04c55501-e548-45a6-94fe-b36d46458b1c">
새로운 Memorize-Test 가 생긴걸 볼 수 있음    
<img width="753" alt="스크린샷 2024-04-03 오후 5 42 28" src="https://github.com/three523/Doc/assets/71269216/7e016d87-dec1-490b-912d-be7b892d2090">
이후 메뉴 -> Product -> Scheme -> EditScheme에 들어가서 Build Configuration을 바꿔줘야함
<img width="937" alt="스크린샷 2024-04-03 오후 5 44 08" src="https://github.com/three523/Doc/assets/71269216/b734244f-365d-4a1a-9b02-75aff328961f">    
새로만든 Test로 하기    
만약 필요하다면 Test, Analyze, Archive도 변경하기   
만약 다른앱으로 만들어지게 하고 싶다면 Bundle Identifier를 다른 값으로 변경해주면 됨
<img width="1056" alt="스크린샷 2024-04-03 오후 5 48 31" src="https://github.com/three523/Doc/assets/71269216/a4b4cc17-bf65-4e1c-84f7-2f8ebf868113">

만약 앱 이름을 다르게 설정하고 싶으면 Bundle Display Name을 찾아서 변경하기
<img width="1045" alt="스크린샷 2024-04-03 오후 5 49 50" src="https://github.com/three523/Doc/assets/71269216/44f59db7-44c9-4150-8557-3763cc094890">

## 실행 모습
<img width="410" alt="스크린샷 2024-04-03 오후 5 51 16" src="https://github.com/three523/Doc/assets/71269216/b4f9f22c-7006-4133-9978-f193dd93d84e">
