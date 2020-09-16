# 📖 NAS 오퍼월 적용 가이드
NAS 오퍼월은 `Android`, `iOS`, `Unity` 를 지원합니다.

플렛폼 별 사이트로 이동하여 SDK 및 예제 소스를 다운받을 수 있습니다.

***상용 버전 SDK***
- [Android SDK](https://github.com/mafin-global/nas-offerwall-android)
- [iOS SDK](https://github.com/mafin-global/nas-offerwall-ios)
- [Unity SDK](https://github.com/mafin-global/nas-offerwall-unity)

***베타 버전 SDK*** 
- [iOS 14용 SDK](https://github.com/mafin-global/nas-offerwall-ios/tree/feature/ios14) ***(iOS 14 테스트를 위한 베타 버전 SDK)***

## 목차
- [📝⠀업데이트](#-업데이트)
- [👤️⠀개발자 등록](#%EF%B8%8F-개발자-등록)
- [🎲⠀매체 등록](#-매체-등록)
    - [적립금 관리 서버](#적립금-관리-서버)
    - [리워드 금액 단위](#리워드-금액-단위)
    - [리워드 금액 비율](#리워드-금액-비율)
    - [콜백 URL 등록](#콜백-url-등록-개발자-서버에서-적립금-관리-시-사용) _(개발자 서버에서 적립금 관리 시 사용)_
    - [아이템 등록](#아이템-등록-nas-서버에서-적립금-관리-시-사용) _(NAS 서버에서 적립금 관리 시 사용)_
- [🚀⠀SDK 연동](#-sdk-연동)

## 📝 업데이트

### `iOS 업데이트`
- [`2020년 9월 16일`](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Update.md#2020년-9월-16일)
    - iOS 14 지원을 위한 SDK 배포
- [`2020년 3월 31일`](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Update.md#2020년-3월-31일)
    - 통신 관련 버그 수정
- [`2020년 1월 30일`](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Update.md#2020년-1월-30일---내장-ui) - _내장 UI_
    - foreground 시 새로고침되지 않는 버그 수정
- [`2020년 1월 28일`](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Update.md#2020년-1월-28일---내장-ui) - _내장 UI_
    - 환경에 따라 오퍼월이 보이지 않는 현상 수정
- [전체 업데이트 목록 보기](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Update.md)

### `Android 업데이트`
- [`2020년 6월 26일`](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Update.md#2020년-6월-26일)
    - 테스트 모드와 관련된 버그 수정
- [`2019년 10월 14일`](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Update.md#2019년-10월-14일)
    - Android Q(10) 대응 버그 수정
- [`2019년 9월 19일`](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Update.md#2019년-9월-19일)
    - Android Q(10) 대응
    - 초기화 완료 이벤트 추가 (NASWall.setOnInitListener)
- [`전체 업데이트 목록 보기`](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Update.md)

## 👤️ 개발자 등록
NAS 오퍼월 연동을 위해서는 먼저 개발자 등록을 해야합니다.

[NAS 홈페이지](http://www.appang.kr/nas) 에 접속하여 `회원가입` 버튼을 눌러 가입합니다.

## 🎲 매체 등록
NAS 오퍼월 연동을 위해서는 연동할 매체 등록 해야합니다.

[NAS 홈페이지](http://www.appang.kr/nas) 에 로그인 후 `신규매체 등록` 버튼을 눌러 매체를 등록합니다.

매체를 등록하면 32자리 `앱 KEY`가 발급되며, SDK 초기화 시 필요한 값입니다.
`매체 관리` 메뉴에서 등록한 매체의 우측 `more` 버튼을 눌러 `앱 KEY 복사` 를 눌러 `앱 KEY`를 복사할 수 있습니다.

### `적립금 관리 서버`
사용자 적립금을 NAS 서버에서 관리할지 아니면 개발자 서버에서 관리할지를 선택합니다.

- `NAS 서버 사용` : 개발자가 서버를 가지고있지 않고, NAS 서버에서 사용자의 적립금을 관리할 경우 선택합니다. SDK를 통해 적립금의 확인 및 사용이 가능합니다.
- `개발자 서버 사용` : 개발자가 서버에서 사용자 적립금을 직접 관리할 경우 선택합니다. 사용자가 적립금 충전 시 개발자 서버의 콜백 URL로 통보해줍니다.

### `리워드 금액 단위`
리워드 금액 단위는 오퍼월 에서 사용자에게 보이는 리워드 금액의 단위입니다.

만약 광고 참여 완료 시 사용자에게 100골드를 준다면 `골드`를 입력하고, 100원을 준다면 `원`을 입력합니다

### `리워드 금액 비율`
리워드 금액 비율은 광고 참여 완료 시 개발자가 얻게되는 수익 중에서 사용자에게 리워드로 줄 금액의 비율(%)입니다.

만약 사용자가 광고참여 시 개발자가 받게되는 수익이 200원이고, 사용자에게 100원을 주고 싶으면 리워드 금액 비율을 `50`으로 입력합니다.

각 광고마다 개발자에게 지급되는 금액이 다르기 때문에, 사용자에게 지급하는 실제 금액은 `콜백 URL` 호출 시 함께 전송됩니다.

### `콜백 URL 등록` _(개발자 서버에서 적립금 관리 시 사용)_
적립금 관리 서버를 `개발자 서버 사용` 으로 선택한 경우 설정할 수 있습니다.

`콜백 URL`은 NAS 서버에서 개발자 서버로 호출하는 URL로 사용자가 광고 `참여 완료` 시 호출됩니다. `콜백 URL`에서 사용자에게 적립금등의 혜택을 지급하도록 구성하시기 바랍니다.
콜백 URL은 `앱 설정` 화면의 `보상형 기본` 탭에서 설정할 수 있습니다.

`콜백 URL`에는 아래의 값들이 제공됩니다.

이 값들은 개발자 서버로 호출 시 실제 값으로 변환됩니다. `콜백 URL` 입력 시 반드시 `대괄호`까지 입력하시기 바랍니다.

- `[SEQ_ID]` : 적립 고유 ID
- `[USER_DATA]` : 회원 정의 데이터
- `[PRICE]` : 광고 단가 (매체 수익금)
- `[REWARD]` : 리워드 금액 (오퍼월에서 참여한 경우에만 값이 있음)
- `[AD_ID]` : 광고 ID
- `[AD_KEY]` : 광고 KEY
- `[AD_NAME]` : 광고명
- `[AD_TYPE]` : 광고구분 (CPI, CPE, CPA, CPC, FACEBOOK)
- `[USER_ADID]` : 사용자 기기 36자리 광고 ID (Android : ADID, iOS : IDFA)
- `[USER_IP]` : 사용자 IP 주소

```
http://server.kr/callback.asp?sid=[SEQ_ID]&ud=[USER_DATA]&p=[PRICE]&r=[REWARD]&ai=[AD_ID]&ak=[AD_KEY]&n=[AD_NAME]&t=[AD_TYPE]&adid=[USER_ADID]&ip=[USER_IP]`
```

개발자 서버의 웹페이지가 `HTTP 200` 상태값을 리턴하면 `콜백 URL`을 더 이상 호출하지 않고 중지됩니다.
만약 `HTTP 200` 이외의 상태값이 리턴되면 `최대 5번`까지 재시도하여 호출하고, `5번` 오류가 발생하면 더 이상 호출하지 않습니다.

오류 횟수에 따른 `재호출` 시간 간격은 아래와 같습니다.

- `1회 오류 시` : 오류 시점부터 5분 후 재호출
- `2회 오류 시` : 오류 시점부터 10분 후 재호출
- `3회 오류 시` : 오류 시점부터 25분 후 재호출
- `4회 오류 시` : 오류 시점부터 30분 후 재호출
- `5회 오류 시` : 오류 시점부터 8시간 후 재호출
- `6회 오류 시` : 호출 중단

> ***적립금 중복 지급 방지를 위한 처리***
> - 콜백 중복 호출 시, 적립금 중복 지급을 방지하기 위해, `[SEQ_ID]`를 기준으로 중복지급을 막아주시기 바랍니다.
>
> - 동일 사용자에게 적립금 중복 지급을 방지하기 위해, 개발사의 `회원 ID` 와 `[AD_ID]` 값을 기준으로 중복지급을 막아주시기 바랍니다.

### `아이템 등록` _(NAS 서버에서 적립금 관리 시 사용)_
아이템은 적립금 관리 서버를 `NAS 서버 사용` 으로 선택한 경우, 사용자가 적립금을 사용(차감)할 때 필요합니다.

아이템을 등록하고 SDK의 `아이템 구매 함수`를 이용하면, 사용자의 적립금을 사용(차감)할 수 있습니다.

`매체 관리` 메뉴에서 등록한 매체의 우측 `more` 버튼을 누르고, `아이템 관리` 를 눌러 아이템 관리 창을 띄웁니다.

아이템 관리 창에서 `아이템 추가` 버튼을 눌러 아이템을 등록합니다.

- `아이템 이름` : 아이템의 이름을 입력합니다.
- `가격` : 아이템의 가격을 입력합니다. 사용자가 아이템 구매 시 입력한 가격 만큼 적립금이 차감됩니다.

아이템 등록 후 아이템 목록에서 `아이템 ID` 를 확인할 수 있습니다.
`아이템 ID`는 SDK의 `아이템 구매 함수`를 호출할 때 필요한 값입니다.
등록된 아이템 정보는 `수정` 버튼을 눌러 언제든지 변경할 수 있습니다.

## 🚀 SDK 연동

플렛폼 별 사이트로 이동하여 가이드를 참고해주세요. 

- Android
    - [내장 UI 연동 가이드](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Guide.Embed.md)
    - [개발자 정의 UI 연동 가이드](https://github.com/mafin-global/nas-offerwall-android/blob/master/docs/Guide.Custom.md)
    
- iOS
    - [내장 UI 연동 가이드](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Guide.Embed.md)
    - [개발자 정의 UI 연동 가이드](https://github.com/mafin-global/nas-offerwall-ios/blob/master/docs/Guide.Custom.md)
    
- [Unity 연동 가이드](https://github.com/mafin-global/nas-offerwall-unity)
