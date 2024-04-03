## [Fastlane](https://docs.fastlane.tools/)
iOS 배포 자동화를 위해 필요한 툴
## 설치 방법
```bash
brew install fastlane
// 설치 완료
// fastlane을 사용할 디렉토리로 이동 (.xcodeproj 파일이 있는 디렉토리)
fastlane init
```
<img width="604" alt="스크린샷 2024-04-03 오후 3 21 05" src="https://github.com/three523/Doc/assets/71269216/26024957-d5e6-4f67-b9d9-f9781c063bd0">      </br>
1. 스크린샷 자동화    
2. TestFlight 배타 배포 자동화    
3. 앱 배포 자동화    
4. 직접 설정    
<img width="601" alt="스크린샷 2024-04-03 오후 3 25 23" src="https://github.com/three523/Doc/assets/71269216/500ae489-d6e8-4676-aaa0-ba7b8bea7d9c">    </br>
apple userID와 패스워드, 핸드폰 인증번호 작성

완료시
```bash
Gemfile
Gemfile.lock
fastlane/Appfile  // 프로젝트 설정, 애플 계정 파일
fastlane/Fastfile // fastlane 설정 파일
```
생성됨을 확인하기    
그리고 Appfile은 team_id, team_name, app_identifier 정도만 들어가는게 좋음    
public 레포를 올릴 숨길 방법 찾아보기    


## App Store인증
Appstore Connect에 앱 업로드 과정에 필요한 인증과정
- Cert, Sigh을 사용하는 방법
이미 애플 계정을 알고 있기 때문에 내 로컬 keychain에 넣어뒀으면 알아서 인증을 진행해주는 방식
로컬에 없으면 알아서 다운받아 진행해줌
- Match를 이용하는 방법
하나의 인증서를 github private 저장소에 넣어두고 팀원들이 해당 저장소에 접근해서 매번 인증서를 가져오는 방식

```bash
default_platform(:ios)

platform :ios do
  desc "Push TestFlight" // 제대로 성공시 커맨드창에 출력될 메세지
  lane :test do    // "fastlane test" 형식으로 커멘트 창에 실행시킬 명령어 명령어 입력시 밑의 내용을 바탕으로 코드를 실행
    increment_build_number( // 빌드번호를 자동으로 증가시키는 코드
      build_number: app_store_build_number + 1, // 앱스토어 기준으로 빌드번호를 증가시킴
      xcodeproj: "Memorize.xcodeproj"
    )
    build_app(scheme: "Memorize-debug")  // 스키마를 선택해 앱을 올림
    upload_to_testflight // testflight에 올린다는 의미
  end

  desc "Push a new release build to the App Store"
  lane :release do
    increment_build_number(
      build_number: app_store_build_number + 1,
      xcodeproj: "Memorize.xcodeproj"
    )
    build_app(scheme: "Memorize")
    upload_to_app_store( // appstore에 올린다는 의미
      submit_for_review: true, // 자동으로 리뷰 요청을 할것인지 여부
      automatic_release: false, // 자동으로 릴리즈 할것인지 여뷰
      skip_screenshots: false,  // 스크린샷을 올리는것을 스킵할 것인지 여뷰
      screenshots_path: "./screenshots", // 스크린샷 경로
      overwrite_screenshots: true, // 스크린샷이 있는 경우 다시 올릴것인지
      skip_metadata: false, // 메타데이터를 스킵할 것인지 
      metadata_path: "./metadata" // 메타데이터 경로
  end
end
```
이후 상황에 맞게 실행시키면 자동으로 올라가게 된다.
```bash
fastlane test
```
```bash
fastlane release
```
