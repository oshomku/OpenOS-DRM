# OpenOS DRM Interface

## Overview
개방형 OS (Linux OS)에서 동작하는 문서 저작 도구(Office 류의 Application)에 문서 권한 관리 솔루션(문서 DRM)을 적용 하기 위한 Interface이다.  
문서 저작 도구는 이 Interface를 이용, 문서 권한 관리 솔루션과 통신하여 문서 저작 도구에 문서 권한 관리 솔루션을 적용 한다.
* 문서 저작 도구는 여러 종류/회사의 문서 권한 관리 솔루션과 통신을 위해 매번 새로이 코드를 수정 할 필요 없이 단일 규격 Interface 한 번만 적용하면 되기 때문에 문서 권한 관리 솔루션 적용이 보다 쉬워 지고, 빨라진다.
* 여러 종류/회사의 문서 권한 관리 솔루션은 단일 규격의 Interface에 맞춰 문서 권한 관리 기능을 수행 하면 되기 때문에, 사용자 및 엔지니어는 동일 규격의 Application을 구축할 수 있게 되며, 동일 규격의 문서 권한 관리 시스템을 지원 할 수 있게 된다.
* Interface를 이용하기 때문에 기존 문서 권한 관리 솔루션에서의 단점이 충돌 및 Hooking 등으로 인해 낭비되는 시스템 리소스를 최소화 할 수 있다.

## OpenOS DRM Interface 구성
OpenOS DRM Interface는 크게 문서 저작 도구 Application의 UI 관련 부분을 위한 'Document Interface'와, 파일의 입/출력 및 암호화된 파일의 정보 확인 등을 위한 'System Interface'로 나뉜다. 

* Document Interface
   * 사용자가 문서 저작 도구를 이용하여 문서를 사용 할 경우 필요한 이벤트 호출 (문서 저작 도구 > 문서 권한 관리 솔루션)
      * 파일 열기 전/후
      * 파일 저장 전/후
      * 문서에 다른 Content(다른 문서, 이미지 등) 삽입 전
      * 문서 미리보기 (인쇄 기능전 미리보기 화면 등)
      * 자동 저장 파일 저장 전
      * 임시 파일 생성 후
      * 임시 파일 삭제 후
      * 프로그램 실행 (초기화)
      * 매크로 실행 전
      * 메뉴/단축키 실행 전
   * 메뉴/단축키 제어
   * 암호화된 문서의 사용 가능 여부
* System Interface
   * 문서의 암호화 API
   * FILE 계열 C Standard API와 1:1 매칭 되는 FILE 관련 API Set
      * Open
      * Read
      * Write
      * close
      * Setting File Pointer
      * Getting File Size
   * DRM 문서의 정보
      * 암호화 된 문서의 권한 정보 확인
      * 암호화 된 문서의 소유 고객사 확인
      * 암호화 문서의 종류
      * 로그온 상태 정보
   * 사용 내역 발송
   * 에러 체크
* 상세 인터페이스는 [개방형 OS 문서 저작 도구 DRM Interface.doc](./DOC/개발형 OS 문서 저작 도구 DRM Interface.docx) 참고

## 지원 환경
   * 개방형 OS 및 Linux 사에서 동작하는 문서 저작 도구 중, C/C++로 Interface 연동이 가능한 제품
   
## 현재 지원 환경
   * [TMAX OS 3](https://tmaxanc.com/#!/product-introduce/TmaxOS) / [ToOffice 3](https://tmaxanc.com/#!/product-introduce/ToOffice)
   
